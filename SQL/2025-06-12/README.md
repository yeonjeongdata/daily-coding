## 문제 1: 조건에 맞는 사용자와 총 거래금액 조회하기

https://school.programmers.co.kr/learn/courses/30/lessons/164668

- USED_GOODS_BOARD와 USED_GOODS_USER 테이블에서 완료된 중고 거래의 총금액이 70만 원 이상인 사람의 회원 ID, 닉네임, 총거래금액을 조회하는 SQL문을 작성
- 결과는 총거래금액을 기준으로 오름차순 정렬

### 코드:
```sql
SELECT U.USER_ID,
       U.NICKNAME,
       SUM(B.PRICE) TOTAL_SALES
FROM USED_GOODS_BOARD B JOIN USED_GOODS_USER U ON B.WRITER_ID = U.USER_ID
WHERE B.STATUS = 'DONE'
GROUP BY U.USER_ID, U.NICKNAME
HAVING SUM(B.PRICE)>=700000
ORDER BY 3
```

## 문제 2: 가격대 별 상품 개수 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/131530

- PRODUCT 테이블에서 만원 단위의 가격대 별로 상품 개수를 출력하는 SQL 문을 작성
- 이때 컬럼명은 각각 컬럼명은 PRICE_GROUP, PRODUCTS로 지정
- 가격대 정보는 각 구간의 최소금액(10,000원 이상 ~ 20,000 미만인 구간인 경우 10,000)으로 표시
- 결과는 가격대를 기준으로 오름차순 정렬

### 코드1 (DIV 연산자 사용)
```sql
SELECT (PRICE DIV 10000)*10000 PRICE_GROUP,
       COUNT(*) PRODUCTS
FROM PRODUCT
GROUP BY PRICE_GROUP
ORDER BY PRICE_GROUP
```

### 코드2 (FLOOR() 함수 사용)
```sql
SELECT FLOOR(PRICE / 10000)*10000 PRICE_GROUP,
       COUNT(*) PRODUCTS
FROM PRODUCT
GROUP BY PRICE_GROUP
ORDER BY PRICE_GROUP
```

## 문제 3: 3월에 태어난 여성 회원 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131120

- MEMBER_PROFILE 테이블에서 생일이 3월인 여성 회원의 ID, 이름, 성별, 생년월일을 조회하는 SQL문을 작성
- 이때 전화번호가 NULL인 경우는 출력대상에서 제외
- 결과는 회원ID를 기준으로 오름차순 정렬
- DATE_OF_BIRTH의 데이트 포맷이 예시와 동일해야 정답처리

### 코드:
```sql
SELECT MEMBER_ID,
       MEMBER_NAME,
       GENDER,
       DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d') DATE_OF_BIRTH
FROM MEMBER_PROFILE
WHERE MONTH(DATE_OF_BIRTH) = 3 AND GENDER = 'W' AND TLNO IS NOT NULL
ORDER BY 1
```

## 문제 4: 대여 기록이 존재하는 자동차 리스트 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/157341

- CAR_RENTAL_COMPANY_CAR 테이블과 CAR_RENTAL_COMPANY_RENTAL_HISTORY 테이블에서 자동차 종류가 '세단'인 자동차들 중 10월에 대여를 시작한 기록이 있는 자동차 ID 리스트를 출력하는 SQL문을 작성
- 자동차 ID 리스트는 중복이 없어야 하며, 자동차 ID를 기준으로 내림차순 

### 코드:
```sql
SELECT DISTINCT(C.CAR_ID) CAR_ID
FROM CAR_RENTAL_COMPANY_CAR C JOIN CAR_RENTAL_COMPANY_RENTAL_HISTORY H ON C.CAR_ID = H.CAR_ID
WHERE C.CAR_TYPE = '세단' AND MONTH(H.START_DATE) = 10
ORDER BY 1 DESC
```
