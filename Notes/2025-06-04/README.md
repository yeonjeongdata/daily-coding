## SQL

### 참고
> SUBSTR(대상 문자열, 추출시작 위치, 추출길이(선택))

---

## Python

### 문제1

#### 코드1
```python
def solution(x):
    tot = sum(int(i) for i in str(x))
    if x%tot == 0:
        return True
    else:
        return False
```

> 파이썬에서는 True/False로 쓰는 것 잊지 말기 (true/false로 쓰면 안됨)

#### 축약된 코드1
```python
def solution(x):
    tot = sum(int(i) for i in str(x))
    return x%tot == 0
```
---
#### 코드2 (map함수 사용)
```python
def solution(x):
    tot = sum(map(int, str(x)))
    return x%tot == 0
```

* 참고 : map 함수
- map(함수, 반복가능한자료형)
  
> 반복 가능한 자료형(예: 리스트, 문자열 등)의 각 요소에 함수를 적용
> 
> 결과는 map 객체로 반환되며, 보통 list()나 sum() 등으로 감싸서 사용
> 
- 예: map(int, str(x)) → "123"의 각 문자를 1, 2, 3으로 변환

---

### 문제3, 문제5

풀이 과정은 velog에 정리

https://velog.io/@ckduswjd/DAY18-파이썬-코드카타

- 참고
> num/2 : float 자료형을 반환 → //를 사용하여 int 자료형을 유지

> arr이 리스트인 경우, range(arr)을 쓰면 오류가 발생
> 
> return 은 마지막에 한 번만 사용하기
> 
> for문과 append()는 분리해서 사용
> 
> len(ele) == 0 대신 if ele 사용 → 빈 리스트는 False니까 더 간결

### 문제4

> list.index(x)
- 리스트에서 x의 인덱스를 찾음
- 예1) ["a", "b"].index("b") → 1
- 예2) seoul = ["Jane", "Kim"]
position = seoul.index("Kim") → 1

> f"문자열 {변수}"
- 변수 값을 문자열 안에 삽입 (중괄호 안에 변수나 식을 넣으면 해당 값으로 자동으로 바뀜)
- 예) f"나이는 {age}" → "나이는 20"
