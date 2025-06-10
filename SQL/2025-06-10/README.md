## 문제 1: 오랜 기간 보호한 동물(2)

https://school.programmers.co.kr/learn/courses/30/lessons/59411

- 입양을 간 동물 중, 보호 기간이 가장 길었던 동물 두 마리의 아이디와 이름을 조회하는 SQL문을 작성
- 이때 결과는 보호 기간이 긴 순으로 조회

### 코드:
```sql
SELECT O.ANIMAL_ID, O.NAME
FROM ANIMAL_INS I
JOIN ANIMAL_OUTS O ON I.ANIMAL_ID = O.ANIMAL_ID
ORDER BY DATEDIFF(O.DATETIME, I.DATETIME) DESC
LIMIT 2
```

## 문제 2: 보호소에서 중성화한 동물

https://school.programmers.co.kr/learn/courses/30/lessons/59045

- 보호소에 들어올 당시에는 중성화되지 않았지만, 보호소를 나갈 당시에는 중성화된 동물의 아이디와 생물 종, 이름을 조회하는 아이디 순으로 조회하는 SQL 문을 작성
- 중성화를 거치지 않은 동물은 Intact, 중성화를 거친 동물은 Spayed 또는 Neutered라고 표시

### 코드:
```sql
SELECT I.ANIMAL_ID, I.ANIMAL_TYPE, I.NAME
FROM ANIMAL_INS I JOIN ANIMAL_OUTS O ON I.ANIMAL_ID = O.ANIMAL_ID
WHERE I.SEX_UPON_INTAKE LIKE 'intact%' AND (O.SEX_UPON_OUTCOME LIKE 'Spayed%' OR O.SEX_UPON_OUTCOME LIKE 'Neutered%')
ORDER BY 1
```

## 문제 3: 조건에 맞는 도서와 저자 리스트 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/144854

- '경제' 카테고리에 속하는 도서들의 도서 ID(BOOK_ID), 저자명(AUTHOR_NAME), 출판일(PUBLISHED_DATE) 리스트를 출력하는 SQL문을 작성
- 결과는 출판일을 기준으로 오름차순 정렬
- PUBLISHED_DATE의 데이트 포맷이 예시와 동일해야 정답처리

### 코드:
```sql
SELECT B.BOOK_ID,
       A.AUTHOR_NAME,
       DATE_FORMAT(B.PUBLISHED_DATE, '%Y-%m-%d') PUBLISHED_DATE
FROM BOOK B JOIN AUTHOR A ON B.AUTHOR_ID = A.AUTHOR_ID
WHERE B.CATEGORY = '경제'
ORDER BY B.PUBLISHED_DATE
```

## 문제 4: 조건별로 분류하여 주문상태 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131113

- FOOD_ORDER 테이블에서 2022년 5월 1일을 기준으로 주문 ID, 제품 ID, 출고일자, 출고여부를 조회하는 SQL문을 작성
- 출고여부는 2022년 5월 1일까지 출고완료로 이 후 날짜는 출고 대기로 미정이면 출고미정으로 출력
- 결과는 주문 ID를 기준으로 오름차순 정렬

### 코드:
```sql
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
