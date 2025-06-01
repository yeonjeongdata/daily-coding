## SQL

### 참고

- LOWER() : 모든 문자를 **소문자**로 변환
- UPPER() : 모든 문자를 **대문자**로 변환

- COALESCE() : 여러 개의 컬럼 중 NULL이 아닌 첫번째 값 반환
> 예. COALESCE(bonus, commission, 0) → bonus가 NULL이면 commission, 둘 다 NULL이면 0 반환
- 모두 NULL이면 NULL을 반환
---

## Python

### 참고

- range(시작값, 끝값, 증가값) : 이때, 끝값으로 적은 값은 포함되지 않음

### 문제3 : 자릿수 더하기

https://school.programmers.co.kr/learn/courses/30/lessons/12931

#### 코드:
```python
def solution(n):
    return sum(int(i) for i in str(n))
```

- 참고
> str(n) : 자연수 n을 문자열로 변환
> 
> int(i) : 가져온 각 자릿수를 정수로 변환

### 문제5 : 나머지가 1이 되는 수 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/87389

#### 코드:
```python
def solution(n):
    for x in range (1,n):
        if n%x==1:
            return x
```

- 참고
> x==n일 경우는 어차피 n%n=0이므로 검사할 필요가 없음 → 비효율적이므로 range(1,n)을 써도 충분
