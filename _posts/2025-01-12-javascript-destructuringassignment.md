---
title: Javascript - 구조 분해 할당
description: >-
  
author: owen
date: 2025-01-12 12:52:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, destructuring-assignment]
sitemap: 
    changefreq : daily
---

## Javascript 구조 분해 할당
- 각 배열 또는 객체의 원소를 각 변수에 할당
- 배열의 구조 분해 할당

    ```javascript
    let arr = [1, 2, 3];

    let [one, two, three, four = 4] = arr;
    ```

- 객체의 구조 분해 할당

    ```javascript
    let person = {
        name: "owen",
        age: 30,
        hobby: "게임",
    };

    let { 
        name, 
        age: myAge, // myAge라는 변수에 다시 할당함
        hobby,
        extra = "hello",
    } = person;

    console.log(name, myAge, hobby, extra);
    ```

- 객체의 구조 분해 할당을 이용해서 함수의 매개변수를 받는 방법

    ```javascript
    const func = ({name, age, hobby, extra}) => {
        console.log(name, age, hobby, extra);
    }

    func(person); // 객체를 넘겼을 때만 구조 분해 할당이 됨
    ```