---
title: React - Hooks
description: >-

author: owen
date: 2025-01-24 10:51:00 +0900
categories: [React, Basic]
tags: [react, hooks]
sitemap: 
  changefreq : daily
---

## React Hooks
- 클래스 컴포넌트의 기능을 함수 컴포넌트에서도 이용할 수 있도록 도와주는 메서드
- 2017년도 이전 React
  - Class 컴포넌트 : 모든 기능을 이용할 수 있음(State, Ref, etc...)
  - Function 컴포넌트 : UI 렌더링만 할 수 있음
- React Hooks 종류 (약 20개)
  - useState : State 기능을 낚아채오는 Hook
  - useRef : Reference 기능을 낚아채오는 Hook
  - useEffect
  - useReducer
  - ...
- 3가지 hook 관련 팁
  1. 함수 컴포넌트, 커스텀 훅 내부에서만 호출 가능
  2. 조건부로 호출될 수는 없음
  3. 나만의 훅(Custom Hook) 직접 만들 수 있음

  - src/components/HookExam.jsx
  
    ```javascript
    import { useState } from "react";
    import useInput from "./../hooks/useInput";

    const HookExam = () => {
      // 1. 내부에서만 호출 가능
      const state = useState();

      // 2. 조건부로 호출될 수 없음
      if (true) {
        const state = useState(); // 오류 발생
      }

      // 3. 커스텀 훅
      const [input, onChange] = useInput();

      return (
        <div>
          <input value={input} onChange={onChange} />
        </div>
      );
    };

    export default HookExam;
    ```

  - src/hooks/useInput.jsx

    ```javascript
    import { useState } from "react";

    // 3. use 접두사를 붙여서 함수를 생성하면 useState를 사용할 수 있음
    function useInput() {
      const [input, setInput] = useState("");

      const onChange = (e) => {
        setInput(e.target.value);
      };

      return [input, onChange];
    }

    export default useInput;
    ```