## SQL

### 문제 2: 즐겨찾기가 가장 많은 식당 정보 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131123

- REST_INFO 테이블에서 음식종류별로 즐겨찾기수가 가장 많은 식당의 음식 종류, ID, 식당 이름, 즐겨찾기수를 조회하는 SQL문을 작성
- 이때 결과는 음식 종류를 기준으로 내림차순 정렬

#### 첫 번째 시도 (성공. 코드 개선 필요) – IN + 서브쿼리 방식
```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM REST_INFO
WHERE (FOOD_TYPE, FAVORITES) IN (SELECT FOOD_TYPE, MAX(FAVORITES)
                   FROM REST_INFO
                   GROUP BY FOOD_TYPE)
ORDER BY 1 DESC
```

- `(A, B) IN (...)` : 일부 DBMS만 지원 → `JOIN ON A = ... AND B = ...` : 모든 DBMS 지원
> 공통점) 동일 값을 모두 출력

#### 개선 코드1 (JOIN 방식)
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
---

#### 코드2 (윈도우 함수( ROW_NUMBER() ). 개선 필요)
```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM (
    SELECT *, ROW_NUMBER() OVER (PARTITION BY FOOD_TYPE ORDER BY FAVORITES DESC) AS RN
    FROM REST_INFO
) R
WHERE RN = 1
ORDER BY FOOD_TYPE DESC
```

- `FAVORITES`가 동률인 경우 1개만 임의 선택됨 → 복수 반환 원하면 RANK() 또는 DENSE_RANK() 사용
- SELECT절에 *보다는 필요한 컬럼만 명시적으로 지정하는 것이 더 좋음

#### 개선 코드2 (DENSE_RANK()로 동률 포함)
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
---

### 참고 : 윈도우 함수
- 집계 함수처럼 동작하지만, 결과를 그룹별로 나누지 않고 원본 행 수를 유지하면서 결과 컬럼으로 추가
- 대표적인 윈도우 함수 : ROW_NUMBER(), RANK(), DENSE_RANK() 등

```sql
SELECT 컬럼명,
       함수이름() OVER (
           PARTITION BY 그룹기준컬럼
           ORDER BY 정렬기준컬럼 [ASC|DESC]
       ) AS 별칭
FROM 테이블명
```

> 함수이름
1. ROW_NUMBER() : 각 파티션 내에서 순위를 1부터 부여. 동일 값이라도 중복 순위 없음
2. DENSE_RANK() : 동일 값은 동일 순위 부여 (예. 공동 1등 두명 → 다음은 2등)
3, RANK() : 동일 값은 동일 순위 부여. 다음 값은 점프 (ex: 공동 1등 두 명 → 다음은 3등)

> PARTITION BY: 그룹핑 기준 (SQL의 GROUP BY처럼 작동하지만, 행을 나누지 않음)
>
> ORDER BY: 윈도우 함수 적용 시 정렬 기준

---

### 문제 3: 식품분류별 가장 비싼 식품의 정보 조회하기

https://school.programmers.co.kr/learn/courses/30/lessons/131116

- FOOD_PRODUCT 테이블에서 식품분류별로 가격이 제일 비싼 식품의 분류, 가격, 이름을 조회하는 SQL문을 작성
- 이때 식품분류가 '과자', '국', '김치', '식용유'인 경우만 출력
- 결과는 식품 가격을 기준으로 내림차순 정렬

#### 첫 번째 시도 (실패)
```sql
SELECT F.CATEGORY, F.PRICE AS MAX_PRICE, F.PRODUCT_NAME
FROM FOOD_PRODUCT F JOIN
    (SELECT CATEGORY, MAX(PRICE)
     FROM FOOD_PRODUCT
     GROUP BY CATEGORY) M
     ON F.CATEGORY=M.CATEGORY AND F.PRICE=M.MAX(PRICE)
WHERE F.CATEGORY IN ('과자', '국', '김치', '식용유')
ORDER BY MAX_PRICE DESC
```

> 문제점
1. 서브쿼리에서 별칭 사용 → `SELECT CATEGORY, MAX(PRICE) AS MAX_PRICE`
2. JOIN 조건에서 컬럼 직접 호출 불가 → `F.PRICE=M.MAX_PRICE` (서브쿼리의 별칭 컬럼명으로 비교)
3. WHERE 조건을 서브쿼리에서 미리 적용하면 효율 증가

#### 개선된 코드
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

---

## Python

https://velog.io/@ckduswjd/DAY25-파이썬-개인-과제-도전

