## SQL

### 문제 풀이 정리

### 문제3
https://school.programmers.co.kr/learn/courses/30/lessons/59405

- 두 가지 방식으로 풀이했으며, 최종적으로는 **코드2**를 선택함

문제 조건에서 ‘가장 먼저 들어온 동물은 한 마리’라고 명시되어 있으므로, 간결하고 성능이 좋은 코드2 방식이 더 적합하다고 판단함

---

### 코드1: 서브쿼리 방식
```sql
SELECT NAME
FROM ANIMAL_INS
WHERE DATETIME = (SELECT MIN(DATETIME)
                  FROM ANIMAL_INS)
```
- 의미가 직관적이며, 같은 시간에 들어온 동물이 여러 마리일 경우 모두 출력됨
- 다만, 성능 면에서는 상대적으로 느릴 수 있음

### 코드2: 정렬 + LIMIT 방식
```sql
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```
- 간단하고 빠르며, 인덱스를 활용한 정렬로 성능이 우수함
- 다만, 여러 동물이 같은 시간에 들어온 경우라도 첫 1개만 조회됨
---

## Python

### 참고
- round(값, 소수점 자리수) : 결과값을 반올림하여 정수 반환
- round(62.499) 결과는 62 : 자리수를 0 또는 생략하면 정수 부분으로 반올림
- round(62.499, 1) 결과는 62.5 : 소수점 이하 자리 (오른쪽)
- round(62.499, -1) 결과는 60 : 정수 자리 (왼쪽)

### 문제4
- 짝수의 합을 구하는 과정은 두가지가 있다.
---
### 코드1:
```python
def solution(n):
    total=0
    for i in range(1, n+1):
        if i%2==0:
            total += i
    return total
```

### 코드2:
```python
def solution(n):
     return sum(range(2, n+1, 2))
```
