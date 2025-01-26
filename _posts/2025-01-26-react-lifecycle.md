---
title: React - 라이프사이클 & useEffect
description: >-

author: owen
date: 2025-01-26 09:31:00 +0900
categories: [React, Basic]
tags: [react, lifecycle, useEffect]
sitemap: 
  changefreq : daily
---

## React 라이프사이클
- 리액트 컴포넌트의 라이프사이클
  1. Mount (탄생)
     - 컴포넌트가 탄생하는 순간
     - 화면에 처음 렌더링 되는 순간
     - "A 컴포넌트가 마운트트 되었다" => A 컴포넌트가 화면에 처음으로 렌더링 되었다
  2. Update (변화)
     - 컴포넌트가 다시 렌더링 되는 순간
     - 리렌더링 될 때를 의미
     - "A 컴포넌트가 업데이트 되었다" => A 컴포넌트가 리렌더링 되었다
  3. UnMount (죽음)
     - 컴포넌트가 화면에서 사라지는 순간
     - 렌더링에서 제외 되는 순간을 의미
     - "A 컴포넌트가 언마운트트 되었다" => A 컴포넌트가 화면에서 사라졌다

## React useEffect
- 리액트 컴포넌트의 사이드 이펙트를 제어하는 React Hook
- 사이드 이펙트 : 컴포넌트의 동작에 따라 파생되는 여러 효과 (값 변경, 라이프사이클 제어)
  - 컴포넌트 내부의 값 변경 -> 콘솔에 변경된 값 출력
  - 컴포넌트 마운트 -> 콘솔에 "Mount" 출력
  - 컴포넌트 업데이트 -> 콘솔에 "Update" 출력
  - 컴포넌트 언마운트 -> 콘솔에 "Unmount" 출력
- 소스코드
  - src/App.jsx

    ```javascript
    import "./App.css";
    import { useState, useEffect } from "react";

    function App() {
      const [count, setCount] = useState(0);
      const [input, setInput] = useState("");
      const isMount = useRef(false);

      useEffect(() => {
        console.log(`count: ${count} / input: ${input}`);
      }, [count, input]);
      // 의존성 배열
      // dependency array
      // deps

      // 1. 마운트 : 탄생
      useEffect(() => {
        console.log("mount");
      }, []);

      // 2. 업데이트 : 변화
      useEffect(() => {
        if(!isMount.current) {
          isMount.current = true;
          return;
        }
        console.log("update");
      }, []);

      const onClickButton = (value) => {
        setCount(count + value);
        console.log(count); // 변경되기 이전의 값이 출력됨(setCount는 비동기로 동작하기 때문에 setCount 호출 -> console.log(count) 실행 -> setCount 완료 순임)
      };

      return (
        <div>
          <div>현재 카운트 : </div>
          <h1>
            {count % 2 === 0 ? <Even /> : null}
          </h1>
          <button 
            onClick={() => {
              onClickButton(-1);
            }} 
          >
            -1
          </button>
          <button 
            onClick={() => {
              onClickButton(1);
            }} 
          >
            +1
          </button>
        </div>
      );
    }
    ```

  - src/components/Even.jsx

    ```javascript
    import { useEffect } from "react";

    const Even = () => {
      // 3. 언마운트 : 죽음
      useEffect(() => {
        // 클린업, 정리함수
        return () => {};
      }, []);

      return <div>짝수</div>;
    };

    export default Even;
    ```