# 필수 문제 - Python

## 문제 1: 숫자 리스트의 평균 계산하기

#### 배경
한 소매점에서 재고를 계산해야 합니다. 주어진 재고의 평균을 계산해보세요.

#### 문제 의도
- 리스트의 자료형을 이해
- 내장 함수의 활용

#### 요구 사항
- 함수명: calcuate_stock
- 해당 함수는 리스트의 전달 인자를 받음

#### 예시 코드
```python
numbers = [10, 20, 30, 40, 50]

def calculate_stock(numbers)
	'''
	여기에 코드를 작성하세요.
	'''
```

### 최종 코드
```python
numbers = [10, 20, 30, 40, 50]
def calculate_stock(numbers):
	return sum(numbers)/len(numbers)

calculate_stock(numbers)
# 출력 30.0
```

---

## 문제 2: 계산기 만들기

#### 배경
컴퓨터 과학 수업에서 학생들은 기본적인 프로그래밍 원리를 익히고, 실제 생활에 적용할 수 있는 간단한 프로그램을 만드는 연습을 합니다. 이를 간단한 형태로 변환하여 함수형으로 만들어 보겠습니다.

#### 문제 의도
- 전달 인자의 입력에 대한 이해
- 조건문에 대한 이해

#### 요구 사항
- 함수명: simple_calculator
- num1 , num2 : 숫자 입력 값
- operator : 문자열 형태의 사칙 연산자 (+, -, * , /)
- 나누려는 숫자 num2 가 0인 경우 다음 문자를 반환 “Cannot divide by zero”

#### 예시 코드
```python
def simple_calculator(num1, num2, operator):
	'''
	여기에 코드를 작성하세요.
	'''
```

### 최종 코드
```python
def simple_calculator(num1, num2, operator):
    if operator == '+':
        return num1+num2
    elif operator == '-':
        return num1-num2
    elif operator == '*':
        return num1*num2
    elif operator == '/':
        if num2 == 0:
            return "Cannot divide by zero"
        return num1/num2
        
print(simple_calculator(10, 5, '+'))  # 출력: 15
print(simple_calculator(10, 5, '-'))  # 출력: 5
print(simple_calculator(10, 5, '*'))  # 출력: 50
print(simple_calculator(10, 0, '/'))  # 출력: 'Cannot divide by zero'
```

---

## 문제 3: 가장 큰 값 구하기 ⭐

#### 배경
한 소매점에서  가장 많은 제품을 가지고 있는 상품을 찾아야 합니다. 딕셔너리 형태로 저장된 재고 현황을 전달하면 가장 많이 있는 상품과 해당 상품의 수량을 반환하세요.

#### 문제 의도
- 딕셔너리 자료형의 이해
- 딕셔너리 자료형과 내장 함수의 조합 혹은 **최대 값 찾기** 알고리즘 구현

#### 요구 사항
- 함수명: `find_top_seller`
- 해당 함수는 딕셔너리의 전달 인자를 받음

#### 예시 코드
```python
sales_data = {"apple": 50, "orange": 2, "banana" : 30}
def find_top_seller(sales_data):
	'''
	여기에 코드를 작성하세요.
	'''    
  return top_product, max_sales
```

### 최종 코드
```python
sales_data = {"apple": 50, "orange": 2, "banana" : 30}
def find_top_seller(sales_data):
    max_sales = 0
    for product in sales_data:
        if sales_data[product] > max_sales:
            max_sales = sales_data[product]
            top_product = product
            
    return top_product, max_sales

sales_data = {"apple": 50, "orange": 2, "banana" : 30}
find_top_seller(sales_data)
# 출력 ('apple', 50)
```
---

# 필수 문제 - Pandas

## 문제 6: Github에 있는 데이터 불러오기

#### 배경
Pandas의 read_csv 함수는 로컬에 저장된 자료 이외에도 인터넷에 있는 자료를 바로 불러올 수 있는 기능을 지원합니다. 또한 구분자가 쉼표(,)가 아니더라도 받아올 수 있습니다. 

#### 문제 의도
- pandas의 read_csv 함수의 이해
- ‘sep’ 전달 인자의 이해

#### 요구 사항
- 함수명: get_csv
- 다음 Github 에 대한 데이터를 pd.read_csv를 이용하여 데이터를 불러오세요
- Hint) url은 다음과 같습니다.
- https://raw.githubusercontent.com/llm-bot-sparta/sparta_coding/refs/heads/main/flight_data.csv

#### 예시 코드
```python
import pandas as pd
def get_csv(url):
	df = 	pd.read_csv('여기에 코드', sep = '여기에 코드')
	return df
```

### 최종 코드
```python
import pandas as pd
def get_csv(url):
	df = pd.read_csv(url, sep = ';')
	return df

url = 'https://raw.githubusercontent.com/llm-bot-sparta/sparta_coding/refs/heads/main/flight_data.csv'
get_csv(url)
```
![](https://velog.velcdn.com/images/ckduswjd/post/1e120c2c-5493-44cc-a3fa-35f05ef0feab/image.png)

---

## 문제 7: 결측치 확인

#### 배경
데이터를 불러 왔을 때 각 컬럼에 결측치 유무를 확인하는 것은 중요합니다. 컬럼의 결측치를 확인해보세요.

#### 문제 의도
- DataFrame의 함수를 활용

#### 요구 사항
- 함수명: get_missing
- 컬럼별 결측치 수를 예시 결과와 같이 출력

#### 예시 코드
```python
'''
각 코드가 독립적으로 실행될 수 있도록
문제 5의 get_csv 정의하고 실행
'''
import pandas as pd
def get_csv(url):
	df = 	pd.read_csv('여기에 코드', sep = '여기에 코드')
	return df
df = get_csv(url) # 1번에서 불러온 df


def get_missing(data):
	return '여기에 코드'
```

### 최종 코드
```python
import pandas as pd
df = get_csv(url) # 1번에서 불러온 df
def get_missing(data):
	return df.isnull().sum()

get_missing(df)
```
![](https://velog.velcdn.com/images/ckduswjd/post/acff26b6-75a3-4d06-b214-7318ea637fde/image.png)

---

## 문제 8: 조건에 맞는 데이터 출력하기 ⭐

#### 배경
Destination 기준으로 price에 대한 평균과 중앙 값을 동시에 구해주세요. 단, 값은 소수점 첫 번째 자리까지 표현해주세요.

#### 문제 의도
- DataFrame의 집계 함수를 사용

#### 요구 사항
- 함수명: `get_price`
- Destination 을 인덱스로, 평균과 중앙값을 컬럼으로하는 데이터프레임 반환
- 소수점 첫 번째 짜리까지 반올림
- 정렬은 필수사항 아님

#### 예시 코드
```python
'''
각 코드가 독립적으로 실행될 수 있도록
문제 5의 get_csv 정의하고 실행
'''
import pandas as pd
def get_csv(url):
	df = 	pd.read_csv('여기에 코드', sep = '여기에 코드')
	return df
df = get_csv(url) # 1번에서 불러온 df

def get_price(df):
    result = '여기에 코드'
    return result
```

### 최종 코드
```python
import pandas as pd
df = get_csv(url) # 1번에서 불러온 df
def get_price(df):
    result = round(df.groupby('Destination')['Price'].agg(['mean', 'median']),1)
    return result

get_price(df)
```
![](https://velog.velcdn.com/images/ckduswjd/post/6cc881ad-75ea-43f2-b244-5de216393100/image.png)
