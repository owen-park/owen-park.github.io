---
title: Javascript - 조건문
description: >-
  if, switch
author: owen
date: 2025-01-05 16:21:00 +0900
categories: [Javascript, Basic]
tags: [javascript, if, switch]
sitemap: 
    changefreq : daily
---

## Javascript 조건문
1. if문
   
   ```javascript
   let num = 4;
   if (num >= 10) {
    console.log("거짓");
   } else if (num >= 3) {
    console.log("참");
   } else {
    console.log("거짓");
   }
   ```

2. switch문
    ```javascript
    let animal = "cat";
    switch (animal) {
        case "cat": {
            console.log("고양이");
            break;
        }
        case "dog": {
            console.log("개");
            break;
        }
        default: {
            console.log("그런 동물 모릅니다");
        }
    }
    ```