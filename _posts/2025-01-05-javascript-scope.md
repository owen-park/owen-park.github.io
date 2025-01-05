---
title: Javascript - 스코프
description: >-
  전역, 지역 스코프
author: owen
date: 2025-01-05 18:17:00 +0900
categories: [Javascript, Basic]
tags: [javascript, scope]
sitemap: 
    changefreq : daily
---

## Javascript 스코프
- 변수나 함수에 접근하거나 호출할 수 있는 범위
- 전역 스코프 : 전체 영역에서 접근 가능
- 지역 스코프 : 특정 영역에서만 접근 가능

```javascript
let b = 1; // 전역 스코프

function funcA() {
    let a = 1; // 지역 스코프
}
console.log(a); // 접근할 수 없음
console.log(b); // 접근할 수 있음
```