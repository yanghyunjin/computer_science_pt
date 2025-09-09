# Day 2 — Conditional Logic Expansion & HTML Intro Page

> Part A: Expand Python conditionals (**if/elif/else**, multiple correct answers, `and`/`or`, `in`)  
> Part B: Build a **self‑intro web page** with basic HTML (plus a tiny bit of CSS)

---

## Part A. Python — Conditional Logic Expansion

### 1) Multiple correct answers — `if / elif / else`

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

### 2) Manage answers with a list — use `in`

```python
valid = ["1443", "1446"]
ans = input("Enter the year: ").strip()
if ans in valid:
    print("Correct!")
else:
    print("Incorrect.")
```

### 3) Normalize user input — preprocessing with `strip`, `lower`, `replace`

```python
name = input("Type 'Shakespeare' (English or Korean spelling is fine): ").strip().lower()
name = name.replace("'", "")  # remove apostrophes, etc.
if name in ["shakespeare", "셰익스피어", "쉑스피어"]:
    print("Accepted as correct!")
else:
    print("Not quite—try again.")
```

### 4) Combine conditions with `and`, `or` (grading example)

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

### 5) Make it clean with a helper function

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

### 6) Optional: Randomize the questions

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

---

## Part B. HTML Basics — Build a Self‑Intro Page

### 1) What is HTML?

- The language that defines the **structure/content** of a web page
- Basic skeleton: `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`

### 2) The smallest valid HTML page

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>My First Web Page</title>
  </head>
  <body>
    <h1>Hello! My name is Alex.</h1>
    <p>I’m learning Python and web development.</p>
  </body>
</html>
```

### 3) Common tags you’ll use a lot

- Headings: `<h1>` ~ `<h3>`
- Paragraph: `<p>`
- List: `<ul>`, `<li>` / Numbered list: `<ol>`, `<li>`
- Link: `<a href="https://example.com">Link text</a>`
- Image: `<img src="IMAGE_URL" alt="description">`

### 4) Add a little style — internal CSS

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>About Me</title>
    <style>
      body {
        max-width: 720px;
        margin: 40px auto;
        font-family: system-ui, -apple-system, sans-serif;
        line-height: 1.6;
      }
      .card {
        padding: 16px;
        border: 1px solid #ddd;
        border-radius: 12px;
      }
      h1 {
        margin-bottom: 8px;
      }
      a {
        text-decoration: none;
      }
    </style>
  </head>
  <body>
    <h1>Hello! I’m Alex.</h1>
    <p>I love literature and I’m currently learning Python.</p>

    <div class="card">
      <h2>Favorite Books</h2>
      <ul>
        <li>And Then There Were None — Agatha Christie</li>
        <li>Crime and Punishment — Fyodor Dostoevsky</li>
        <li>The Old Man and the Sea — Ernest Hemingway</li>
      </ul>
    </div>

    <h2>Contact</h2>
    <p>Email: <a href="mailto:me@example.com">me@example.com</a></p>

    <h2>Links</h2>
    <p>
      <a href="https://github.com/">GitHub</a> ·
      <a href="https://www.notion.so/">Notion</a>
    </p>

    <h2>Photo</h2>
    <img src="https://picsum.photos/640/360" alt="Sample image" />
  </body>
</html>
```

### 5) Hands‑on steps

1. Open Notepad/VS Code and save a file named `index.html`
2. Double‑click the file to open it in your browser
3. Replace the sample content with your own intro, links, and an image

### 6) Mini project (recommended)

- Add a section: **“About my quiz”** (describe Day 1’s quiz and include a screenshot)
- Add a list: **Top 3 favorite authors**
- Add links: school/club/hobby sites

---

## Homework

- **Python**: Expand to 5 questions; allow **multiple correct answers** (use `in`), and print a final rating (High/Medium/Low) based on the score.
- **HTML**: Finish the self‑intro page with a title/paragraph/list/link/image and a small amount of styling.

---

## Checklist

- [ ] I can use `if/elif/else` to branch logic
- [ ] I can normalize input with `strip`, `lower`, and `replace`
- [ ] I know the basic HTML structure and common tags
- [ ] I can add an image, links, and lists
- [ ] I can save an `.html` file and open it in a browser

---

## Troubleshooting

- **HTML shows as plain text**: Make sure the file extension is `.html`
- **Image not visible**: Check the `src` URL and your internet connection
- **Garbled text**: Ensure `<meta charset="utf-8">` is present
- **Python errors**: Check lowercase names, parentheses, and colons (`:`) in `if/elif/else`

---
