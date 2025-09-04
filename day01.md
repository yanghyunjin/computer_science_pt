# Day 1 — First Steps in Python (Google Colab)

> **Coding experience without installation.**  
> Today we’ll go step by step: Output/Input → Simple calculation → **Single if statement** → if/else.

---

## Today’s Goals

- Talk to the computer with `print()`
- Receive and store values with `input()` and **variables**
- Understand **type conversion** (`int`) for numeric calculations
- Learn **single if** and **if/else**
- Create your own **3-question quiz** (with score count)

---

## Preparation & Getting Started

- Google account, Chrome browser
- Go to <https://colab.research.google.com> → click **New Notebook**
- Notebook name: `day01_first_code.ipynb`
- Run: Place cursor in a cell and press **Shift+Enter**

> Tip: Colab saves automatically. Add new code cells with **+ Code**.

---

## 1. Hello, World! — Output and Input

### 1-1. Output

```python
print("Hello, World!")
```

### 1-2. Input + Variable

```python
name = input("What is your name? ")
print("Nice to meet you,", name, "! Today is your first day of coding 🎉")
```

**Concept Check**

- `print()` = computer **speaks**
- `input()` = computer **asks and receives a string**
- **Variable** = a **box** to store data

**Common Mistakes**

- Mismatched quotes → `SyntaxError`
- Always run with **Shift+Enter**

---

## 2. Calculator — Number Input and Type Conversion

### 2-1. Addition Calculator

```python
print("Simple Calculator 🧮")
a = int(input("Enter the first number: "))
b = int(input("Enter the second number: "))
print("The sum is", a + b, "!")
```

**Concept Check**

- `input()` returns a **string** → convert to number with **`int()`**
- `a + b` = numeric addition (different from string concatenation)

**Extension Mission (optional)**

- Average: `(a + b) / 2`
- Add a third number `c` and print sum/average

**Error Handling Preview (optional)**

```python
try:
    x = int(input("Enter a number: "))
    y = int(input("Another number: "))
    print("Sum:", x + y)
except ValueError:
    print("Numbers only, please 🙂")
```

---

## 3. Conditionals — **Single if → if/else**

> Today we start with **one condition only**. (Multiple answers with `elif` come tomorrow.)

### 3-1. Single if

```python
score = 95
if score >= 90:
    print("Wow! That’s an A!")
```

- Runs only if the condition is true, otherwise nothing happens
- Try changing `score = 80`

### 3-2. if + else

```python
answer = input("In what year did King Sejong create Hangul? ")
if answer == "1443":
    print("Correct! 👑")
else:
    print("Incorrect. The answer is 1443.")
```

- With else, the computer always gives a reply
- For today: **only one correct answer** (multiple → `elif` on Day 2)

---

## 4. Mini Project — My Own 3-Question Quiz (with Score)

Change the questions/answers in the template.  
(Only 1 correct answer per question, lowercase recommended)

```python
print("My Personal Quiz 🎯")
score = 0

# Q1
a1 = input("1) Who is my favorite author? ").strip().lower()
if a1 == "shakespeare":
    score += 1

# Q2
a2 = input("2) What is my favorite genre? ").strip().lower()
if a2 == "mystery":
    score += 1

# Q3
a3 = input("3) What’s a keyword from the last book I read? ").strip().lower()
if a3 == "love":
    score += 1

print("Score:", score, "/ 3")
if score == 3:
    print("Perfect! 🏆")
else:
    print("Good job! You can do even better next time 💪")
```

**Points**

- `strip()` → removes spaces, `lower()` → makes lowercase
- Only **one correct answer** today (multi-answer tomorrow)

---

## 5. Reflection

### 5-1. One-line Reflection

```python
reflection = "Today I felt _____. Next time I want to make ____."
print(reflection)
```

---

## Assignment

1. Expand the quiz to **5 questions**
2. Calculator: Receive 3 numbers, print **sum and average**
3. Add a **hint** when the answer is wrong

---

## Troubleshooting

- **SyntaxError**: check quotes/parentheses
- **NameError**: check variable spelling (case-sensitive)
- **ValueError**: happens when `int()` gets non-numeric input → enter only numbers or use `try/except`
- If stuck: **Runtime → Restart Runtime** and re-run

---
