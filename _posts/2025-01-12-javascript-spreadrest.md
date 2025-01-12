---
title: Javascript - Spread 연산자 & Rest 매개변수
description: >-
  
author: owen
date: 2025-01-12 13:00:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, spread, rest]
sitemap: 
    changefreq : daily
---

## Javascript Spread 연산자 & Rest 매개변수
- Spread 연산자
  - Spread : 흩부리다, 펼치다
  - 객체나 배열에 저장된 여러개의 값을 개별로 흩뿌려주는 역할
  - 예시

    ```javascript
    let arr1 = [1, 2, 3];
    let arr2 = [4, ...arr1, 5, 6];

    let obj1 = {
        a: 1,
        b: 2,
    };
    let obj2 = {
        ...obj1,
        c: 3,
        d: 4,
    };

    function funcA(p1, p2, p3) {
        console.log(p1, p2, p3);
    }

    funcA(...arr1);
    ```

- Rest 매개변수
  - Rest : 나머지, 나머지 매개변수
  - rest 매개변수 뒤에 추가적인 매개변수는 올 수 없음
  - 예시
    
    ```javascript
    function funcB(one, ...rest) {
        console.log(rest); // [2, 3]
    }

    funcB(...arr1);
    ```