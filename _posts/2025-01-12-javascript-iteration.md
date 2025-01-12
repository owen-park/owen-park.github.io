---
title: Javascript - 반복문(순회)
description: >-
  
author: owen
date: 2025-01-12 13:36:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, iteration]
sitemap: 
    changefreq : daily
---

## Javascript 반복문(순회)
- 배열, 객체에 저장된 여러개의 값에 순서대로 하나씩 접근하는 것
- 배열 순회

  ```javascript
  let arr = [1, 2, 3];
  ```

- 배열 인덱스

  ```javascript
  for(let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
  }
  ```

- for of 반복문 (배열 순회)

  ```javascript
  for (let item of arr) {
    console.log(item);
  }
  ```

- 객체 순회

  ```javascript
  let person = {
    name: "owen",
    age: 30,
    hobby: "게임",
  };
  ```

- Object.keys 사용 (객체에서 key 값들만 뽑아서 새로운 배열로 반환)

  ```javascript
  let keys = Object.keys(person);

  for (let key of keys) {
    console.log(key, person[key]);
  }
  ```

- Object.values 사용 (객체에서 value 값들만 뽑아서 새로운 배열로 반환)

  ```javascript
  let values = Object.values(person);

  for (let value of values) {
    console.log(value);
  }
  ```

- for in 반복문 (객체 순회)

  ```javascript
  for (let key in person) {
    console.log(key, person[key]);
  }
  ```