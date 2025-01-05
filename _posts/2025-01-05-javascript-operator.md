---
title: Javascript - 연산자
description: >-
  대입, 산술, 복합대입, 증감, 논리, 비교, null병합, typeof, 삼항 연산자
author: owen
date: 2025-01-05 16:00:00 +0900
categories: [Javascript, Basic]
tags: [javascript, operator]
sitemap: 
    changefreq : daily
---

## Javascript 연산자
1. 대입 연산자
    ```javascript
    let var1 = 1;
    ```

2. 산술 연산자
   ```javascript
   let num1 = 3 + 2;
   let num2 = 3 - 2;
   let num3 = 3 * 2;
   let num4 = 3 / 2;
   let num5 = 3 % 2;
   ```

3. 복합 대입 연산자
   ```javascript
   let num6 = 10;
   num6 += 20;
   num6 -= 20;
   num6 *= 20;
   num6 /= 20;
   num6 %= 20;
   ```

4. 증감 연산자
   ```javascript
   let num7 = 10;
   ++num7;
   num7++;
   ```

5. 논리 연산자
   ```javascript
   let or = true || false;
   let and = true && false;
   let not = !true;
   ```

6. 비교 연산자
   ```javascript
   let comp1 = 1 === "1"; // false
   let comp2 = 1 !== 2; // true
   let comp3 = 2 > 1; // true
   let comp4 = 2 <= 2; // true
   ```

7. null 병합 연산자
   - 존재하는 값을 추려내는 기능
   - null, undefined가 아닌 값을 찾아내는 연산자자
   ```javascript
   let var1;
   let var2 = 10;
   let var3 = 20;

   let var4 = var1 ?? var2; // 10
   let var5 = var1 ?? var3; // 20
   let var6 = var2 ?? var3; // 10 (먼저 오는 값을 반환)
   ```

8. typeof 연산자
   - 값의 타입을 문자열로 반환하는 기능을 하는 연산자
    ```javascript
    let var7 = 1;
    let t1 = typeof var7; // number
    ```

9. 삼항 연산자
   - 항을 3개 사용하는 연산자
   - 조건식을 이용해서 참, 거짓일 때의 값을 다르게 반환
    ```javascript
    let var8 = 10;
    let res = var8 % 2 === 0 ? "짝수" : "홀수";
    ```