---
title: React - useReducer
description: >-

author: owen
date: 2025-01-26 11:05:00 +0900
categories: [React, Basic]
tags: [react, useReducer]
sitemap: 
  changefreq : daily
---

## useState를 사용하면?
- 컴포넌트 내부에 상태 관리 코드를 작성해야 함
- 소스코드 예시

  ```javascript
  function App() {
    const [state, setState] = useState(0);

    // useState를 선언한 내부에서만 상태 관리를 할 수 있음
    const onClickButton = () => {
      setState(state + 1);
    };
  }
  ```

## useReducer를 사용하면?
- 컴포넌트 외부에 상태 관리 코드를 분리할 수 있음
- 소스코드 예시

  ```javascript
  // 외부에서 함수로 상태를 관리할 수 있음
  // reducer : 변환기
  // -> 상태를 실제로 변환시키는 변환기 역할할
  function reducer(state, action) {
    switch(action.type) {
      case 'INCREASE': 
        return state + action.data;
      case 'DECREASE':
        return state - action.data;
      default:
        return state;
    }
  }

  function App() {
    // dispatch : 발송하다
    // -> 상태 변화가 있어야 한다는 사실을 알리는, 발송하는 함수
    const [state, dispatch] = useReducer(reducer, 0);

    const onClickPlus = () => {
      // 인수 : 상태가 어떻게 변화되길 원하는지
      // -> 액션 객체
      dispatch({
        type: "INCREASE",
        data: 1,
      });
    };

    const onClickMinus = () => {
      // 인수 : 상태가 어떻게 변화되길 원하는지
      // -> 액션 객체
      dispatch({
        type: "DECREASE",
        data: 1,
      });
    };

    return (
      <div>
        <h1>{state}</h1>
        <button onClick={onClickPlus}>+</button>
        <button onClick={onClickMinus}>-</button>
      </div>
    );
  }
  ```