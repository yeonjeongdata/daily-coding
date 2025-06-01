## 문제 1: 동명 동물 수 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/59041

- 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성
- 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회

### 코드:
```sql
SELECT NAME, COUNT(*) COUNT
FROM ANIMAL_INS
WHERE NAME IS NOT NULL
GROUP BY NAME
having COUNT(NAME)>=2
ORDER BY 1
```

## 문제 2: 아픈 동물 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/59036

- 동물 보호소에 들어온 동물 중 아픈 동물의 아이디와 이름을 조회하는 SQL 문을 작성
- 이때 결과는 아이디 순으로 조회

### 코드:
```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION = 'Sick'
ORDER BY 1
```

## 문제 3: 	상위 n개 레코드

https://school.programmers.co.kr/learn/courses/30/lessons/59405

- 동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성

### 코드:
```sql
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```

## 문제 4: 최솟값 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/59038

- 동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성

### 코드:
```sql
SELECT DATETIME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```

## 문제 5: 어린 동물 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/59037

- 동물 보호소에 들어온 동물 중 젊은 동물의 아이디와 이름을 조회하는 SQL 문을 작성
- 이때 결과는 아이디 순으로 조회

### 코드:
```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION != 'Aged'
ORDER BY 1
```
