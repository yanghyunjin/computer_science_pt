# Node 설치 → Vite + React Todo 앱 → GitHub → Vercel 배포 가이드

이 문서는 **처음부터 배포까지 한 번에** 해보는 실습용 가이드입니다.

---

## 0. 준비 사항

- 크롬 브라우저
- GitHub 계정
- Vercel 계정 (GitHub로 로그인 가능)

---

## 1. Node.js 설치

### 1-1. Node.js 다운로드

1. 브라우저에서 https://nodejs.org 접속
2. **LTS (Recommended)** 버튼 클릭
   - Current 말고 **LTS 버전** 설치 권장

### 1-2. 설치 진행

- 다운로드한 설치 파일 실행
- `Next → Next → Install → Finish`
- 기본 옵션 그대로 진행

### 1-3. 설치 확인

터미널에서:

```
node -v
npm -v
```

버전 번호가 나오면 정상 설치입니다.

---

## 2. Vite + React로 Todo 앱 만들기

### 2-1. Vite 프로젝트 생성

```
npm create vite@latest my-todo --template react
cd my-todo
npm install
```

개발 서버 실행:

```
npm run dev
```

브라우저에서 Vite 기본 화면이 뜨면 성공.

---

### 2-2. Todo 앱 기본 코드 작성

`src/App.jsx` 전체 코드:

```jsx
import { useState } from "react";

function App() {
  const [text, setText] = useState("");
  const [todos, setTodos] = useState([]);

  const addTodo = () => {
    const trimmed = text.trim();
    if (!trimmed) return;
    setTodos([
      ...todos,
      {
        id: Date.now(),
        text: trimmed,
        done: false,
      },
    ]);
    setText("");
  };

  const toggleTodo = (id) => {
    setTodos(todos.map((t) => (t.id === id ? { ...t, done: !t.done } : t)));
  };

  const removeTodo = (id) => {
    setTodos(todos.filter((t) => t.id !== id));
  };

  const handleKeyDown = (e) => {
    if (e.key === "Enter") addTodo();
  };

  return (
    <div
      style={{
        minHeight: "100vh",
        maxWidth: 480,
        margin: "0 auto",
        padding: "24px 16px",
        fontFamily: "system-ui, -apple-system, BlinkMacSystemFont",
      }}
    >
      <h1 style={{ fontSize: 24, marginBottom: 16 }}>📝 Todo List</h1>

      <div
        style={{
          display: "flex",
          gap: 8,
          marginBottom: 16,
        }}
      >
        <input
          style={{
            flex: 1,
            padding: "8px 10px",
            fontSize: 16,
            borderRadius: 8,
            border: "1px solid #ccc",
          }}
          type="text"
          placeholder="할 일을 입력하고 Enter ⏎"
          value={text}
          onChange={(e) => setText(e.target.value)}
          onKeyDown={handleKeyDown}
        />
        <button
          style={{
            padding: "8px 12px",
            fontSize: 14,
            borderRadius: 8,
            border: "none",
            backgroundColor: "#2563eb",
            color: "white",
            cursor: "pointer",
            whiteSpace: "nowrap",
          }}
          onClick={addTodo}
        >
          추가
        </button>
      </div>

      <ul
        style={{
          listStyle: "none",
          padding: 0,
          margin: 0,
          display: "flex",
          flexDirection: "column",
          gap: 8,
        }}
      >
        {todos.map((t) => (
          <li
            key={t.id}
            style={{
              display: "flex",
              alignItems: "center",
              padding: "8px 10px",
              borderRadius: 8,
              border: "1px solid #e5e7eb",
              backgroundColor: "#f9fafb",
            }}
          >
            <input
              type="checkbox"
              checked={t.done}
              onChange={() => toggleTodo(t.id)}
              style={{ marginRight: 8 }}
            />
            <span
              style={{
                flex: 1,
                fontSize: 15,
                textDecoration: t.done ? "line-through" : "none",
                color: t.done ? "#9ca3af" : "#111827",
              }}
            >
              {t.text}
            </span>
            <button
              onClick={() => removeTodo(t.id)}
              style={{
                border: "none",
                background: "transparent",
                color: "#ef4444",
                cursor: "pointer",
                fontSize: 13,
              }}
            >
              삭제
            </button>
          </li>
        ))}
      </ul>

      {todos.length === 0 && (
        <p
          style={{
            marginTop: 16,
            fontSize: 14,
            color: "#9ca3af",
          }}
        >
          아직 등록된 할 일이 없습니다.
        </p>
      )}
    </div>
  );
}

export default App;
```

---

## 3. GitHub에 올리기

프로젝트 폴더에서:

```
git init
git add .
git commit -m "Init Vite React Todo app"
```

GitHub에서 새 Repo 생성 → URL 복사 후:

```
git branch -M main
git remote add origin https://github.com/내아이디/my-todo.git
git push -u origin main
```

---

## 4. Vercel로 배포

### 4-1. 로그인

https://vercel.com → GitHub로 로그인

### 4-2. 프로젝트 가져오기

- `Add New` → `Project`
- GitHub에서 `my-todo` 선택

### 4-3. 빌드 설정

- Framework: 자동 감지 (Vite)
- Build Command: `npm run build`
- Output Directory: `dist`

### 4-4. Deploy 클릭 → 배포 완료

URL이 생성됨:  
`https://my-todo-xxxx.vercel.app`

---

## 5. 선택 과제

- localStorage에 Todo 저장
- Todo 전체 삭제 버튼
- 오늘/내일/이주일 필터 만들기
- 모바일 하단 고정 입력창 UI 만들기

---
