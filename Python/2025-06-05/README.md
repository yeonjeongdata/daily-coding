## 실습

### 문제1) 이름과 나이를 입력받아 출력하기
```python
name = input("이름을 입력하세요: ")
age = int(input("나이를 입력하세요: "))
print(f"{name}님의 나이는 {age}살입니다.")
```

> `print(name + "님의 나이는 " + age + "살입니다.")`을 사용하려면,
`name`과 `age`의 데이터 타입이 동일해야 됨
> 
> → 데이터 타입이 다를 경우, `f-stirng` 사용 (더 유용)

### 문제2) 숫자 입력 후 더하기
```python
num1 = int(input("첫 번째 숫자: "))
num2 = int(input("두 번째 숫자: "))
print(f"두 수의 합은 {num1+num2}입니다.")
```

### 문제3) 현재 시각(시, 분)을 입력받아 오전/오후 여부를 출력하기
> 1-12: 오전 / 13-24: 오후

```python
hour = int(input("시: "))
min = int(input("분: "))

if hour < 13:
    print(f"오전 {hour}시 {min}분입니다.")
else:
    print(f"오후 {hour-12}시 {min}분입니다.")
```

## 과제
- **Hello World 출력하기**
    - `Hello, World!`를 출력하는 코드를 작성하기

```python
print("Hello, World!")
```

- **이름 입력받아 출력하기**
    - 사용자에게 이름을 입력받고, `"000님, 반갑습니다!"` 라고 출력하기
    - 예: `홍길동님, 반갑습니다!`

```python
name = input("이름: ")
print(f"{name}님, 반갑습니다!")
```

- **정수 두 개 입력받아 출력하기**
    - 사용자에게 두 정수를 입력받고, `"첫 번째 숫자: ___, 두 번째 숫자: ___"` 형식으로 출력하기

```python
a = int(input("첫 번째 정수: "))
b = int(input("두 번째 정수: "))
print(f"첫 번째 숫자: {a}, 두 번째 숫자: {b}")
```
- **나이 입력받아 내년 나이 출력하기**
    - 현재 나이를 입력받아, 내년 나이를 `"당신의 내년 나이는 ___살입니다."` 형식으로 출력하기

```python
age = int(input("현재 나이: "))
print(f"당신의 내년 나이는 {age+1}살입니다.")
```
- **덧셈 프로그램 만들기**
    - 숫자 두 개를 입력받고, 두 수의 합을 출력하기
    - 예: `3과 5의 합은 8입니다.`

```python
num1 = int(input("첫 번째 숫자: "))
num2 = int(input("두 번째 숫자: "))
print(f"{num1}과 {num2}의 합은 {num1+num2}입니다.")
```
- **곱셈 프로그램 만들기**
    - 숫자 두 개를 입력받아 곱한 결과를 `"곱셈 결과: ___"` 형태로 출력하기
```python
num1 = int(input("첫 번째 숫자: "))
num2 = int(input("두 번째 숫자: "))
print(f"곱셈 결과: {num1*num2}")
```
- **문자열 연결 출력하기**
    - 사용자에게 이름과 학교 이름을 입력받아,
        `"홍길동님은 서울고등학교에 다니고 있습니다."` 형식으로 출력하기
```python
name = input("이름: ")
school = input("학교명: ")
print(f"{name}님은 {school}에 다니고 있습니다.")
```

- **문장 내 변수 삽입**
    - 과목명과 점수를 입력받고
        `"당신은 영어 과목에서 92점을 받았습니다."` 형식으로 출력하기
```python
subject = input("과목명: ")
score = input("점수: ")
print(f"당신은 {subject} 과목에서 {score}점을 받았습니다.")
```

- **BMI 계산기 만들기**
    - 사용자에게 **키(cm)**와 **몸무게(kg)**를 입력받고, BMI를 계산하여 `"당신의 BMI는 ___입니다."`를 출력하기
        
    > BMI 계산식:BMI=체중(kg)/(키(m))^2

```python
height = input("키(cm): ")
weight = input("몸무게(kg): ")
bmi = weight/((height/100)**2)
print(f"당신의 BMI는 {round(bmi,2)}입니다.")
```

- **시간 변환기 만들기 1**
    - 분(minute)을 입력받고, 시(hour)와 분으로 변환하여 출력하기
    - 예: `135분` → `2시간 15분입니다.`

```python
min = int(input("분(minute): "))
hour = min//60
minute = min%60
print(f"{hour}시간 {minute}분입니다.")
```

- **시간 변환기 만들기 2**
    - 초(second)를 입력받아 시간:분:초 형식으로 변환하기
    - 예: `1시간 1분 1초입니다.`

```python
sec = int(input("초(second): "))
hour = sec // 3600
minute = (sec % 3600) // 60
second = sec % 60
print(f"{hour}시간 {minute}분 {second}초입니다.")
```

- 사용자에게 세 과목 점수를 입력받고 평균을 출력하기
    - `평균 점수는 86.7점입니다.` 형식으로 출력하기
    
```python
score1 = int(input("첫 번째 과목 점수: "))
score2 = int(input("두 번째 과목 점수: "))
score3 = int(input("세 번째 과목 점수: "))
average = (score1+score2+score3)/3
print(f"평균 점수는 {round(average, 1)}점입니다.")
```
