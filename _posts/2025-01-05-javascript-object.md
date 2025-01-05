---
title: Javascript - 객체
description: >-
  
author: owen
date: 2025-01-05 18:21:00 +0900
categories: [Javascript, Basic]
tags: [javascript, object]
sitemap: 
    changefreq : daily
---

## Javascript 객체
1. 객체 생성

    ```javascript
    let obj1 = new Object(); // 객체 생성자
    let obj2 = {}; // 객체 리터럴 (대부분 사용)
    ```

2. 객체 프로퍼티 (객체 속성)

   ```javascript
   let person = {
    name: "owen",
    age: 30,
    hobby: "게임",
    sayHi() {
        console.log("안녕");
    },
   };

   // 접근
   let name = person.name;
   let age = person["age"];
   let property = "hobby";
   let hobby = person[property];
   person.sayHi();

   // 추가 / 수정
   person.job = "developer";
   person["favoriteFood"] = "짬뽕";

   // 삭제
   delete person.job;
   delete person["favoriteFood"];

   // 존재유무 확인
   let res1 = "name" in person; // true
   let res2 = "cat" in person; // false
   ```