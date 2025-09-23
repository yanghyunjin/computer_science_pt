# Day 3 — Python `for` Loops (Revised Practice Pack)

> Focus: Keep difficulty within what we’ve learned and add step‑by‑step hints.  
> Use this as a ready‑to‑teach handout: **starter → solution(teacher) → optional** format.

---

## 4) Looping over text (strings & lists)

### 4-A (basic): Count **vowels** only
- Goal: Count **a, e, i, o, u** in a sentence.
- Hint: `sentence.lower()`, `if ch in "aeiou":`
```python
# starter
sentence = input("Enter a sentence: ")
vowels = "aeiou"
count = 0
for ch in sentence.lower():
    if ch in vowels:
        count += 1
print("Vowel count:", count)
```

### 4-B (extend): Count vowels **and consonants** (letters only)
- Hint: `if ch.isalpha():` to ignore digits/spaces/punctuation.
```python
# solution (teacher)
sentence = input("Enter a sentence: ")
vowels = "aeiou"
v_count = 0
c_count = 0
for ch in sentence.lower():
    if ch.isalpha():
        if ch in vowels:
            v_count += 1
        else:
            c_count += 1
print("Vowels:", v_count, "Consonants:", c_count)
```

### 4-C (list loop): Print names with **length ≥ 8**
```python
# solution (teacher)
names = ["Shakespeare", "Dante", "Hemingway", "Woolf", "Dostoevsky", "Yeats"]
for name in names:
    if len(name) >= 8:
        print(name)
```

### 4-D (optional): Words containing `"oo"` or `"ea"`
```python
# solution (teacher)
text = "We love reading great books"
for word in text.split():
    w = word.lower()
    if "oo" in w or "ea" in w:
        print(word)
```

---

## 5) `enumerate()` — numbering items

### 5-A (basic): Numbered list (start at 1)
```python
# starter/solution
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
for idx, title in enumerate(books, start=1):
    print(f"{idx}. {title}")
```

### 5-B (small step): Print **first n** books
- Hint: `books[:n]` slicing.
```python
# solution (teacher)
n = int(input("How many titles? "))
for idx, title in enumerate(books[:n], start=1):
    print(f"{idx}. {title}")
```

### 5-C (optional): Build `["1) Hamlet", ...]`
```python
# solution (teacher)
numbered = []
for i, title in enumerate(books, start=1):
    numbered.append(f"{i}) {title}")
print(numbered)
```

---

## 6) Build new lists from loops

### 6-A (basic): Lengths list
```python
# starter/solution
titles = ["Hamlet", "Dorian Gray", "The Trial"]
lengths = []
for t in titles:
    lengths.append(len(t))
print(lengths)  # e.g., [6, 11, 9]
```

### 6-B (basic): Titles **without spaces**
```python
# solution (teacher)
no_spaces = []
for t in titles:
    no_spaces.append(t.replace(" ", ""))
print(no_spaces)  # ['Hamlet', 'DorianGray', 'TheTrial']
```

### 6-C (optional): List comprehensions
```python
# solution (teacher)
lengths2 = [len(t) for t in titles]
no_spaces2 = [t.replace(" ", "") for t in titles]
print(lengths2, no_spaces2)
```

---

## 7) `break` and `continue`

### 7-A (basic): First title that starts with `"The"`
```python
# solution (teacher)
titles = ["War and Peace", "The Trial", "Hamlet", "The Old Man and the Sea"]
for t in titles:
    if t.startswith("The"):
        print("Found:", t)
        break
```

### 7-B (basic): Skip titles that contain a **space**
```python
# solution (teacher)
for t in titles:
    if " " in t:
        continue
    print(t)
```

### 7-C (optional): Print 1..20, skip multiples of 3
```python
# solution (teacher)
for i in range(1, 21):
    if i % 3 == 0:
        continue
    print(i)
```

---

## 8) Nested loops (light)

### 8-A (basic): Generate A1…C3
```python
# solution (teacher)
letters = ["A", "B", "C"]
nums = [1, 2, 3]
for L in letters:
    for n in nums:
        print(f"{L}{n}")
```

### 8-B (basic): Two‑word phrases
```python
# solution (teacher)
adjs = ["dark", "bright"]
nouns = ["forest", "sea", "sky"]
for adj in adjs:
    for noun in nouns:
        print(f"{adj} {noun}")
```

### 8-C (optional): All author–book pairs
```python
# solution (teacher)
authors = ["Shakespeare", "Dostoevsky", "Hemingway"]
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
for a in authors:
    for b in books:
        print(f"{a} — {b}")
```

---

## 9) Mini‑project — Quiz Bank (gentle version)

### 9-A (basic): Two questions, **single** correct answer each
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

### 9-B (optional): Allow **multiple spellings**
```python
def is_correct_multi(user_input, answers):
    ui = user_input.strip().lower()
    return ui in [a.lower() for a in answers]

questions = [
    ("Author of 'Crime and Punishment'?", ["Dostoevsky", "Dostoyevsky", "도스토옙스키"]),
    ("Author of 'Romeo and Juliet'?", ["Shakespeare", "셰익스피어"]),
]

score = 0
for q, answers in questions:
    if is_correct_multi(input(q + " "), answers):
        print("Correct!")
        score += 1
    else:
        print("Try again next time!")
print("Score:", score, "/", len(questions))
```

---

### Teaching tips
- Slow group: give the **starter** versions and fill small blanks only.  
- Fast group: try every **optional** item.  
- Demo expected output first; it speeds up understanding dramatically.
