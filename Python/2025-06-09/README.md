## 문제 1: 음양 더하기

https://school.programmers.co.kr/learn/courses/30/lessons/76501

### 코드1:
```python
def solution(absolutes, signs):
    res = []
    for a, s in zip(absolutes, signs):
        res.append(a if s else -a)
    return sum(res)
```

### 코드2:
```python
def solution(absolutes, signs):
    result = 0
    for a, s in zip(absolutes, signs):
        if s:
            result += a
        else:
            result -= a
    return result
```

### 축약된 코드:
```python
def solution(absolutes, signs):
    return sum(a if s else -a for a, s in zip(absolutes, signs))
```

## 문제 2: 핸드폰 번호 가리기

https://school.programmers.co.kr/learn/courses/30/lessons/12948

### 코드:
```python
def solution(phone_number):
    return '*'*(len(phone_number)-4) + phone_number[-4:]
```

## 문제 3: 없는 숫자 더하기

https://school.programmers.co.kr/learn/courses/30/lessons/86051

### 코드1:
```python
def solution(numbers):
    total = 0
    for i in range(10):
        if i not in numbers:
            total += i
    return total
```

### 코드2:
```python
def solution(numbers):
    return sum(set(range(10)) - set(numbers))
```

## 문제 4: 제일 작은 수 제거하기

https://school.programmers.co.kr/learn/courses/30/lessons/12935

### 코드:
```python
def solution(arr):
    arr.remove(min(arr))
    return [-1] if len(arr)==0 else arr
```

### 코드2:
```python
def solution(arr):
    if len(arr) == 1:
        return [-1]
    min_val = min(arr)
    return [x for x in arr if x != min_val]
```
## 문제 5: 가운데 글자 가져오기

https://school.programmers.co.kr/learn/courses/30/lessons/12903

### 코드:
```python
def solution(s):
    mid = len(s)//2
    return s[mid-1:mid+1] if len(s)%2==0 else s[mid]
```
