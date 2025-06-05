## 참고
> SQL (선언형 언어) → `if/else` 대신 ‘case when’을 사용하는 것이 좋은 이유
- CASE WHEN은 ANSI SQL 표준에 포함되어 있으며, 거의 모든 DBMS에서 동일한 문법으로 작동
- IF...ELSE는 MySQL이나 PL/pgSQL (PostgreSQL의 프로시저 언어) 등 특정 상황에서만 사용 가능

> Python (절차형 언어) → if/else가 명확하고 직관적 (삼항 연산자로 한 줄 표현도 가능)

---

## SQL

### 문제 5: 자동차 종류 별 특정 옵션이 포함된 자동차 수 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/151137

- CAR_RENTAL_COMPANY_CAR 테이블에서 '통풍시트', '열선시트', '가죽시트' 중 하나 이상의 옵션이 포함된 자동차가 자동차 종류 별로 몇 대인지 출력하는 SQL문을 작성
- 이때 자동차 수에 대한 컬럼명은 CARS로 지정
- 결과는 자동차 종류를 기준으로 오름차순 정렬

#### 코드:
```sql
SELECT CAR_TYPE, COUNT(*) CARS
FROM CAR_RENTAL_COMPANY_CAR
WHERE OPTIONS LIKE '%통풍시트%'
    OR OPTIONS LIKE '%열선시트%'
    OR OPTIONS LIKE '%가죽시트%'
GROUP BY CAR_TYPE
ORDER BY 1
```

> `OPTIONS`는 쉼표로 구분된 문자열이므로, `IN` 절(`IN (...)`)을 사용할 수 없음
>  - SQL에서는 `OPTIONS IN ('통풍시트', ...)`와 같이 비교하면 문자열 전체가 정확히 일치해야 하므로 이 문제에서는 부적절함
> 
> 각 옵션 키워드가 문자열 안에 포함되어 있는지 확인하려면 `LIKE '%옵션%'`을 사용
>  - 다중 조건 문자열 필터링에는 `LIKE ... OR LIKE ...` 또는 `REGEXP` 사용이 일반적

---

## Python

### VS Code 세팅 순서
1. 바탕화면에 `python_basic` 이란 폴더 생성
2. VS Code 열고 폴더 연결 후 `day1.py` 라는 이름의 파일 생성
3. 새 터미널 열고 `python day1.py` 입력

### VS Code 기본 기능
- 파일 열기, 터미널 열기 (`Ctrl + ~`)
- `.py` 파일 만들기
- 저장 (`Ctrl + S`)
- 코드 출력 원하지 않으면, 드래그 후 `Ctrl+/` 누르면 한 줄 주석으로 변경됨

### 출력 함수와 입력 함수
- 출력 함수 : `print()`
- 입력 함수 : `input()`
> input에서 받은 값은 문자형 → 숫자형으로 바꾸려면 `int()` 사용

### f-string
`print(f"{name}님의 나이는 {age}살입니다.")`

> `print(name + "님의 나이는 " + age + "살입니다.")`을 사용하려면, `name`과 `age`의 데이터 타입이 동일해야 됨
> 
>→ 데이터 타입이 다를 경우, `f-stirng` 사용 (더 유용)

### 문제) 시간 변환기 만들기 2
- 초(second)를 입력받아 시간:분:초 형식으로 변환하기
  - 예: `1시간 1분 1초입니다.`

```python
sec = int(input("초(second): "))
hour = sec // 3600
minute = (sec % 3600) // 60
second = sec % 60
print(f"{hour}시간 {minute}분 {second}초입니다.")
```
