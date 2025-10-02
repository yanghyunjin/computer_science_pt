# Python 조건문 · 반복문 확장 & 데이터 다루기

## 1. 조건문 · 반복문 확장 

### 숫자 맞추기 게임 (while, if 활용)
```python
import random

secret = random.randint(1, 100)
guess = 0

while guess != secret:
    guess = int(input("숫자를 맞춰보세요 (1~100): "))
    if guess < secret:
        print("더 큰 수입니다!")
    elif guess > secret:
        print("더 작은 수입니다!")
    else:
        print("정답입니다!")
```
- `while` 반복문으로 계속 입력 받기
- `if` 조건문으로 크기 비교하기

#### 연습 문제
1. 사용자가 5번까지만 시도할 수 있도록 수정해보세요.  
2. 시도 횟수를 화면에 같이 출력해보세요.  

---

### 야구 숫자 맞추기 게임 (반복문 + 조건문)
```python
import random

# 1~9 사이의 숫자 4개 뽑기 (중복 없음)
numbers = random.sample(range(1, 10), 4)

print("야구 게임을 시작합니다! (1~9 사이의 서로 다른 숫자 4개)")

while True:
    guess = input("네 자리 숫자를 입력하세요: ")
    guess_list = [int(x) for x in guess]

    strike = 0
    ball = 0

    for i in range(4):
        if guess_list[i] == numbers[i]:
            strike += 1
        elif guess_list[i] in numbers:
            ball += 1

    print(f"{strike} 스트라이크, {ball} 볼")

    if strike == 4:
        print("정답입니다!")
        break
```

#### 연습 문제
1. 사용자가 `quit`를 입력하면 게임이 종료되도록 바꿔보세요.  

---

### 별찍기, 패턴 출력 (반복문 감각 키우기)
```python
for i in range(1, 6):
    print("*" * i)

# 2. 왼쪽 정렬 역삼각형
for i in range(5, 0, -1):
    print("*" * i)

# 3. 오른쪽 정렬 삼각형
for i in range(1, 6):
    print(" " * (5 - i) + "*" * i)

# 4. 오른쪽 정렬 역삼각형
for i in range(5, 0, -1):
    print(" " * (5 - i) + "*" * i)

# 5. 정삼각형 (피라미드 모양)
#     *
#    ***
#   *****
#  *******
# *********

# 6. 다이아몬드 모양
#     *
#    ***
#   *****
#  *******
# *********
#  *******
#   *****
#    ***
#     *
```
- 반복문을 활용해 패턴 출력하기

#### 연습 문제
1. 사각형(5x5) 출력해보세요.  

---

## 2. 데이터 다루기 (React와 연결고리)

### JSON 읽고 출력하기
```python
import json

data = '{"title": "영화", "rating": 9.2}'
movie = json.loads(data)

print("제목:", movie["title"])
print("평점:", movie["rating"])
```

- JSON 문자열을 파이썬 딕셔너리로 변환
- React에서 props/state로 다루는 데이터와 유사

#### 연습 문제
1. JSON 문자열을 수정해서 다른 영화 정보를 출력해보세요.  
2. `"year"` 항목을 추가해서 출력해보세요.  

---

### 리스트 안의 데이터를 필터링 (if), 집계 (for)
```python
students = [
    {"name": "Alice", "score": 87},
    {"name": "Bob", "score": 92},
    {"name": "Charlie", "score": 78}
]

# 90점 이상 학생 출력
for s in students:
    if s["score"] >= 90:
        print(s["name"], "우수 학생")

# 평균 점수 구하기
total = 0
for s in students:
    total += s["score"]

print("평균 점수:", total / len(students))
```
- React에서 `map`, `filter`를 사용하는 것과 비슷한 개념
- 데이터 필터링, 집계 연습

#### 연습 문제
1. 80점 미만 학생만 출력해보세요.  
2. 최고 점수를 가진 학생의 이름을 출력해보세요.  

---

### JSON 파일 저장과 불러오기 (응용)
```python
import json

students = [
    {"name": "Alice", "score": 87},
    {"name": "Bob", "score": 92},
    {"name": "Charlie", "score": 78}
]

# JSON 파일로 저장
with open("students.json", "w", encoding="utf-8") as f:
    json.dump(students, f, ensure_ascii=False, indent=2)

# JSON 파일 불러오기
with open("students.json", "r", encoding="utf-8") as f:
    loaded = json.load(f)

print(loaded)
```

- 파이썬 → JSON 파일 → React에서 fetch()로 불러오는 흐름  
- 실제 프로젝트 데이터와 연결되는 과정 이해 가능  

---
