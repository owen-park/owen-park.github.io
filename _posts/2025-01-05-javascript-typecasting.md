---
title: Javascript - 형 변환
description: >-
  묵시적 형 변환, 명시적 형 변환
author: owen
date: 2025-01-05 15:53:00 +0900
categories: [Javascript, Basic]
tags: [javascript, typecasting]
sitemap: 
    changefreq : daily
---

## Javascript 형 변환
1. 묵시적 형 변환 : 자바스크립트 엔진이 알아서 형 변환 하는 것
    ```javascript
    let num = 10;
    let str = "20";
    const result = num + str; // 1020
    ```

2. 명시적 형 변환 : 프로그래머 내장함수 등을 이용해서 직접 형 변환을 명시
    ```javascript
    let str1 = "10";
    let strToNum1 = Number(str);

    let str2 = "10개";
    let strToNum2 = parseInt(str2);

    let num1 = 20;
    let numToStr1 = String(num1);
    ```