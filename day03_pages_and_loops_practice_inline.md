# Day 3 — Deploy to GitHub Pages & Learn Python `for` Loops

> Goal: (A) Publish your HTML as a live website using **GitHub Pages**, and (B) learn Python **`for` loops** with text‑friendly examples.

---

## Part A — Publish Your Page with GitHub Pages

You already have an `index.html` (from Day 2). We’ll host it for free on GitHub Pages.

### Structure (recommended)

```
your-repo/
├─ docs/
│  └─ index.html     # home page for GitHub Pages
└─ README.md
```

> GitHub Pages can serve files from `/docs` on the `main` branch.

### Option 1: Web UI (no terminal)

1. **Create a repo** (or open an existing one) on GitHub → _Add a README_ (optional).
2. Click **Add file → Upload files**. Upload your `docs/index.html` (create the `docs` folder if needed).
3. Commit your changes with a clear message: `Add docs/index.html for Pages`.
4. Go to **Settings → Pages**:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main`
   - **Folder**: `/docs` → **Save**
5. Wait ~1–2 minutes. Refresh the Pages section to see your site URL:  
   `https://<username>.github.io/<repo-name>/`

**Troubleshooting**

- 404? Wait a minute and refresh. Ensure the folder is exactly **`/docs`** and the file is **`index.html`**.
- Text shows weird characters? Check `<meta charset="utf-8">` in your HTML `<head>`.

**Practice (Web UI)**

- Upload a **second HTML page** as `docs/about.html`, add a link from `index.html`, and visit `/about.html` on your site.
- Edit `index.html` text (e.g., change the heading), commit, and **confirm the live site updates**.
- Open the **Commits** tab and read your last commit message. What changed? Can you view the diff?

---

### Option 2: Command Line (CLI)

> Requires Git to be installed. Optional but handy: **GitHub CLI `gh`**.

```bash
# 1) Create a project folder and init Git
mkdir my-site && cd my-site
git init -b main

# 2) Create structure and a sample index.html
mkdir -p docs lessons
cat > docs/index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>My First Web Page</title>
  </head>
  <body>
    <h1>Hello! I’m Alex.</h1>
    <p>Published via GitHub Pages.</p>
  </body>
</html>
EOF

# 3) Commit
git add -A
git commit -m "Init: add docs/index.html for Pages"

# 4A) If you have GitHub CLI:
gh repo create <username>/<repo-name> --public --source=. --remote=origin --push

# 4B) If not, create an empty repo on the web, then:
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

Now enable Pages (web step, once):

1. Repo → **Settings → Pages** → **Source**: `Deploy from a branch`
2. **Branch**: `main` / **Folder**: `/docs` → **Save**
3. Visit your site URL after a short delay.

**Quick CLI loop for updates**

```bash
# Edit files...
git status
git add -A
git commit -m "Update: improve index.html content"
git push
```

**Practice (CLI)**

- Create `docs/links.html` with two external links, commit, push, and link it from `index.html`.
- Run `git log --oneline` and `git diff` after a small edit. What do you see?
- Break your HTML on purpose (remove `</body>`), push, check the site, then **fix it** and push again.

---

## Part B — Python `for` Loops (Literature‑friendly Examples)

### 1) Why loops?

Repeat actions without copy‑pasting. Great for text processing (titles, authors, quotes).

### 2) Basic `for`

```python
for item in [1, 2, 3]:
    print(item)
```

**Practice**

- Print the **square** of each number in `[1, 2, 3, 4, 5]`.
- Print a countdown from **5 to 1**, then print `"Go!"`.
- Loop through `["A", "B", "C"]` and print `"Letter: A"`…

### 3) `range()`

```python
for i in range(5):        # 0,1,2,3,4
    print(i)

for i in range(1, 6):     # 1..5
    print(i)

for i in range(0, 10, 2): # 0,2,4,6,8
    print(i)
```

**Practice**

- Use `range(2, 21, 2)` to print **even numbers** from 2 to 20.
- Compute the **sum** of numbers from 1 to 100 using a loop.
- Print a simple progress bar: `#` repeated `i` times for `i` from 1 to 5.

### 4) Looping over text (strings & lists)

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
- Given a list of names, print only those with **length ≥ 8**.
- Split `"We love reading great books"` and print words that contain `"oo"` or `"ea"`.

### 5) `enumerate()` for index + value

```python
books = ["Hamlet", "Crime and Punishment", "The Old Man and the Sea"]
for idx, title in enumerate(books, start=1):
    print(f"{idx}. {title}")
```

**Practice**

- Print numbered titles
- Ask the user for a number `n` and print the **first n** titles with numbers.
- Create a new list of strings like `"1) Hamlet"` using a loop.

### 6) Build new lists from loops

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

- Build a list of **lengths** for each title.
- Build a list of titles **without spaces** (e.g., `"DorianGray"`).
- Rewrite one of your loops as a **list comprehension**.

### 7) `break` and `continue`

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

### 8) Nested loops (light introduction)

```python
adjectives = ["great", "tragic"]
nouns = ["hero", "journey"]
for adj in adjectives:
    for n in nouns:
        print(adj, n)
```

**Practice**

- Generate **A1…C3** using `["A","B","C"]` and `[1,2,3]`.
- Make two‑word phrases from `["dark","bright"]` and `["forest","sea","sky"]`.
- Create all pairs of authors and books (two small lists) and print them.

### 9) Mini‑project — Quiz Bank with a Loop

```python
def is_correct(user_input, answers):
    ui = user_input.strip().lower()
    return ui in [a.lower() for a in answers]

questions = [
    ("Author of 'Romeo and Juliet'?", ["Shakespeare", "셰익스피어"]),
    ("Author of 'Crime and Punishment'?", ["Dostoevsky", "Dostoyevsky", "도스토옙스키"]),
    ("Author of 'The Old Man and the Sea'?", ["Hemingway", "헤밍웨이"]),
]

score = 0
for q, answers in questions:
    if is_correct(input(q + " "), answers):
        score += 1

print("Score:", score, "/", len(questions))
```

**Practice (extensions)**

- Shuffle the questions and **limit to the first 2** each run.
- After each answer, print `"Correct!"` or `"Hint: starts with H"` (customize hints).
- Track **wrong answers** in a list and print them at the end.

---

## Checklist

- [ ] My site is live at `https://<username>.github.io/<repo-name>/`
- [ ] I can push updates by running: `git add -A && git commit -m "..." && git push`
- [ ] I can loop over lists/strings and use `range()` and `enumerate()`
- [ ] I understand `break` and `continue`
- [ ] I completed the quiz‑bank looping exercise

---

## Troubleshooting

- **Pages 404** → Wait 1–2 minutes; ensure `/docs/index.html` exists and Pages settings use `main` + `/docs`.
- **Weird characters** → Add `<meta charset="utf-8">` in `<head>`.
- **Permission errors on push** → Check remote URL, login status, or set up a Personal Access Token if needed.
- **Python input errors** → Use `strip()` and `lower()` to normalize; convert numbers with `int()` before comparisons.

---

## One‑line summary

- “We published a live website with GitHub Pages and practiced Python `for` loops using book/author examples.”
