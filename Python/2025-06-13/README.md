## 문제4

#### 배경
당신은 대규모 텍스트 데이터를 분석하는 프로젝트를 진행하고 있습니다. 텍스트 데이터에서 특정 패턴을 찾아내는 작업을 수행해야 합니다. 이번 작업에서는 중복된 문자를 제거하고 각 문자가 한 번씩만 나타나게 하는 프로그램을 작성하는 것이 목표입니다. 하지만 각 문자는 처음 등장한 순서를 유지해야 하며, 추가적으로 각 문자가 등장하는 빈도를 함께 계산해야 합니다.

#### 문제 의도
- 딕셔너리의 자료형의 이해
- 중첩된 자료형에 대한 이해

#### 요구 사항
- 함수명: remove_duplicates_and_count
- 해당 함수는 문자열의 답을 받음
- 주어진 문자열에서 중복된 문자를 제거
- 각 문자가 처음 등장한 순서를 유지
- 각 문자가 등장하는 빈도를 함께 출력하며  결과는 (문자, 빈도수) 형태의 튜플로 반환

#### 예시 코드

```python
input_string = "abracadabra123321"
def remove_duplicates_and_count(s):
    result_with_frequency = []
		'''
		여기에 코드 작성
		'''
    return result_with_frequency # 튜플 리스트로 변환
```

### 최종 코드
```python
input_string = "abracadabra123321"
def remove_duplicates_and_count(s):
    result_with_frequency = []
    remove_duplicates = []
    
    for i in str(s):
        if i not in remove_duplicates:
            remove_duplicates.append(i)
            result_with_frequency.append((i, s.count(i)))  
    return result_with_frequency

input_string = "abracadabra123321"
remove_duplicates_and_count(input_string)

# 결과값 [('a', 5), ('b', 2), ('r', 2), ('c', 1), ('d', 1), ('1', 2), ('2', 2), ('3', 2)]
```

---

## 문제 5: 이동 거리 구하기

#### 배경
축구 경기 데이터 분석가로서, 선수들의 위치 데이터를 활용하여 그들의 활동 범위와 이동 효율성을 계산하고자 합니다. 선수들의 이동 패턴을 분석하고 이를 통해 그들의 총 누적 이동 거리를 계산하여 선수의 활동량을 평가해보겠습니다.

#### 문제 의도
- 수학적 공식을 파이썬으로 구현
- 튜플 자료형의 이해
- 중첩된 자료형에 대한 이해

#### 요구 사항
- 함수명: calculate_total_distances
- 유클리드 거리 공식을 사용하여 각 위치 간 이동 거리를 계산
	- 유클리드 거리 공식
