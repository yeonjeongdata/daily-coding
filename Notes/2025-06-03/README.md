## SQL

### 참고

- DATE_FORMAT(DATETIME, '%Y-%m-%d')
> DATETIME 필드에서 **시간(hh:mm:ss)**을 제외하고 **날짜(yyyy-mm-dd)**만 출력

- IN (값1, 값2, ...)
> 지정한 여러 값 중 하나와 일치하는지 확인할 때 사용
> 가독성이 좋고 OR 조건을 간결하게 표현 가능 (값이 많을수록 IN이 훨씬 효율적)

### 문제5

#### 코드:
```sql
SELECT PRODUCT_ID, PRODUCT_NAME, PRODUCT_CD, CATEGORY, PRICE
FROM FOOD_PRODUCT
WHERE PRICE = (SELECT MAX(PRICE) FROM FOOD_PRODUCT)
```

- 서브쿼리를 사용하는 WHERE절 (단일 행 서브쿼리)
> 서브쿼리의 결과값과 일치하는 조건을 메인 쿼리에서 필터링하는 방식

---

## Python

### 문제1: x만큼 간격이 있는 n개의 숫자

https://school.programmers.co.kr/learn/courses/30/lessons/12954

#### 코드:
```python
def solution(x, n):
    answer = [i for i in range(x, x*(n+1), x)]
    return answer
```
- x가 음수일 때 range() 함수가 제대로 작동하지 않을 수 있다는 생각에 더 나은 풀이를 고민했고, 아래와 같은 코드를 작성

#### 개선된 코드:
```python
def solution(x, n):
    return [x*i for i in range(1, n+1)]
```

### 문제2: 자연수 뒤집어 배열로 만들기

https://school.programmers.co.kr/learn/courses/30/lessons/12932

#### 코드1 ( reverse() ):
```python
def solution(n):
    answer = [int(i) for i in str(n)]
    answer.reverse()
    return answer
```

#### 코드2 ( [::-1] ):
```python
def solution(n):
    answer = [int(i) for i in str(n)][::-1]
    return answer
```

* 참고
- 슬라이싱: 문자열이나 리스트에서 특정 범위를 추출할 때 사용
> 기본 형태: 문자열[시작:끝:증가폭]
> 생략 시, 증가폭 기본값 = 1 (오른쪽으로 이동)

- 역순 슬라이싱: [::-1]
> 시작과 끝을 비워두어 전체 문자열을 대상으로 함 (오른쪽에서 왼쪽으로 한 칸씩 이동)

### 문제4: 정수 제곱근 판별

https://school.programmers.co.kr/learn/courses/30/lessons/12934

#### 코드:
```python
import math

def solution(n):
    x = math.isqrt(n)
    if x * x == n:
        return (x + 1) ** 2
    else:
        return -1
```

- 참고
> import math
> 
> math.sqrt(x): 제곱근 구하기
>
> math.isqrt(n): n의 제곱근을 구하고 정수 부분을 반환

### 문제5: 정수 내림차순으로 배치하기

https://school.programmers.co.kr/learn/courses/30/lessons/12933

#### 코드:
```python
def solution(n):
    answer = int(''.join(sorted(str(n), reverse=True)))
    return answer
```

* 참고
- str(n): 정수 n을 문자열로 변환 (예: 123 → '123')
- sorted(str(n), reverse=True) : 문자열로 변환된 각 숫자를 문자 단위로 내림차순 정렬 (예: '123' → ['3', '2', '1']
- ''.join() : 정렬된 문자 리스트를 다시 하나의 문자열로 합치기 (예: ['3', '2', '1'] → '321')
- int() : 문자열을 정수형으로 변환 (예: '321' → 321)
