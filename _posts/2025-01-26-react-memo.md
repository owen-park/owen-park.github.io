---
title: React - React.memo & useCallback
description: >-

author: owen
date: 2025-01-26 12:58:00 +0900
categories: [React, Basic]
tags: [react, memo]
sitemap: 
  changefreq : daily
---

## React.memo란?
- 컴포넌트를 인수로 받아, 최적화된 컴포넌트로 만들어 반환

  ```javascript
  const memoizedComponent = memo(component)
  ```

- 최적화된 컴포넌트는 Props를 기준으로 메모이제이션 됨
- 부모 컴포넌트에서 리렌더링되어도 메모이제이션된 자식 컴포넌트는 리렌더링되지 않음(Props의 값이 변경되면 리렌더링됨)

## useCallback 이란?
- React.memo를 사용하여 컴포넌트를 메모이제이션해도 props 중 함수는 리렌더링될때마다 주소값이 바뀌기 때문에 useCallback을 사용하여 메모이제이션함

## 소스코드 예시 
- 아래 예시처럼 간단한 컴포넌트에는 보통 메모이제이션을 하지 않음 (아래는 이해를 위함)
- title props의 값이 변경되지 않으면 해당 컴포넌트는 다시 호출되지 않음
- onClickButton props는 부모가 리렌더링될때마다 매번 다른 주소값을 가지기 때문에 다시 자식 컴포넌트를 호출시켜버림
- src/App.jsx

  ```javascript
  import Header from "./components/Header";

  function App() {
    // 함수를 메모이제이션함
    const onClickButton = useCallback(() => {}, []);
    
    return (
      <div>
        <Header
          title="hello"
          onClickButton={onClickButton}
        />
      </div>
    );
  }
  ```

- src/components/Header.jsx
  
  ```javascript
  import { memo } from "react";

  const Header = (title, onClickButton) => {
    return (
      <div className="Header">
        <h1>{title}</h1>
        <button onClick={onClickButton}>
      </div>
    );
  };

  export default memo(Header);
  ```

## 최적화는 언제? 어떤 것을?
- 보통 프로젝트가 완성된 후 최적화를 진행
- 꼭 최적화가 필요할 것 같은 연산, 함수, 컴포넌트들