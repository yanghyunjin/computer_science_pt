# Day 3 — Python `for` Loops (BASIC: code shown / EXTEND & OPTIONAL: TODO-only)

---

## 4) Looping over text (strings & lists)

### 4-A (Basic): Count **vowels** only ✅

```python
sentence = input("Enter a sentence: ")
vowels = "aeiou"
count = 0
for ch in sentence.lower():
    if ch in vowels:
        count += 1
print("Vowel count:", count)
```

### 4-B (Extend): Count vowels **and consonants** (letters only) ⏳

- **Hint**: `if ch.isalpha()` 로 알파벳만 처리, `ch in "aeiou"` 이면 모음, 아니면 자음

```python
sentence = input("Enter a sentence: ")
vowels = "aeiou"
v_count = 0
c_count = 0

for ch in sentence.lower():
    # TODO: 알파벳만 고려하고 모음/자음 카운팅 분기 작성
    pass

print("Vowels:", v_count, "Consonants:", c_count)
```

### 4-C (Basic): Print names with **length ≥ 8** ✅

```python
names = ["Shakespeare", "Dante", "Hemingway", "Woolf", "Dostoevsky", "Yeats"]
for name in names:
    if len(name) >= 8:
        print(name)
```

### 4-D (Optional): Words containing `"oo"` or `"ea"` ⏳

- **Hint**: `for word in text.split():`, 소문자 비교 `w = word.lower()` 후 `"oo" in w or "ea" in w`

```python
text = "We love reading great books"

for word in text.split():
    # TODO: "oo" 또는 "ea" 포함 여부를 소문자로 검사하고, 해당 단어를 출력
    pass
```

---

## 5) `enumerate()` — numbering items

### 5-A (Basic): Numbered list (start at 1) ✅

```python
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
for idx, title in enumerate(books, start=1):
    print(f"{idx}. {title}")
```

### 5-B (Extend): Print **first n** books ⏳

- **Hint**: 입력값 `n = int(input(...))`, 슬라이싱 `books[:n]`, `enumerate(..., start=1)`

```python
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
n = int(input("How many titles? "))

# TODO: 앞에서 n개만 번호를 붙여 출력
```

### 5-C (Optional): Build `["1) Hamlet", ...]` ⏳

- **Hint**: 비어있는 리스트 `numbered = []` 에 `f"{i}) {title}"` 형식으로 `append`

```python
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
numbered = []

# TODO: enumerate(start=1)로 순회하며 "1) Hamlet" 형태의 문자열을 numbered에 추가
print(numbered)
```

---

## 6) Build new lists from loops

### 6-A (Basic): Lengths list ✅

```python
titles = ["Hamlet", "Dorian Gray", "The Trial"]
lengths = []
for t in titles:
    lengths.append(len(t))
print(lengths)  # e.g., [6, 11, 9]
```

### 6-B (Basic): Titles **without spaces** ✅

```python
titles = ["Hamlet", "Dorian Gray", "The Trial"]
no_spaces = []
for t in titles:
    no_spaces.append(t.replace(" ", ""))
print(no_spaces)  # ['Hamlet', 'DorianGray', 'TheTrial']
```

### 6-C (Optional): List comprehensions ⏳

- **Hint**: `lengths2 = [len(t) for t in titles]`, `no_spaces2 = [t.replace(" ", "") for t in titles]`

```python
titles = ["Hamlet", "Dorian Gray", "The Trial"]

# TODO: 리스트 컴프리헨션 두 줄 작성 후 출력
# print(lengths2, no_spaces2)
```

---

## 7) `break` and `continue`

### 7-A (Basic): First title that starts with `"The"` ✅

```python
titles = ["War and Peace", "The Trial", "Hamlet", "The Old Man and the Sea"]
for t in titles:
    if t.startswith("The"):
        print("Found:", t)
        break
```

### 7-B (Basic): Skip titles that contain a **space** ✅

```python
titles = ["War and Peace", "The Trial", "Hamlet", "The Old Man and the Sea"]
for t in titles:
    if " " in t:
        continue
    print(t)
```

### 7-C (Optional): Print 1..20, skip multiples of 3 ⏳

- **Hint**: `for i in range(1, 21):` → `if i % 3 == 0: continue`

```python
# TODO: 1부터 20까지 출력하되, 3의 배수는 건너뛰기
```

---

## 8) Nested loops (light)

### 8-A (Basic): Generate A1…C3 ✅

```python
letters = ["A", "B", "C"]
nums = [1, 2, 3]
for L in letters:
    for n in nums:
        print(f"{L}{n}")
```

### 8-B (Basic): Two‑word phrases ✅

```python
adjs = ["dark", "bright"]
nouns = ["forest", "sea", "sky"]
for adj in adjs:
    for noun in nouns:
        print(f"{adj} {noun}")
```

### 8-C (Optional): All author–book pairs ⏳

- **Hint**: 중첩 루프로 `<author> — <book>` 출력

```python
authors = ["Shakespeare", "Dostoevsky", "Hemingway"]
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]

# TODO: 모든 조합을 한 줄씩 출력
```

---

## 9) Mini‑project — Quiz Bank (gentle)

### 9-A (Basic): Two questions, **single** correct answer each ✅

```python
def is_correct(user_input, answer):
    return user_input.strip().lower() == answer.lower()

questions = [
    ("Author of 'Hamlet'?", "Shakespeare"),
    ("Author of 'The Old Man and the Sea'?", "Hemingway"),
]

score = 0
for q, ans in questions:
    if is_correct(input(q + " "), ans):
        print("Correct!")
        score += 1
    else:
        print("Oops!")
print("Score:", score, "/", len(questions))
```

### 9-B (Optional): Allow **multiple spellings** ⏳

- **Hint**: 입력값을 소문자/공백 정리 후, 정답 목록을 소문자로 바꿔서 포함 여부 검사

```python
def is_correct_multi(user_input, answers):
    # TODO: strip/lower 처리 후 정답 목록과 대조
    pass

questions = [
    ("Author of 'Crime and Punishment'?", ["Dostoevsky", "Dostoyevsky", "도스토옙스키"]),
    ("Author of 'Romeo and Juliet'?", ["Shakespeare", "셰익스피어"]),
]

score = 0
for q, answers in questions:
    # TODO: 정답 처리 및 점수 집계
    pass

print("Score:", score, "/", len(questions))
```

---
