## 리스트 (`list`) 실습 문제

```python
fruits = ["apple", "banana", "cherry"]
```

### 1. 위 리스트에 `"orange"`를 추가

#### 첫 번째 시도 (실패. 개념 정리하기)
```python
fruits = ["apple", "banana", "cherry"]
print(fruits.append("orange"))
```

> 문제점)
- `fruits.append("orange")`는 리스트에 "orange"를 추가만 함
→ append() 자체는 None을 반환하므로, print(...) 하면 None이 출력됨

#### 최종 코드
```python
fruits = ["apple", "banana", "cherry"]
fruits.append("orange")
print(fruits)
```

### 2. 리스트의 두 번째 값 `"banana"`를 `"grape"`로 바꾸기 ⭐
- **리스트의 인덱스를 이용해 값 변경**

#### 코드
```python
fruits[1]="grape"
print(fruits)
```

### 3. 리스트에 `"kiwi"`를 1번 인덱스에 삽입

#### 코드
```python
fruits.insert(1, "kiwi")
print(fruits)
```

### 4. 리스트에서 `"cherry"`를 삭제

#### 코드
```python
fruits.remove("cherry")
print(fruits)
```

### 5. 마지막 요소를 제거하고 출력

#### 코드
```python
fruits.pop()
print(fruits)
```

### 6. 리스트를 오름차순으로 정렬

#### 코드
```python
fruits.sort()
print(fruits)
```

![](https://velog.velcdn.com/images/ckduswjd/post/33076fcf-2742-4421-8329-8246b843ed3f/image.png)

- 둘 다 다음과 같은 옵션 사용 가능
1. key=
→ 정렬 기준 지정 (예: 길이 기준 정렬 key=len)
2. reverse=True
→ 내림차순 정렬

> 상황별 추천
- 원본을 변경해도 괜찮을 때 : list.sort()
- 원본을 유지하고 복사본이 필요할 때 : sorted()

### 7. 리스트의 순서를 뒤집기

#### 코드
```python
fruits.reverse()
print(fruits)
```

### 8. 리스트에서 `"apple"`의 인덱스를 출력
#### 코드
```python
print(fruits.index("apple"))
```

> 참고) 인덱스를 출력하는 건 아래와 같이 쓰면 안됨
```python
fruits.index("apple")
print(fruits)
```

### 9. 리스트에 `"apple"`을 하나 더 추가하고, `"apple"`이 몇 개 있는지 출력

#### 코드
```python
fruits.append("apple")
print(fruits.count("apple"))
```

### 10. 리스트의 모든 항목을 비우기

#### 코드
```python
fruits.clear()
print(fruits)
```

---

## 튜플 (`tuple`) 실습 문제

```python
scores = (90, 85, 90, 70)
```

### 1. 튜플에서 첫 번째 값을 출력

#### 코드
```python
print(scores[0])
```
### 2. 튜플에서 마지막 값을 출력

#### 코드
```python
print(scores[-1])
```

### 3. 튜플의 길이 구하기

#### 코드
```python
print(len(scores))
```

### 4. `"90"`이 몇 번 나오는지 출력

#### 코드
```python
print(scores.count(90))
```

### 5. `"70"`이 몇 번째 인덱스에 있는지 출력

#### 코드
```python
print(scores.index(70))
```

### 6. 튜플 전체를 for문으로 출력

#### 코드
```python
for i in scores:
    print(i)
```

### 7. 튜플을 리스트로 바꾸기

#### 코드
```python
print(list(scores))
```

### 8. 바뀐 리스트에 `"100"`을 추가하고 다시 튜플로 바꾸기
#### 코드
```python
n_scores = list(scores)
n_scores.append(100)
print(tuple(n_scores))
```

### 9. 튜플 안에 있는 값 중 최댓값을 출력

#### 코드
```python
print(max(n_scores))
```

### 10. 튜플을 오름차순으로 정렬한 새 튜플을 만들기
- 리스트 변환 후 `sorted()`

#### 코드
```python
print(tuple(sorted(list(n_scores))))
```

---

## 딕셔너리 (`dict`) 실습 문제

```python
person = {"name": "지민", "age": 23}
```

### 1. `"job"`이라는 key를 추가하고 `"학생"`이라는 값을 넣기 ⭐

- 파이썬에서 딕셔너리에 새로운 key-value 쌍을 추가할 때는 다음과 같이 작성
`딕셔너리이름[새로운_키] = 값`

#### 코드
```python
person["job"] = "학생"
print(person)
```

### 2. `"age"`를 24로 수정

- 딕셔너리에서 기존 key의 값을 바꾸고 싶을 때는 새 값을 대입
`딕셔너리[기존_key] = 새로운_값`

#### 코드
```python
person["age"] = 24
print(person)
```

### 3. `"name"` 값을 출력

#### 코드
```python
print(person["name"])
```

![](https://velog.velcdn.com/images/ckduswjd/post/27524fa3-04cb-448f-a76e-ec5ced1aeb05/image.png)

> .get(...) 추천


### 4. 존재하지 않는 key `"address"`를 안전하게 출력하는 코드를 작성 (`get()`)

#### 코드
```python
print(person.get("address"))
```

### 5. 딕셔너리의 모든 key를 출력

#### 코드
```python
print(person.keys())
```

### 6. 딕셔너리의 모든 value를 출력

#### 코드
```python
print(person.values())
```

> 참고 ⭐
- 키/값 둘 다 리스트로 변환 가능
→ `list(person.values())`

### 7. 딕셔너리의 (key, value) 쌍을 모두 출력

#### 코드
```python
print(person.items())
```

### 8. `"job"` key를 삭제

#### 코드
```python
person.pop("job")
print(person)
```

### 9. 새로운 딕셔너리 `{"gender": "female"}`을 기존 딕셔너리에 병합

#### 코드
```python
person.update({"gender": "female"})
print(person)
```

### 10. 딕셔너리의 모든 항목을 삭제

#### 코드
```python
person.clear()
print(person)
```

---

## 튜플 (`tuple`) 실습 문제

```python
scores = (90, 85, 90, 70)
```

## 집합 (`set`) 실습 문제

```python
a = {1, 2, 3, 3, 2}
b = {3, 4, 5}
```

### 1. `a`에 6을 추가

#### 코드
```python
a.add(6)
print(a)
```

### 2. `a`에서 2를 제거

#### 코드
```python
a.remove(2)
print(a)
```

### 3. 없는 값 99를 안전하게 제거 (`discard`)

#### 코드
```python
a.discard(99)
print(a)
```

### 4. `a`와 `b`의 합집합

#### 코드
```python
print(a.union(b))
```

### 5. `a`와 `b`의 교집합

#### 코드
```python
print(a.intersection(b))
```

### 6. `a`와 `b`의 차집합(`a - b`)

#### 코드
```python
print(a.difference(b))
```

### 7. 리스트 `[7, 8, 9]`를 `a`에 한 번에 추가 (`update`)

#### 코드
```python
a.update([7, 8, 9])
print(a)
```

### 8. `a`를 비우기

#### 코드
```python
a.clear()
print(a)
```

### 9. 두 집합이 서로소인지 확인 (`isdisjoint`)

#### 코드
```python
a = {1, 3, 6, 7, 8, 9}
print(a.isdisjoint(b))
```
### 10. 집합 `c = {1, 2}`가 `a`의 부분집합인지 확인 (`issubset`)

#### 코드
```python
c={1,2}
print(c.issubset(a))
```
