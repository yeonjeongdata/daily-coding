## 문제 1: 하샤드 수

https://school.programmers.co.kr/learn/courses/30/lessons/12947

### 코드1:
```python
def solution(x):
    tot = sum(int(i) for i in str(x))
    if x%tot == 0:
        return True
    else:
        return False
```

### 축약된 코드1:
```python
def solution(x):
    tot = sum(int(i) for i in str(x))
    return x%tot == 0
```

### 코드2 (map함수 사용)
```python
def solution(x):
    tot = sum(map(int, str(x)))
    return x%tot == 0
```

## 문제 2: 두 정수 사이의 합

https://school.programmers.co.kr/learn/courses/30/lessons/12912

### 코드1:
```python
def solution(a, b):
    answer = sum(range(min(a, b), max(a, b) + 1))
    return answer
```

### 코드2 (수학 공식 풀이)
```python
def solution(a, b):
    n = abs(a-b) + 1     # 항의 개수
    return (a+b) * n // 2  # 등차수열 합 공식
```
- 등차수열 공식: (첫항 + 끝항) × 항의 개수 ÷ 2
- 코드1보다 빠르게 실행됨

## 문제 3: 콜라츠 추측

https://school.programmers.co.kr/learn/courses/30/lessons/12943

### 코드:
```python
def solution(num):
    if num==1:
        return 0
    count=0
    while num !=1:
        if num%2==0:
            num=num//2
        else:
            num=num*3+1
        count+=1
    return -1 if count >= 500 else count
```

## 문제 4: 서울에서 김서방 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/12919

### 코드:
```python
def solution(seoul):
    position = seoul.index('Kim')
    return f"김서방은 {position}에 있다"
```

## 문제 5: 나누어 떨어지는 숫자 배열

https://school.programmers.co.kr/learn/courses/30/lessons/12910

### 코드:
```python
def solution(arr, divisor):
    ele = []
    for i in arr:
        if i%divisor == 0:
            ele.append(i)
    return [-1] if len(ele)==0 else sorted(ele)
```

### 축약+개선된 코드:
```python
def solution(arr, divisor):
    ele = sorted([i for i in arr if i % divisor == 0])
    return ele if ele else [-1]
```
