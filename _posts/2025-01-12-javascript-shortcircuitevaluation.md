---
title: Javascript - 단락 평가
description: >-
  
author: owen
date: 2025-01-12 10:00:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, short-circuit-evaluation]
sitemap: 
    changefreq : daily
---

## Javascript Truthy & Falsy
- 샘플
    ```javascript
    let varA = false;
    let varB = true;

    console.log(varA && varB); // varA 평가에서 끝남

    console.log(varB || varA); // varB 평가에서 끝남
    ```


- 활용 사례
    ```javascript
    function printName(person) {
        const name = person && person.name;
        console.log(name || "person의 값이 없음");
    }

    printName();
    printName({ name: "owen" });
    ```