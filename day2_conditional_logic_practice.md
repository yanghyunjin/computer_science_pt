# Day 2 — Conditional Logic Expansion

## 1) Multiple correct answers — `if / elif / else`

```python
print("Quiz: Key years for Hunminjeongeum (Korean script)")
ans = input("Enter the year: ").strip()

if ans == "1443":
    print("Correct! (invention)")
elif ans == "1446":
    print("Correct! (publication)")
else:
    print("Close! The answers are 1443 (invention) or 1446 (publication).")
```

**Practice Problem**  
- Write a quiz using `if/elif/else` to guess Olympic host years.  
  Example: `1988 → Seoul`, `2008 → Beijing`, `2021 → Tokyo`, else `"Different host city."`

---

## 2) Manage answers with a list — use `in`

```python
valid = ["1443", "1446"]
ans = input("Enter the year: ").strip()
if ans in valid:
    print("Correct!")
else:
    print("Incorrect.")
```

**Practice Problem**  
- Create a program that checks if the entered color is in a list of favorites (`["red", "blue", "green"]`).  
  Print `"Nice choice!"` if correct, otherwise `"Not in the list."`

---

## 3) Normalize user input — `strip`, `lower`, `replace`

```python
name = input("Type 'Shakespeare' (English or Korean spelling is fine): ").strip().lower()
name = name.replace("'", "")  # remove apostrophes, etc.
if name in ["shakespeare", "셰익스피어", "쉑스피어"]:
    print("Accepted as correct!")
else:
    print("Not quite—try again.")
```

**Practice Problem**  
- Accept `"yes"`, `"Yes"`, `"YES"`, or `" y "` as the same correct answer.

---

## 4) Combine conditions with `and`, `or` (grading example)

```python
score = int(input("Score (0~100): "))
if score >= 90:
    print("A")
elif 80 <= score < 90:
    print("B")
elif 70 <= score < 80:
    print("C")
else:
    print("D or below")
```

**Practice Problem**  
- Ask for both **age** and **country**.  
  If age ≥ 20 and country is `"korea"` → print `"Adult (Korea)"`.  
  If age ≥ 20 but country is something else → print `"Adult (Abroad)"`.

---

## 5) Make it clean with a helper function

```python
def is_correct(user_input, answers):
    ui = user_input.strip().lower()
    return ui in [a.lower() for a in answers]

score = 0
if is_correct(input("1) Author of 'Romeo and Juliet'? "), ["Shakespeare", "셰익스피어"]):
    score += 1
if is_correct(input("2) Author of 'Crime and Punishment'? "), ["Dostoevsky", "Dostoyevsky", "도스토옙스키"]):
    score += 1
if is_correct(input("3) Author of 'The Old Man and the Sea'? "), ["Hemingway", "헤밍웨이"]):
    score += 1

print("Score:", score, "/ 3")
```

**Practice Problem**  
- Use the `is_correct` function to build a **Fruit Quiz**.  
  Example: Accept both English and Korean answers for apple/banana/grape.

---

## 6) Optional: Randomize the questions

```python
import random

def is_correct(user_input, answers):
    ui = user_input.strip().lower()
    return ui in [a.lower() for a in answers]

questions = [
    ("Author of 'Romeo and Juliet'?", ["Shakespeare", "셰익스피어"]),
    ("Author of 'Crime and Punishment'?", ["Dostoevsky", "Dostoyevsky", "도스토옙스키"]),
    ("Author of 'The Old Man and the Sea'?", ["Hemingway", "헤밍웨이"]),
]

random.shuffle(questions)
score = 0
for q, answers in questions:
    if is_correct(input(q + " "), answers):
        score += 1

print("Randomized quiz score:", score, "/", len(questions))
```

**Practice Problem**  
- Create a **Math Quiz** with shuffled questions.  
  Example: `[("2+2=?", ["4"]), ("5*3=?", ["15"]), ("10-7=?", ["3"])]`

---
