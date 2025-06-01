## 문제 1: 두 수의 합 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/120802

### 코드:
```python
def solution(num1, num2):
    answer = num1+num2
    return answer
```

## 문제 2: 두 수의 나눗셈

https://school.programmers.co.kr/learn/courses/30/lessons/120806

### 코드:
```python
def solution(num1, num2):
    answer = int((num1/num2)*1000)
    return answer
```

## 문제 3: 각도기

https://school.programmers.co.kr/learn/courses/30/lessons/120829

### 코드:
```python
def solution(angle):
    if 0 < angle < 90:
        return 1
    elif angle == 90:
        return 2
    elif 90 < angle < 180:
        return 3
    elif angle == 180:
        return 4
```

## 문제 4: 짝수의 합

https://school.programmers.co.kr/learn/courses/30/lessons/120831

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

## 문제 5: 배열의 평균값

https://school.programmers.co.kr/learn/courses/30/lessons/120817

### 코드:
```python
def solution(numbers):
    return sum(numbers) / len(numbers)
```
