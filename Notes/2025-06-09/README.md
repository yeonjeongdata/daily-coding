## SQL

### 날짜 조회
- `LIKE '2022-01%'` 조건은 문자열 비교 방식이라 날짜 타입 처리에 비효율적일 수 있음
- ` WHERE S.SALES_DATE BETWEEN '2022-01-01' AND '2022-01-31' 또는 `WHERE S.SALES_DATE >= '2022-01-01' AND S.SALES_DATE < '2022-02-01'` 로 작성

---

## Python

### 문제 1~3에 대한 풀이는 velog에 작성

https://velog.io/@ckduswjd/DAY19-파이썬-코드카타

#### 참고 : zip()
zip(list1, list2) : 두 리스트를 쌍으로 묶어서 반복
```python
for a, b in zip(absolutes, signs):
    # a는 absolutes[i], b는 signs[i]
```
→ 두 리스트를 같은 인덱스로 같이 다루고 싶을 때 사용하면 편리

#### 참고2 : replace()
`replace(부분문자열, 다른문자열)`은 문자열 내 해당 부분 전체를 찾아서 바꾸는 함수 (예: `"abcabc".replace("abc", "*") → "**"`)

#### 참고3 : set()
- set은 파이썬의 자료형 중 하나로, 중복이 없는 값들의 모음(집합)을 나타냄
> set의 특징
> 1. 중복을 허용하지 않음
> 2. 순서가 없음 (인덱스로 접근 불가)
> 3. 집합 연산 가능 (차집합, 합집합 등)

---

### 문제4 : 제일 작은 수 제거하기
- 정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 작성하기
- 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴

![image](https://github.com/user-attachments/assets/51ef7b8d-016d-437a-aa14-11dba5b962e4)


#### 첫번째 시도 (실패: 개념 정리 필요)
```python
def solution(arr):
    arr.remove(min(i) for i in arr)
    return [-1] if len(arr)==0 else arr
```

> 문제점 요약
> 1. `min(i) for i in arr` → 문법 오류
>     - `min(arr)` → arr에서 가장 작은 수 하나 반환
> 2. `remove()`는 **값**을 제거 (인덱스 아님)

#### 최종 코드
```python
def solution(arr):
    arr.remove(min(arr))
    return [-1] if len(arr)==0 else arr
```

#### 개선 코드1 (원본 보호)
```python
def solution(arr):
    if len(arr)==1:
        return [-1]
    arr_copy = arr[:]
    arr_copy.remove(min(arr_copy))
    return arr_copy
```

> `remove()`는 원본 배열 `arr`을 수정하므로, 복사본을 만들면 안전하게 처리 가능
특히 함수 내부에서 리스트를 수정하지 않는 습관이 중요함

#### 개선 코드2

```python
def solution(arr):
    if len(arr)==1:
        return [-1]
    min_val = min(arr)
    return [x for x in arr if x != min_val]
```

> `remove()`는 리스트에 해당 값이 2개 이상 있을 경우 **첫 번째 값만 제거**하지만, 이 방식은 **가장 작은 값이 여러 개 있어도 전부 제거** 가능
>
> 문제 조건에는 ‘모든 값이 서로 다름’이라 이 차이는 중요하지 않지만, 더 일반화된 방식

### 문제5 : 가운데 글자 가져오기
- 단어 `s`의 가운데 글자를 반환하는 함수, solution 작성하기
- 단어의 길이가 짝수면 가운데 두 글자, 홀수면 가운데 한 글자를 반환

#### 첫번째 시도 (실패: 개념 정리 필요)
```python
def solution(s):
    return range(len(s)//2-1, len(s)//2) if len(s)%2==0 else s[(len(s)-3)]
```

> 문제점 요약
1. `range()`는 숫자의 나열 객체로, 문자열 추출에 직접 사용 불가능
	- `range`는 반복문(`for i in range(...)`) 등에 유용하지만, 문자열 슬라이싱에 사용할 수 없음
	- 예: `s[range(...)]` → 오류 발생
2. 문자열 슬라이싱은 `s[start:end]` 형태로 해야 하며, **end는 포함되지 않음**에 유의할 것

#### 최종 코드
```python
def solution(s):
    mid = len(s)//2
    return s[mid-1:mid+1] if len(s)%2==0 else s[mid]
```

> `len(s)//2`로 가운데 인덱스를 구한 뒤, 짝수/홀수 조건에 따라 슬라이싱 범위를 다르게 설정
