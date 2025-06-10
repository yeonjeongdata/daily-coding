## SQL

### 날짜 차이 계산
> DATEDIFF(날짜2, 날짜1)
> - `날짜2 - 날짜1`의 **일 수 차이**를 반환

- 참고) DATEDIFF()는 MySQL, SQL Server 등에서 지원되지만, DBMS에 따라 사용법이나 반환 단위가 다를 수 있음

### 대소문자 민감성 문제
- `LIKE` 비교 시 대소문자 민감성 문제를 방지하고자 대소문자 명확히 처리하는 방식 추천
`WHERE I.SEX_UPON_INTAKE LIKE 'intact%' → `WHERE LOWER(I.SEX_UPON_INTAKE) LIKE 'intact%'`

### 문제4 : 조건별로 분류하여 주문상태 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131113

- FOOD_ORDER 테이블에서 2022년 5월 1일을 기준으로 주문 ID, 제품 ID, 출고일자, 출고여부를 조회하는 SQL문을 작성
- 출고여부는 2022년 5월 1일까지 출고완료로 이 후 날짜는 출고 대기로 미정이면 출고미정으로 출력
- 결과는 주문 ID를 기준으로 오름차순 정렬

#### 첫번째 시도 (성공. 코드 개선 필요)
```python
SELECT ORDER_ID,
       PRODUCT_ID,
       DATE_FORMAT(OUT_DATE, '%Y-%m-%d') OUT_DATE,
       CASE WHEN OUT_DATE <= '2022-05-01' THEN '출고완료'
            WHEN OUT_DATE > '2022-05-01' THEN '출고대기'
            ELSE '출고미정' END 출고여부
FROM FOOD_ORDER
ORDER BY ORDER_ID
```

> 개선점 : 조건 순서 중요
- CASE문에서 NULL인 경우를 마지막에 두면 앞의 조건문들에서 비교가 불가능하므로 출고미정 조건이 먼저 나와야 명확함

> 참고 : `DATE_FORMAT()` 함수는 MySQL에서만 사용 (Oracle일 경우 `TO_CHAR()`를 사용)

#### 개선된 코드
```python
SELECT ORDER_ID,
       PRODUCT_ID,
       DATE_FORMAT(OUT_DATE, '%Y-%m-%d') AS OUT_DATE,
       CASE WHEN OUT_DATE IS NULL THEN '출고미정'
            WHEN OUT_DATE <= '2022-05-01' THEN '출고완료'
            ELSE '출고대기'
       END AS 출고여부
FROM FOOD_ORDER
ORDER BY ORDER_ID
```

---

## Python

https://velog.io/@ckduswjd/DAY22-파이썬-기초-2
