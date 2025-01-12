---
title: Javascript - 원시타입 VS 객체타입
description: >-
  
author: owen
date: 2025-01-12 13:10:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, datatype]
sitemap: 
    changefreq : daily
---

## Javascript 원시타입 VS 객체타입
- 원시타입과 객체타입은 값이 저장되거나 복사되는 과정이 서로 다름
- 원시타입
  - 값 자체로써 변수에 저장되고 복사됨
  - 불변값임 (메모리 값 수정 X)
- 객체타입
  - 참조값을 통해 변수에 저장되고 복사됨
  - 가변값임 (메모리 값 수정 O)
  - 주의사항 #1 : 의도치 않게 값이 수정될 수 있음
    - 얕은 복사 : 객체의 참조값을 복사함 (원본 객체가 수정될 수 있어 위험함)

    ```javascript
    let o1 = { name: "owen" };
    let o2 = o1;
    ```

    - 깊은 복사 : 새로운 객체를 생성하면서 프로퍼티만 따로 복사함 (원본 객체가 수정될 일이 없어 안전함)

    ```javascript
    let o1 = { name: "owen" };
    let o2 = { ...o1 };
    ```

  - 주의사항 #2 : 객체간의 비교는 기본적으로 참조값을 기준으로 이루어짐
    - 예시
    
    ```javascript
    let o1 = { name: "owen" };
    let o2 = o1;
    let o3 = { ...o1 };

    console.log(o1 === o2); // true
    console.log(o1 === o3); // false
    console.log(JSON.stringify(o1) === JSON.stringify(o3)); // true
    ```

    - 얕은 비교 : 참조값을 기준으로 비교

    ```javascript
    o1 === o2
    ```

     - 깊은 비교 : 객체를 문자열로 변환하여 비교 (JSON.stringify())
    
    ```javascript
    JSON.stringify(o1) === JSON.stringify(o3)
    ```

  - 주의사항 #3 : 배열과 함수도 사실 객체임