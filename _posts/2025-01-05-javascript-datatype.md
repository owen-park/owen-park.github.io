---
title: Javascript - 자료형
description: >-
  원시타입, 객체타입
author: owen
date: 2025-01-05 13:00:00 +0900
categories: [Javascript, Basic]
tags: [javascript, datatype]
---

## Javascript 자료형
1. 원시타입
   - Number
        ```javascript
        let num1 = 27;
        let num2 = 1.5;
        let num3 = -20;
        let inf = Infinity;
        let mInf = -Infinity;
        let nan = NaN; // not a number(수치연산이 실패했을 때의 결과 값으로 보통 사용)
        ```
   - String
        ```javascript
        let str1 = "hello";
        let str2 = "world";
        let str3 = str1 + str2;
        let str4 = `${str1} ${str2}~~`;
        ```
   - Boolean
        ```javascript
        let bool1 = true;
        let bool2 = false;
        ```
   - Null
        ```javascript
        let empty = null; // 아무런 값도 담겨 있지 않음(명시적으로 아무런 값이 없다고 선언)
        ```
   - Undefined
        ```javascript
        let none; // 변수를 미처 초기화하지 못했거나 존재하지 않는 값을 불러올 때 발생
        ```
2. 객체타입
   - Object
      - Array
      - Function
      - RegexExp