![](https://velog.velcdn.com/images/ckduswjd/post/5955c1fc-41e5-4651-8019-e9c21c49aa43/image.png)
- 각 선수별 로 경기 동안 이동 총 누적거리를 반환
- (선수 이름, 누적 거리) 의 형태의 튜플로 저장 하며 리스트로 감싸 반환. 누적 거리는 소수점 2째 자리까지 반올림

#### 예시 코드
```python
player_positions = {
    "John Doe": [(0, 0), (1, 1), (2, 2), (5, 5)],
    "Jane Smith": [(2, 2), (3, 8), (6, 8)],
    "Mike Brown": [(0, 0), (3, 4), (6, 8)]
}

def calculate_total_distances(player_positions):
	records = []
    '''
    여기에 코드를 작성하세요.
    '''
  return records
```

### 최종 코드1
```python
def calculate_total_distances(player_positions):
    records = []
    for player, positions in player_positions.items():
        total = 0.0

        for i in range(1, len(positions)):
            x1, y1 = positions[i - 1]
            x2, y2 = positions[i]
            distance = ((x1 - x2) ** 2 + (y1 - y2) ** 2) ** 0.5
            total += distance
        records.append((player, round(total, 2)))
    return records

player_positions = {
    "John Doe": [(0, 0), (1, 1), (2, 2), (5, 5)],
    "Jane Smith": [(2, 2), (3, 8), (6, 8)],
    "Mike Brown": [(0, 0), (3, 4), (6, 8)]
}
calculate_total_distances(player_positions)

# 결과값) [('John Doe', 7.07), ('Jane Smith', 9.08), ('Mike Brown', 10.0)]
```

### 최종 코드2 (math함수 사용)
```python
import math

def calculate_total_distances(player_positions):
    records = []
    for player, positions in player_positions.items():
        total = 0.0

        for i in range(1, len(positions)):
            x1, y1 = positions[i - 1]
            x2, y2 = positions[i]
            distance = math.sqrt((x1 - x2) ** 2 + (y1 - y2) ** 2)
            total += distance
        records.append((player, round(total, 2)))
    return records

player_positions = {
    "John Doe": [(0, 0), (1, 1), (2, 2), (5, 5)],
    "Jane Smith": [(2, 2), (3, 8), (6, 8)],
    "Mike Brown": [(0, 0), (3, 4), (6, 8)]
}
calculate_total_distances(player_positions)

# 결과값) [('John Doe', 7.07), ('Jane Smith', 9.08), ('Mike Brown', 10.0)]
```

---

## 문제 9: 수요일에 예약된 비행기 표 값 평균 구하기

#### 배경
특정한 날짜(Ex 수요일) 에 대한 평균 예약 금액을 조회하겠습니다. 

#### 문제 의도
- 날짜형 자료형 이해
- 불리언 인덱싱 활용
- Hint
	- 기존 날짜형 자료형을 바꿀 함수 찾기
	- Series의 dt의 함수 알아보기
- 문제의 푸는 방법은 단 1개가 아니며 여러가지가 나올 수 있음

#### 요구 사항
- 함수명: get_wed_price
- 결과 값은 소수 값 1개가 나와야합니다.
- 소수점 첫 번째 짜리까지 반올림

#### 예시 코드
```python
import pandas as pd
def get_csv(url):
	df = 	pd.read_csv('여기에 코드', sep = '여기에 코드')
	return df
df = get_csv(url) # 1번에서 불러온 df

def get_wed_price(df):
		'''
		여기에 코드
		'''
    return '여기에 코드'
```

### 최종 코드
```python
import pandas as pd

def get_csv(url):
	df = pd.read_csv(url, sep = ';')
	return df

url = 'https://raw.githubusercontent.com/llm-bot-sparta/sparta_coding/refs/heads/main/flight_data.csv'
df = get_csv(url) # 1번에서 불러온 df

def get_wed_price(df):
    df['Date_of_Journey'] = pd.to_datetime(df['Date_of_Journey'], format='%d/%m/%Y')
    Wednesday = df['Date_of_Journey'].dt.day_name() == 'Wednesday'
    Wed_avg_price = round(df[Wednesday]['Price'].mean(),1)
    return Wed_avg_price

get_wed_price(df)
```

---

## 문제 10: 출발 시간 기준 비행기 수 집계하기

#### 배경
출발 시간마다 비행기 출발의 편차가 있는지 확인해보려합니다. 요구사항에 맞춰 아침,밤,오후,저녁으로 분류하여 수를 세보세요.

#### 문제 의도
- 날짜형 자료형의 이해
- .apply 함수를 통한 기존 자료 재정의
- lambda 혹은 함수를 DataFrame에 적용하기

#### 요구 사항
- 함수명: get_cat
- Dep_Time 컬럼 기준 아침(5시 이상 12시 미만), 오후(12시 이상 18시 미만), 저녁(18시 이상 24시 미만), 그 외시간 밤
- Airline 수 기준으로 내림차순 정렬 해주세요.
- 최종 결과물은 예시 결과와 같이 reset_index() 를 적용해주세요.

#### 예시 코드
```python
import pandas as pd
def get_csv(url):
	df = 	pd.read_csv('여기에 코드', sep = '여기에 코드')
	return df
df = get_csv(url) # 1번에서 불러온 df

def get_cat(df):
		'''
		여기에 코드
		'''
    return '여기에 코드'
get_cat(df)
```

### 최종 코드
```python
import pandas as pd

def get_csv(url):
    df = pd.read_csv(url, sep=';')
    return df

def get_cat(df):
    df['Dep_Time_dt'] = pd.to_datetime(df['Dep_Time'], format='%H:%M')
    df['hour'] = df['Dep_Time_dt'].dt.hour
    def time_category(hour):
        if 5 <= hour < 12:
            return '아침'
        elif 12 <= hour < 18:
            return '오후'
        elif 18 <= hour < 24:
            return '저녁'
        else:
            return '밤'

    df['Time_Of_Day'] = df['hour'].apply(time_category)
    group = df.groupby('Time_Of_Day')['Airline'].count().sort_values(ascending=False)
    result = group.reset_index()
    return result

get_cat(df)
```
