---
title: Javascript - 반복문
description: >-
  for, continue, break
author: owen
date: 2025-01-05 17:51:00 +0900
categories: [Javascript, Basic]
tags: [javascript, for]
sitemap: 
    changefreq : daily
---

## Javascript 반복문
- for문

    ```javascript
    // 결과 : 1 3 5
    for (let idx = 1; idx <= 10; idx++) {
        if (idx % 2 === 0) {
            continue;
        }
        
        console.log(idx);

        if (idx >= 5) {
            break;
        }
    }
    ```