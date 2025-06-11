### 문제1) 사용자에게 숫자 5개를 입력받고 총합과 평균을 출력

```python
total = 0
for i in range(5):
	num = int(input(f"{i+1}번째 숫자: "))
    total += num
print("총합:", total)
print("평균:", total / 5)
```

### 문제2) 숫자를 입력받아 그 수만큼 별(*)을 출력

```python
n = int(input("별 몇 개 출력할까요? "))
for i in range(n):
    print("*", end="")
```

> 참고) end=""
- print("*", end="") → 줄바꿈 없이 한 줄에 계속 출력
	- `end=" "`처럼 공백이나 다른 문자로도 바꿀 수 있음
- print("*") → 기본적으로 줄바꿈 포함됨

### 문제3) 사용자에게 정수를 입력받고, 양수인지 음수인지 출력

```python
num = int(input("정수를 입력하세요: "))

if num > 0:
    print("양수입니다.")
elif num < 0:
    print("음수입니다.")
else:
    print("0입니다.")
```

### 문제4) 두 정수 중 더 큰 수 출력

```python
a = int(input("첫 번째 정수: "))
b = int(input("두 번째 정수: "))

if a > b:
    print(f"{a}이 더 큽니다.")
elif b > a:
    print(f"{b}이 더 큽니다.")
else:
    print("두 수는 같습니다.")
```

### 문제5) 점수에 따른 등급 출력

- 90점 이상: A
- 80점 이상: B
- 70점 이상: C
- 60점 이상: D
- 그 외: F

```python
score = int(input("점수를 입력하세요: "))

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

### 문제6) 현재 시간에 따라 오전/오후 구분

```python
hour = int(input("현재 시각을 입력하세요 (0~23): "))

if 0 <= hour < 12:
    print("오전")
elif 12 <= hour <= 23:
    print("오후")
else:
    print("올바른 시간(0~23)을 입력하세요.")
```

### 문제7) 2와 3의 공배수 판별 

```python
num = int(input("숫자를 입력하세요: "))

if num % 2 == 0 and num % 3 == 0:
    print("2와 3의 공배수입니다.")
else:
    print("공배수가 아닙니다.")
```

### 문제8) for문을 사용하여 1부터 10까지 출력 

```python
for i in range(1, 11):
    print(i)
```

### 문제9) 1~100 사이의 짝수만 출력

```python
for i in range(1, 101):
    if i % 2 == 0:
        print(i)
```

### 문제10) 1부터 n까지의 합 구하기 

```python
n = int(input("n을 입력하세요: "))
total = 0

for i in range(1, n + 1):
    total += i

print("합:", total)
```

### 문제11) 리스트 항목 한 줄에 하나씩 출력

```python
fruits = ['apple', 'banana', 'grape']

for fruit in fruits:
    print(fruit)
```

### 문제12) 종료를 입력할 때까지 반복

```python
while True:
    word = input("입력: ")
    if word == "종료":
        print("→ 종료되었습니다.")
        break
```

### 문제13) 별찍기 1단계: 왼쪽 정렬 별 출력 

```python
n = int(input("줄 수를 입력하세요: "))

for i in range(1, n + 1):
    print("*" * i)
```

### 문제14) 별찍기 2단계: 오른쪽 정렬 별 출력

- 줄마다 공백 개수는 `n - i`
- 별은 `i`개
- `" " * (n - i) + "*" * i`를 출력

```python
n = int(input("줄 수를 입력하세요: "))

for i in range(1, n + 1):
    spaces = " " * (n - i)    # 공백 먼저
    stars = "*" * i           # 별 그다음
    print(spaces + stars)
```

### 문제15) 별찍기 3단계: 피라미드 별 출력

- 총 줄 수: `n`
- 각 줄마다 별 개수는 `2 * i - 1` (1, 3, 5, 7...)
- 공백은 `n - i`개
- 출력 구조: `" " * (n - i) + "*" * (2 * i - 1)`

```python
n = int(input("피라미드 높이를 입력하세요: "))

for i in range(1, n + 1):
    spaces = " " * (n - i)            # 좌측 공백
    stars = "*" * (2 * i - 1)         # 홀수 개수의 별
    print(spaces + stars)
```
