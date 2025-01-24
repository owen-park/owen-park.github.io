---
title: React - useRef
description: >-

author: owen
date: 2025-01-24 10:31:00 +0900
categories: [React, Basic]
tags: [react, useRef]
sitemap: 
  changefreq : daily
---

## React useRef
- 새로운 Reference 객체를 생성하는 기능
- useRef를 이용하여 특정한 DOM 요소에 접근을 하면, 불필요한 리렌더링을 피할 수 있음
  
  ```javascript
  const refObject = useRef();
  ```

- useRef VS useState
  - useRef : 어떤 경우에도 리렌더링을 유발하지 않음
  - 값이 변경되면 컴포넌트 리렌더링

- 소스코드

  ```javascript
  import { useState, useRef } from "react";

  const Register = () => {
    const [input, setInput] = useState({
      name: "",
      birth: "",
      country: "",
    });
    const inputRef = useRef(0);

    // 통합 onChange 이벤트 핸들러
    const onChange = (e) => {
      setInput({
        ...input,
        [e.target.name]: e.target.value,
      });
    };

    // onSubmit 이벤트 핸들러
    const onSubmit = () => {
      if(input.name === "") {
        // 이름을 입력하는 DOM 요소 포커스
        inputRef.current.focus();
      }
    };

    return (
      <div>
        <div>
          <input
            ref={inputRef}
            name="name"
            value={input.name}
            onChange={onChange}
          />
        </div>

        <div>
          <input
            name="birth"
            value={input.birth}
            onChange={onChange}
          />
        </div>

        <div>
          <input
            name="country"
            value={input.country}
            onChange={onChange}
          />
        </div>

        <button onClick={onSubmit}>제출</button>
      </div>
    );
  }
  ```