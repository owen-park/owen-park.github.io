---
title: React - useMemo
description: >-

author: owen
date: 2025-01-26 12:22:00 +0900
categories: [React, Basic]
tags: [react, useMemo]
sitemap: 
  changefreq : daily
---

## useMemo란?
- <U>**메모이제이션**</U> 기법을 기반으로 불필요한 연산을 최적화하는 리액트 훅
- 반복적으로 수행되는 동일한 연산을 최초 1번만 실행하고 결과값을 메모리에 저장함
- 다시 해당 연산이 필요하면 메모리에서 결과값을 가져옴

## 소스코드 예시 (AS-IS)
- Todo List에서 전체/완료/미완료 건수를 카운팅
- 리렌더링될때 불필요한 연산이 실행될 수 있음

  ```javascript
  function App() {
    const [todos, setTodos] = useState([]);

    const getAnalyzedData = () => {
      const totalCount = todos.length;
      const doneCount = todos.filter(
        (todo) => todo.isDone
      ).length;
      const notDoneCount = totalCount - doneCount;

      return {
        totalCount,
        doneCount,
        notDoneCount,
      };
    };

    // 다른 기능으로 인해 리렌더링될 때마다 해당 함수도 다시 호출됨 
    // -> todos가 길어질수록 사용된 filter가 계속 호출되므로 성능이 악화됨
    const { totalCount, doneCount, notDoneCount } = getAnalyzedData();

    return (
      <div>
        <h1>Todo List</h1>
        <div>
          <div>total: {totalCount}</div>
          <div>done: {doneCount}</div>
          <div>notDone: {notDoneCount}</div>
        </div>
      </div>
    );
  }
  ```

## 소스코드 예시 (TO-BE)
- <U>**useMemo**</U>를 사용하여 함수를 1번만 실행되도록 할 수 있음
- 의존성 배열에 변화가 생길때마다 실행시킬 수 있음

  ```javascript
  function App() {
    const [todos, setTodos] = useState([]);

    // 최초 1번 실행되고 나서 리렌더링되어도 아래 연산은 실행되지 않음
    const { totalCount, doneCount, notDoneCount } = 
      useMemo(() => {
        const totalCount = todos.length;
        const doneCount = todos.filter(
          (todo) => todo.isDone
        ).length;
        const notDoneCount = totalCount - doneCount;

        return {
          totalCount,
          doneCount,
          notDoneCount,
        }
      }, [todos]);
      // 의존성 배열 : deps
      // deps에 변화가 생길때는 해당 연산을 다시 실행할 수 있음
    };

    return (
      <div>
        <h1>Todo List</h1>
        <div>
          <div>total: {totalCount}</div>
          <div>done: {doneCount}</div>
          <div>notDone: {notDoneCount}</div>
        </div>
      </div>
    );
  }
  ```