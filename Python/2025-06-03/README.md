## 문제 1: x만큼 간격이 있는 n개의 숫자

https://school.programmers.co.kr/learn/courses/30/lessons/12954

### 코드:
```python
def solution(x, n):
    return [x*i for i in range(1, n+1)]
```

## 문제 2: 자연수 뒤집어 배열로 만들기

https://school.programmers.co.kr/learn/courses/30/lessons/12932

### 코드1 ( reverse() ):
```python
def solution(n):
    answer = [int(i) for i in str(n)]
    answer.reverse()
    return answer
```

### 코드2 ( [::-1] ):
```python
def solution(n):
    answer = [int(i) for i in str(n)][::-1]
    return answer
```

## 문제 3: 문자열을 정수로 바꾸기

https://school.programmers.co.kr/learn/courses/30/lessons/12925

### 코드:
```python
def solution(s):
    answer = int(s)
    return answer
```

## 문제 4: 정수 제곱근 판별

https://school.programmers.co.kr/learn/courses/30/lessons/12934

### 코드:
```python
import math

def solution(n):
    x = math.isqrt(n)
    if x * x == n:
        return (x + 1) ** 2
    else:
        return -1
```

## 문제 5: 정수 내림차순으로 배치하기

https://school.programmers.co.kr/learn/courses/30/lessons/12933

### 코드:
```python
def solution(n):
    answer = int(''.join(sorted(str(n), reverse=True)))
    return answer
```
