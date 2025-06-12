## SQL

### 참고 : GROUP BY 절
1. 집계 함수(`SUM`, `COUNT` 등)를 사용하지 않는다.
❌ → `GROUP BY SUM(PRICE)`
2. SELECT 절의 컬럼은 모두 `GROUP BY`에 명시해야 한다. (단, 집계 함수가 적용된 항목은 GROUP BY에 없어도 된다.)
❌ → `SELECT U.USER_ID, U.NICKNAME, SUM(B.PRICE)`
      `GROUP BY U.USER_ID`

### 참고 : SELECT 절의 별칭 사용
1. GROUP BY : ❌
→ 대부분의 DBMS에서는 오류 **(MySQL만 허용)**
2. HAVING: ⭕
3. ORDER BY: ⭕
→ 별칭 사용 가능하고 컬럼 순번(숫자) 표현도 가능

### 참고 : DBMS별 날짜 필터 (10월 필터 방법)
1. MySQL → MONTH(START_DATE) = 10
2. Oracle → TO_CHAR(START_DATE, 'MM') = '10'
3. PostgreSQL → EXTRACT(MONTH FROM START_DATE) = 10

---

### 문제 2: 가격대 별 상품 개수 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/131530

- PRODUCT 테이블에서 만원 단위의 가격대 별로 상품 개수를 출력하는 SQL 문을 작성
- 이때 컬럼명은 각각 컬럼명은 PRICE_GROUP, PRODUCTS로 지정
- 가격대 정보는 각 구간의 최소금액(10,000원 이상 ~ 20,000 미만인 구간인 경우 10,000)으로 표시
- 결과는 가격대를 기준으로 오름차순 정렬

### 첫 번째 시도 (실패)
```sql
SELECT (PRICE//10000)*10000 PRICE_GROUP, COUNT(PRICE) PRODUCTS
FROM PRODUCT
GROUP BY PRICE_GROUP
ORDER BY PRICE_GROUP
```

> 문제점
1. `//` 는 Python에서 정수 나눗셈 연산자 (MySQL에는 없으므로 헷갈리지 말기!!)
→ 방법 1) `DIV` 연산자 사용 (MySQL 전용)
	- 정수 나눗셈
→ 방법 2) `FLOOR()` 함수 사용 (MySQL 포함 대부분 DB에서 가능)
	- 정수로 내림 후 계산
2. COUNT(*) vs COUNT(PRICE)
	- COUNT(*) : **행의 개수 전체**를 센다. (NULL 여부 상관없음)
	- COUNT(PRICE) : `PRICE` 값이 **NULL이 아닌 행의 개수**만 센다.
- `PRICE`가 NOT NULL이면 COUNT(*)와 COUNT(PRICE)의 결과는 동일
→ 일반적으로는 `COUNT(*)`가 더 안전하고 직관적

### 최종 코드1 (DIV 연산자 사용)
```sql
SELECT (PRICE DIV 10000)*10000 PRICE_GROUP,
       COUNT(*) PRODUCTS
FROM PRODUCT
GROUP BY PRICE_GROUP
ORDER BY PRICE_GROUP
```

### 최종 코드2 (FLOOR() 함수 사용)
```sql
SELECT FLOOR(PRICE / 10000)*10000 PRICE_GROUP,
       COUNT(*) PRODUCTS
FROM PRODUCT
GROUP BY PRICE_GROUP
ORDER BY PRICE_GROUP
```

---

## Python

https://velog.io/@ckduswjd/DAY24-파이썬-개인-과제-필수

### 참고
1.
- return을 여러 번 써도 된다. 단, 실행 흐름은 return을 만나면 즉시 함수 종료
- 조건에 따라 바로 return하면 가독성, 명확성 모두 좋아짐 (불필요하게 변수 할당하지 말자)

2. Python은 줄마다 정확히 동일한 들여쓰기 폭을 요구 (tab + space 혼용 불가)

3. 딕셔너리에서
- `for product in sales_data:` → **키(상품 이름)**만 꺼냄
- `sales_data[product]` → 해당 키의 **값(수량)**을 가져옴

4. `df.isnull().sum()`
- 결측치 개수 확인 방법 (True가 1, False가 0으로 취급되므로 isnull, sum 함수 연계)

5. 집합(set)은 순서가 보장되지 않음

