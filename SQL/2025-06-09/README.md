## 문제 1: 오랜 기간 보호한 동물(1)

https://school.programmers.co.kr/learn/courses/30/lessons/59044

- 아직 입양을 못 간 동물 중, 가장 오래 보호소에 있었던 동물 3마리의 이름과 보호 시작일을 조회하는 SQL문을 작성
- 이때 결과는 보호 시작일 순으로 조회

### 코드:
```sql
SELECT I.NAME, I.DATETIME
FROM ANIMAL_INS I LEFT JOIN ANIMAL_OUTS O ON I.ANIMAL_ID = O.ANIMAL_ID
WHERE O.ANIMAL_ID IS NULL
ORDER BY I.DATETIME
LIMIT 3
```

## 문제 2: 카테고리 별 도서 판매량 집계하기

https://school.programmers.co.kr/learn/courses/30/lessons/144855

- 2022년 1월의 카테고리 별 도서 판매량을 합산하고, 카테고리(CATEGORY), 총 판매량(TOTAL_SALES) 리스트를 출력하는 SQL문을 작성
- 결과는 카테고리명을 기준으로 오름차순 정렬

### 코드1:
```sql
SELECT B.CATEGORY, SUM(S.SALES) TOTAL_SALES
FROM BOOK B JOIN BOOK_SALES S ON B.BOOK_ID = S.BOOK_ID
WHERE S.SALES_DATE LIKE '2022-01%'
GROUP BY B.CATEGORY
ORDER BY B.CATEGORY
```

> LIKE '2022-01%' 조건은 문자열 비교 방식이라 날짜 타입 처리에 비효율적일 수 있음

### 코드2:
```sql
SELECT B.CATEGORY, SUM(S.SALES) TOTAL_SALES
FROM BOOK B JOIN BOOK_SALES S ON B.BOOK_ID = S.BOOK_ID
WHERE S.SALES_DATE BETWEEN '2022-01-01' AND '2022-01-31'
GROUP BY B.CATEGORY
ORDER BY B.CATEGORY
```

## 문제 3: 상품 별 오프라인 매출 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/131533

- PRODUCT 테이블과 OFFLINE_SALE 테이블에서 상품코드 별 매출액(판매가 * 판매량) 합계를 출력하는 SQL문을 작성
- 결과는 매출액을 기준으로 내림차순 정렬, 매출액이 같다면 상품코드를 기준으로 오름차순 정렬

### 코드:
```sql
SELECT P.PRODUCT_CODE, SUM(P.PRICE*O.SALES_AMOUNT) SALES
FROM PRODUCT P JOIN OFFLINE_SALE O ON P.PRODUCT_ID = O.PRODUCT_ID
GROUP BY P.PRODUCT_CODE
ORDER BY 2 DESC, 1
```

## 문제 4: 있었는데요 없었습니다

https://school.programmers.co.kr/learn/courses/30/lessons/59043

- 보호 시작일보다 입양일이 더 빠른 동물의 아이디와 이름을 조회하는 SQL문을 작성
- 이때 결과는 보호 시작일이 빠른 순으로 조회

### 코드:
```sql
SELECT I.ANIMAL_ID, I.NAME
FROM ANIMAL_INS I JOIN ANIMAL_OUTS O ON I.ANIMAL_ID = O.ANIMAL_ID
WHERE I.DATETIME > O.DATETIME
ORDER BY I.DATETIME
```
