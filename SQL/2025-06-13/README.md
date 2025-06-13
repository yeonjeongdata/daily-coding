## 문제 1: 모든 레코드 조회하기

https://school.programmers.co.kr/learn/courses/30/lessons/59034

- 동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성

### 코드:
```sql
SELECT *
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```

## 문제 2: 즐겨찾기가 가장 많은 식당 정보 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131123

- REST_INFO 테이블에서 음식종류별로 즐겨찾기수가 가장 많은 식당의 음식 종류, ID, 식당 이름, 즐겨찾기수를 조회하는 SQL문을 작성
- 이때 결과는 음식 종류를 기준으로 내림차순 정렬

### 코드1 (JOIN 방식)
```sql
SELECT R.FOOD_TYPE, R.REST_ID, R.REST_NAME, R.FAVORITES
FROM REST_INFO R
JOIN (
    SELECT FOOD_TYPE, MAX(FAVORITES) AS MAX_FAV
    FROM REST_INFO
    GROUP BY FOOD_TYPE
) M ON R.FOOD_TYPE = M.FOOD_TYPE AND R.FAVORITES = M.MAX_FAV
ORDER BY R.FOOD_TYPE DESC
```

### 코드2 (DENSE_RANK())
```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM (
    SELECT REST_ID, FOOD_TYPE, REST_NAME, FAVORITES,
           DENSE_RANK() OVER (PARTITION BY FOOD_TYPE ORDER BY FAVORITES DESC) AS RANKING
    FROM REST_INFO
) R
WHERE RANKING = 1
ORDER BY FOOD_TYPE DESC
```

## 문제 3: 식품분류별 가장 비싼 식품의 정보 조회하기

https://school.programmers.co.kr/learn/courses/30/lessons/131116

- FOOD_PRODUCT 테이블에서 식품분류별로 가격이 제일 비싼 식품의 분류, 가격, 이름을 조회하는 SQL문을 작성
- 이때 식품분류가 '과자', '국', '김치', '식용유'인 경우만 출력
- 결과는 식품 가격을 기준으로 내림차순 정렬

### 코드:
```sql
SELECT F.CATEGORY, F.PRICE AS MAX_PRICE, F.PRODUCT_NAME
FROM FOOD_PRODUCT F
JOIN (
    SELECT CATEGORY, MAX(PRICE) AS M_PRICE
    FROM FOOD_PRODUCT
    WHERE CATEGORY IN ('과자', '국', '김치', '식용유')
    GROUP BY CATEGORY
) M ON F.CATEGORY = M.CATEGORY AND F.PRICE = M.M_PRICE
ORDER BY MAX_PRICE DESC
```

## 문제 4: 5월 식품들의 총매출 조회하기

https://school.programmers.co.kr/learn/courses/30/lessons/131117

- FOOD_PRODUCT와 FOOD_ORDER 테이블에서 생산일자가 2022년 5월인 식품들의 식품 ID, 식품 이름, 총매출을 조회하는 SQL문을 작성
- 이때 결과는 총매출을 기준으로 내림차순 정렬, 총매출이 같다면 식품 ID를 기준으로 오름차순 정렬

### 코드:
```sql
SELECT P.PRODUCT_ID,
       P.PRODUCT_NAME,
       SUM(PRICE*AMOUNT) TOTAL_SALES
FROM FOOD_PRODUCT P JOIN FOOD_ORDER O ON P.PRODUCT_ID = O.PRODUCT_ID
WHERE PRODUCE_DATE BETWEEN '2022-05-01' AND '2022-05-31'
GROUP BY P.PRODUCT_ID, P.PRODUCT_NAME
ORDER BY 3 DESC, 1
```
