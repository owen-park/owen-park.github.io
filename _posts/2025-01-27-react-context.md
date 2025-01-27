---
title: React - Context
description: >-

author: owen
date: 2025-01-27 14:38:00 +0900
categories: [React, Basic]
tags: [react, context]
sitemap: 
  changefreq : daily
---

## Context란?
- 컴포넌트간의 데이터를 전달하는 방법
- 기존의 Props가 가지고 있던 단점을 해결할 수 있음
- Props의 단점 : Props Drilling
  - 한 단계 자식한테만 Props를 전달할 수 있기 때문에 계속 전달 -> 전달 -> ... 해야함
  - Parent
  <br> -> Child
  <br> -> Child-Child
  <br> -> Child-Child-Child
  <br> -> ...
- Context는 <U>**Props Drilling을 해결**</U>
- Context : <U>**데이터 보관소 (객체)**</U>

## 소스코드 예시
- src/App.jsx

  ```javascript
  // 컴포넌트가 리렌더링될때마다 context를 다시 생성할 필요는 없으니 보통 외부에 생성함
  export const Context = createContext();

  function App() {
    const [title, setTitle] = useState("hello");
    
    const onClickButton1 = () => {
      console.log("버튼1 클릭");
    };

    const onClickButton2 = () => {
      console.log("버튼2 클릭");
    };

    return (
      <div>
        <Context.Provider
          value={{
            title,
            setTitle,
            onClickButton1,
            onClickButton2,
          }}
        >
          <Main />
        </Context.Provider>
      </div>
    );
  }
  ```

- src/compoents/Main.jsx

  ```javascript
  import { useContext } from "react";
  import { Context } from "../App";

  const Main = () => {
    const { title, setTitle, onClickButton1, onClickButton2 } = useContext(Context);

    return (
      <div>
        <h1>{title}</h1>
        <button onClick={onClickButton1}>
      </div>
    );
  };

  export default Main;
  ```

## Context 사용시 메모이제이션 방법
- 변화하는 값들과 변하지 않는 값들을 분리해서 Context를 생성
- 변하지 않는 Context에는 useMemo 적용
- 소스코드 예시

  ```javascript
  // 컨텍스트 분리
  export const StateContext = createContext();
  export const DispatchContext = createContext();

  function App() {
    const [title, setTitle] = useState("hello");
    
    const onClickButton1 = useCallback(() => {
      console.log("버튼1 클릭");
    }, []);

    const onClickButton2 = useCallback(() => {
      console.log("버튼2 클릭");
    }, []);

    const memoizedDispatch = useMemo(() => {
      return { onClickButton1, onClickButton2};
    }, []);

    return (
      <div>
        <StateContext.Provider value={title, setTitle}>
          <DispatchContext.Provider value={memoizedDispatch}>
            <Main />
          </DispatchContext.Provider>
        </StateContext.Provider>
      </div>
    );
  }
  ```