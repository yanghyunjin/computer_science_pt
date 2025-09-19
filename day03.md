# Day 3 — Python `for` Loops (Focused, v2)

> Goal: Learn Python **`for` loops** with text-friendly, literature-themed examples.

---

## 1) Why loops?

Repeat actions without copy-pasting. Great for text processing (titles, authors, quotes).

---

## 2) Basic `for`

```python
for item in [1, 2, 3]:
    print(item)
```

**Practice**

- Print the **square** of each number in `[1, 2, 3, 4, 5]`.
- Print a countdown from **5 to 1**, then print `"Go!"`.

---

## 3) `range()`

```python
for i in range(5):
    print(i)

for i in range(1, 6):
    print(i)

for i in range(0, 10, 2):
    print(i)
```

**Practice**

- Use `range(2, 21, 2)` to print **even numbers** from 2 to 20.
- Compute the **sum** of numbers from 1 to 100 using a loop.
- Print a simple progress bar: `#` repeated `i` times for `i` from 1 to 5.

#

##

###

####

#####

---

## 4) Looping over text (strings & lists)

```python
quote = "To be, or not to be."
for ch in quote:
    # Count vowels, skip spaces, etc.
    if ch.lower() in "aeiou":
        print("vowel:", ch)

authors = ["Shakespeare", "Dostoevsky", "Hemingway"]
for name in authors:
    print("Author:", name)
```

**Practice**

- Given a sentence, **count vowels** and **consonants** separately.
- Split `"We love reading great books"` and print words that contain `"oo"` or `"ea"`.

---

## 5) `enumerate()` for index + value

```python
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
for idx, title in enumerate(books, start=1):
    print(f"{idx}. {title}")
```

**Practice**

- Create a new list of strings like `"1) Hamlet"` using a loop.

---

## 6) Build new lists from loops

```python
titles = ["Hamlet", "Dorian Gray", "The Trial"]
uppercased = []
for t in titles:
    uppercased.append(t.upper())
print(uppercased)  # ['HAMLET', 'DORIAN GRAY', 'THE TRIAL']
```

> (Optional) Peek: List comprehension

```python
uppercased2 = [t.upper() for t in titles]
```

**Practice**

- Build a list of **lengths** for each title. (len(t))
- Build a list of titles **without spaces** (e.g., `"DorianGray"`). (replace(" ", ""))

---

## 7) `break` and `continue`

```python
# Find the first title containing 'and'
titles = ["War and Peace", "Hamlet", "Crime and Punishment"]
for t in titles:
    if "and" in t.lower():
        print("Found:", t)
        break  # stop after first hit

# Print all titles except those shorter than 5 chars
for t in titles:
    if len(t) < 5:
        continue  # skip short ones
    print(t)
```

**Practice**

- Find the **first** title that starts with `"The"` and stop.
- Skip all titles that contain a **space** and print the rest.
- Loop over `range(1, 21)` and print numbers, but **skip multiples of 3**.

---

## 8) Nested loops (light introduction)

```python
adjectives = ["great", "tragic"]
nouns = ["hero", "journey"]
for adj in adjectives:
    for n in nouns:
        print(adj, n)
```

**Practice**

- Generate **A1…C3** using `["A","B","C"]` and `[1,2,3]`.
- Make two-word phrases from `["dark","bright"]` and `["forest","sea","sky"]`.
- Create all pairs of authors and books (two small lists) and print them.

---

## Checklist (Python only)

- [ ] I can loop over lists/strings and use `range()` and `enumerate()`
- [ ] I understand `break` and `continue`

---

## Troubleshooting (Python only)

- **Input handling** → Use `strip()` and `lower()` to normalize text.
- **Numbers** → Convert with `int()` or `float()` before arithmetic/comparison.
- **Indentation** → Use 4 spaces per level; keep blocks aligned.
- **Non-ASCII quotes** → Avoid “smart quotes”; use plain `'` or `"`.

---

## One-line summary

- “We practiced Python `for` loops using book/author examples and built a loop-driven quiz.”
