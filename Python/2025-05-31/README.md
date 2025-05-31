## 문제 1: 두 수의 차 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/120803

### 코드:
```python
def solution(num1, num2):
    answer = num1-num2
    return answer
```

## 문제 2: 두 수의 곱 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/120804

### 코드:
```python
def solution(num1, num2):
    answer = num1*num2
    return answer
```

## 문제 3: 몫 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/120805

### 코드:
```python
def solution(num1, num2):
    answer = num1//num2
    return answer
```

## 문제 4: 나이 출력

https://school.programmers.co.kr/learn/courses/30/lessons/120820

* 풀이 접근
- ( 나이(age) - 1 )은 태어난 후 경과한 연수
- 출생 연도 = 2022 - (age - 1) = 2023 - age

### 코드:
```python
def solution(age):
    answer = 2023-age
    return answer
```

## 문제 5: 숫자 비교하기

https://school.programmers.co.kr/learn/courses/30/lessons/120807

### 코드:
```python
def solution(num1, num2):
    return 1 if num1==num2 else -1
```
