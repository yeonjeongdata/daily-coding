## 문제 1: 성분으로 구분한 아이스크림 총 주문량

https://school.programmers.co.kr/learn/courses/30/lessons/133026

- 상반기 동안 각 아이스크림 성분 타입과 성분 타입에 대한 아이스크림의 총주문량을 총주문량이 작은 순서대로 조회하는 SQL 문을 작성
- 이때 총주문량을 나타내는 컬럼명은 TOTAL_ORDER로 지정

### 코드:
```sql
SELECT INGREDIENT_TYPE, SUM(TOTAL_ORDER) TOTAL_ORDER
FROM FIRST_HALF F JOIN ICECREAM_INFO I ON F.FLAVOR = I.FLAVOR
GROUP BY INGREDIENT_TYPE
ORDER BY SUM(TOTAL_ORDER)
```

## 문제 2: 루시와 엘라 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/59046

- 동물 보호소에 들어온 동물 중 이름이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 아이디와 이름, 성별 및 중성화 여부를 조회하는 SQL 문을 작성
- 결과는 아이디 순으로 조회

### 코드:
```sql
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE
FROM ANIMAL_INS
WHERE NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
ORDER BY 1
```

## 문제 3: 조건에 맞는 도서 리스트 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/144853

- BOOK 테이블에서 2021년에 출판된 '인문' 카테고리에 속하는 도서 리스트를 찾아서 도서 ID(BOOK_ID), 출판일 (PUBLISHED_DATE)을 출력하는 SQL문을 작성
- 결과는 출판일을 기준으로 오름차순 정렬
- PUBLISHED_DATE의 데이트 포맷이 예시와 동일해야 정답처리

### 코드:
```sql
SELECT BOOK_ID, DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d') PUBLISHED_DATE
FROM BOOK
WHERE YEAR(PUBLISHED_DATE) = 2021 AND CATEGORY = '인문'
ORDER BY 2
```

## 문제 4: 평균 일일 대여 요금 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/151136

- CAR_RENTAL_COMPANY_CAR 테이블에서 자동차 종류가 'SUV'인 자동차들의 평균 일일 대여 요금을 출력하는 SQL문을 작성
- 이때 평균 일일 대여 요금은 소수 첫 번째 자리에서 반올림하고, 컬럼명은 AVERAGE_FEE 로 지정

### 코드:
```sql
SELECT ROUND(AVG(DAILY_FEE),0) AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = 'SUV'
```
