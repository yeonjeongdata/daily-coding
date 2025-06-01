## 문제 1: 짝수와 홀수

https://school.programmers.co.kr/learn/courses/30/lessons/12937

### 코드:
```python
def solution(num):
    return "Even" if num%2==0 else "Odd"
```

## 문제 2: 평균 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/12944

### 코드:
```python
def solution(arr):
    return sum(arr) / len(arr)
```

## 문제 3: 자릿수 더하기

https://school.programmers.co.kr/learn/courses/30/lessons/12931

### 코드:
```python
def solution(n):
    return sum(int(i) for i in str(n))
```

## 문제 4: 약수의 합

https://school.programmers.co.kr/learn/courses/30/lessons/12928

### 코드:
```python
def solution(n):
    return sum(i for i in range(1, n + 1) if n % i == 0)
```

## 문제 5: 나머지가 1이 되는 수 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/87389

### 코드:
```python
def solution(n):
    for x in range (1,n):
        if n%x==1:
            return x
```
