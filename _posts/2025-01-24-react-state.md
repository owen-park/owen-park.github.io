---
title: React - State
description: >-

author: owen
date: 2025-01-24 10:17:00 +0900
categories: [React, Basic]
tags: [react, state]
sitemap: 
  changefreq : daily
---

## React State
- State를 갖는 React 컴포넌트
  1. State : OFF -> ON
  2. 상태변화 감지
  3. 리렌더링 (컴포넌트를 다시 렌더링)

- 소스코드
  - src/App.jsx

    ```javascript
    import "./App.css";
    import { useState } from "react";

    function App() {
      const [state, setState] = useState(0);
      let light = "OFF";

      return (
        <>
          <h1>{state}</h1>
          <button
            onClick={() => {
              setState(state + 1);
            }}
          >
          </button>

          // 리렌더링 되지 않음
          <h1>{light}</h1>
          <button
            onClick={() => {
              light = light === "ON" ? "OFF" : "ON";
            }}
          >
          </button>
        </>
      );
    }

    export default App;
    ```