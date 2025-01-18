---
title: Javascript - Date
description: >-
  
author: owen
date: 2025-01-18 17:42:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, date]
sitemap: 
    changefreq : daily
---

## Javascript Date
1. Date 객체 생성

   ```javascript
   let date1 = new Date(); // 현재
   let date2 = new Date("2025-01-18");
   let date3 = new Date("2025-01-18-10-30-50");
   let date4 = new Date(2025, 1, 18, 10, 30, 50);
   ```

2. 타임 스탬프 : 특정 시간이 "1970-01-01 00시 00분 00초"로부터 몇 ms가 지났는지를 의미하는 숫자값

   ```javascript
   let date1 = new Date();
   let ts = date.getTime();
   let date2 = new Date(ts); // date1과 동일
   ```

3. 시간 요소 추출

   ```javascript
   let year = date.getFullYear();
   let month = date.getMonth() + 1; // 0부터 시작함
   let date = date.getDate();
   let hour = date.getHours();
   let minute = date.getMinutes();
   let seconds = date.getSeconds();
   ```

4. 시간 수정

   ```javascript
   date.setFullYear(2025);
   date.setMonth(1);
   date.setDate(18);
   date.setHours(17);
   date.setMinutes(17);
   date.setSeconds(50);
   ```

5. 시간을 여러 포맷으로 출력

   ```javascript
   date.toDateString(); // Sat Jan 18 2025
   date.toLocaleString(); // 2025. 1. 18 오후 5:17:50
   ```