## 문제 1: 경기도에 위치한 식품창고 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131114

- FOOD_WAREHOUSE 테이블에서 경기도에 위치한 창고의 ID, 이름, 주소, 냉동시설 여부를 조회하는 SQL문을 작성
- 이때 냉동시설 여부가 NULL인 경우, 'N'으로 출력
- 결과는 창고 ID를 기준으로 오름차순 정렬

### 코드:
```sql
SELECT WAREHOUSE_ID,
       WAREHOUSE_NAME,
       ADDRESS,
       COALESCE(FREEZER_YN, 'N') AS FREEZER_YN
FROM FOOD_WAREHOUSE
WHERE ADDRESS LIKE '경기도%'
ORDER BY WAREHOUSE_ID
```

## 문제 2: 강원도에 위치한 생산공장 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131112

- FOOD_FACTORY 테이블에서 강원도에 위치한 식품공장의 공장 ID, 공장 이름, 주소를 조회하는 SQL문을 작성
- 이때 결과는 공장 ID를 기준으로 오름차순 정렬

### 코드:
```sql
SELECT FACTORY_ID, FACTORY_NAME, ADDRESS
FROM FOOD_FACTORY
WHERE ADDRESS LIKE '강원도%'
ORDER BY 1
```

## 문제 3: DATETIME에서 DATE로 형 변환

https://school.programmers.co.kr/learn/courses/30/lessons/59414

- ANIMAL_INS 테이블에 등록된 모든 레코드에 대해, 각 동물의 아이디와 이름, 들어온 날짜를 조회하는 SQL문을 작성
> 시각(시-분-초)을 제외한 날짜(년-월-일)만 보여주기
- 이때 결과는 아이디 순으로 조회

### 코드:
```sql
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, '%Y-%m-%d') AS 날짜
FROM ANIMAL_INS
ORDER BY 1
```

## 문제 4: 흉부외과 또는 일반외과 의사 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/132203

- DOCTOR 테이블에서 진료과가 흉부외과(CS)이거나 일반외과(GS)인 의사의 이름, 의사ID, 진료과, 고용일자를 조회하는 SQL문을 작성
- 이때 결과는 고용일자를 기준으로 내림차순 정렬하고, 고용일자가 같다면 이름을 기준으로 오름차순 정렬

### 코드:
```sql
SELECT DR_NAME, DR_ID, MCDP_CD, DATE_FORMAT(HIRE_YMD, '%Y-%m-%d') AS HIRE_YMD
FROM DOCTOR
WHERE MCDP_CD IN ('CS', 'GS')
ORDER BY HIRE_YMD DESC, DR_NAME
```

## 문제 5: 가격이 제일 비싼 식품의 정보 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131115

- FOOD_PRODUCT 테이블에서 가격이 제일 비싼 식품의 식품 ID, 식품 이름, 식품 코드, 식품분류, 식품 가격을 조회하는 SQL문을 작성

### 코드:
```sql
SELECT PRODUCT_ID, PRODUCT_NAME, PRODUCT_CD, CATEGORY, PRICE
FROM FOOD_PRODUCT
WHERE PRICE = (SELECT MAX(PRICE) FROM FOOD_PRODUCT)
```
