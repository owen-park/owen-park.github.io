---
title: Javascript - 배열
description: >-
  
author: owen
date: 2025-01-05 18:31:00 +0900
categories: [Javascript, Basic]
tags: [javascript, array]
sitemap: 
    changefreq : daily
---

## Javascript 배열
1. 배열 생성

   ```javascript
   let arrA = new Array(); // 배열 생성자
   let arrB = []; // 배열 리터럴 (대부분 사용)
   let arrC = [1, 2, true, "hello", undefined, () => {}];

   // 접근
   let item1 = arrC[0];
   let item2 = arrC[1];

   // 수정
   arrC[0] = "hello";
   ```