# VS Code와 Python 오프라인 개발환경 만들기 가이드

이 문서는 **처음 파이썬을 배우는 사람**도 혼자서 따라 할 수 있도록 아주 쉽게 설명한 가이드입니다.
Mac과 Windows 모두 순서대로 따라 하면 **인터넷이 없어도** Python 프로그램을 실행할 수 있어요!

---

## 🍎 Mac (맥북)에서 설치하기

### 1️⃣ Python 설치하기

1. 인터넷이 될 때 [https://www.python.org/downloads/](https://www.python.org/downloads/) 로 들어가세요.  
2. ‘Download Python 3.x.x for macOS’ 버튼을 눌러 다운로드합니다.  
3. 다운로드된 **.pkg 파일**을 더블클릭해서 설치를 시작합니다.  
4. 설치 중에 “Add Python to PATH”라는 선택지가 있다면 꼭 체크해주세요. (없을 수도 있어요, 괜찮습니다.)  
5. 설치가 끝나면, Launchpad(돋보기 아이콘)에서 “터미널”을 열고 아래를 입력해보세요.
   ```bash
   python3 --version
   ```
   버전이 표시되면 성공이에요! 🎉

---

### 2️⃣ VS Code 설치하기

1. [https://code.visualstudio.com/](https://code.visualstudio.com/) 로 이동합니다.  
2. “Download for macOS”를 눌러 다운로드합니다.  
3. 다운로드가 끝나면 ‘Visual Studio Code’ 아이콘을 **응용 프로그램 폴더**로 끌어다 넣습니다.  
4. Launchpad에서 VS Code를 실행하면 처음엔 “인터넷에서 받은 앱입니다”라는 알림이 나올 수 있는데, “열기”를 눌러주세요.

---

### 3️⃣ 새 프로젝트 폴더 만들기

1. 바탕화면에서 **새 폴더**를 만들고 이름을 `python_study` 로 해요.  
2. VS Code에서 **File → Open Folder…** 를 눌러 `python_study` 폴더를 엽니다.

---

### 4️⃣ 파이썬 가상환경 만들기

> 가상환경은 ‘이 프로젝트 안에서만 쓸 파이썬 공간’을 만드는 거예요.

1. VS Code에서 상단 메뉴 → **Terminal → New Terminal** 선택.  
2. 아래 명령을 복사해서 붙여넣고 엔터!
   ```bash
   python3 -m venv .venv
   ```
   그러면 `python_study` 폴더 안에 `.venv`라는 폴더가 생깁니다.

3. 다음 명령으로 가상환경을 켜요:
   ```bash
   source .venv/bin/activate
   ```
   `(venv)`라는 표시가 터미널 왼쪽에 뜨면 성공!

---

### 5️⃣ VS Code에서 파이썬 실행 준비

1. VS Code 왼쪽의 네모 모양 아이콘(확장 프로그램)을 눌러요.  
2. **검색창에 ‘Python’** 을 입력한 후, Microsoft에서 만든 파란색 아이콘의 “Python” 확장을 설치하세요.  
3. Command Palette (⌘+Shift+P)를 열고 `Python: Select Interpreter`를 검색합니다.  
4. 목록 중에서 `.venv`로 시작하는 것을 선택하세요.

---

### 6️⃣ 첫 번째 프로그램 만들기

1. VS Code에서 새 파일을 만들고 이름을 `hello.py` 로 저장하세요.  
2. 다음 코드를 입력합니다:
   ```python
   name = input("이름을 입력하세요: ")
   print(f"안녕하세요, {name}! 파이썬에 오신 걸 환영해요!")
   ```
3. 상단의 ▶️ (Run) 버튼을 누르거나, 터미널에서 다음을 입력해요:
   ```bash
   python3 hello.py
   ```
4. 이름을 입력하면 파이썬이 인사해 줄 거예요! 👋

---

## 💻 Windows에서 설치하기

### 1️⃣ Python 설치하기

1. [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/) 로 이동.  
2. “Download Python 3.x.x” 버튼 클릭.  
3. 설치할 때 꼭 아래 두 가지를 체크해야 해요.
   - ✅ “Add Python to PATH”
   - ✅ “Install for all users”
4. 설치가 끝나면 **명령 프롬프트(CMD)** 를 열고 아래를 입력해보세요.
   ```cmd
   python --version
   ```
   버전이 나오면 설치 성공!

---

### 2️⃣ VS Code 설치하기

1. [https://code.visualstudio.com/](https://code.visualstudio.com/) 로 가서 **Download for Windows** 클릭.  
2. 설치 중 “Add to PATH”를 꼭 체크하세요.

---

### 3️⃣ 가상환경 만들기

1. 바탕화면에 `python_study` 폴더를 만듭니다.  
2. VS Code를 실행하고, **File → Open Folder** 로 `python_study` 폴더를 엽니다.
3. 상단 메뉴 → **Terminal → New Terminal** 클릭.  
4. 아래 명령어 입력:
   ```cmd
   python -m venv .venv
   ```
5. 다음으로 가상환경을 켜요:
   ```cmd
   .\.venv\Scripts\activate
   ```
   `(venv)` 표시가 나오면 성공!

---

### 4️⃣ VS Code 설정하기

1. 왼쪽 확장(네모) 아이콘 클릭 → ‘Python’ 검색 → Microsoft Python 확장 설치.  
2. `Ctrl + Shift + P` 누르고 → `Python: Select Interpreter` 입력 → `.venv` 선택.

---

### 5️⃣ 첫 프로그램 실행하기

1. `hello.py` 파일 만들기.
   ```python
   name = input("이름을 입력하세요: ")
   print(f"안녕하세요, {name}! 파이썬 공부를 시작했군요!")
   ```
2. 상단 ▶️ 실행 버튼 클릭 또는 아래 입력:
   ```cmd
   python hello.py
   ```
3. 이름을 입력하면 인사 메시지가 출력됩니다! 😊

---

## 📘 폴더 구조 예시
```
python_study/
 ├─ .venv/         ← 파이썬 가상환경 폴더
 ├─ hello.py       ← 내가 만든 첫 코드 파일
```

---

## ⚡ 자주 생기는 문제 해결하기
| 문제 | 해결 방법 |
|------|-------------|
| VS Code가 .venv를 못 찾음 | Command Palette → `Python: Select Interpreter` → `.venv` 선택 |
| Windows에서 가상환경 안 켜짐 | 관리자 권한 PowerShell에서 `Set-ExecutionPolicy RemoteSigned` 입력 |
| ‘python’이 인식 안 됨 | 재부팅하거나 PATH 추가 후 다시 시도 |

---

## 🎯 오늘 만든 것
✅ Python 설치 완료  
✅ VS Code 설치 완료  
✅ 나만의 가상환경 생성  
✅ 첫 파이썬 프로그램 실행 성공 🎉

이제 인터넷이 없어도 `hello.py` 같은 파이썬 파일을 직접 실행할 수 있습니다!

