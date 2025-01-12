---
title: Javascript - Truthy & Falsy
description: >-
  
author: owen
date: 2025-01-12 09:40:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, truthy, falsy]
sitemap: 
    changefreq : daily
---

## Javascript Truthy & Falsy
- 참, 거짓을 의미하지 않는 값도, 조건문 내에서 참이나 거짓으로 평가하는 특징
- Truthy

    ```javascript
    if (123) {
        console.log("123 is true");
    }

    // Truthy 한 값
    let t1 = "hello";
    let t2 = 123;
    let t3 = [];
    let t4 = {};
    let t5 = () => {};
    ```

- Falsy
    ```javascript
    if (undefined) {
        console.log("undefined is true");
    }
    
    // Falsy 한 값
    let f1 = undefined;
    let f2 = null;
    let f3 = 0;
    let f4 = -0;
    let f5 = NaN;
    let f6 = "";
    let f7 = 0n; // 큰 숫자를 저장, 웹 개발에서는 거의 사용안함
    ```

- 활용 사례
    ```javascript
    function printName(person) {
        if (!person) { // undefined, null 일 때의 경우를 모두 판별할 수 있음
            console.log("person의 값이 없음");
            return;
        }
        console.log(person.name);
    }

    let person = { name: "owen" };
    printName(person);
    ```