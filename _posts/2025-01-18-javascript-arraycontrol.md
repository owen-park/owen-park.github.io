---
title: Javascript - 배열 메서드
description: >-
  
author: owen
date: 2025-01-18 16:56:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, array]
sitemap: 
    changefreq : daily
---

## Javascript 배열 메서드
### 요소 조작
1. push : 배열의 맨 뒤에 새로운 요소를 추가
   
    ```javascript
    let arr1 = [1, 2, 3];
    const newLength = arr1.push(4, 5, 6, 7);
    ```

2. pop : 배열의 맨 뒤에 있는 요소를 제거하고 반환

    ```javascript
    let arr2 = [1, 2, 3];
    const popedItem = arr2.pop();
    ```

3. shift : 배열의 맨 앞에 있는 요소를 제거하고 반환

    ```javascript
    let arr3 = [1, 2, 3];
    const shiftedItem = arr3.shift();
    ```

4. unshift : 배열의 맨 앞에 새로운 요소를 추가하는 메서드

    ```javascript
    let arr4 = [1, 2, 3];
    const newLength2 = arr4.unshift(0);
    ```

5. slice : 마치 가위처럼 배열의 특정 범위를 잘라내서 새로운 배열로 반환

    ```javascript
    let arr5 = [1, 2, 3, 4, 5];
    arr5.slice(2, 5); // [3, 4, 5]
    arr5.slice(2); // [3, 4, 5]
    arr5.slice(-2); // [4, 5]
    ```

6. concat : 두개의 서로 다른 배열을 이어 붙여서 새로운 배열을 반환

    ```javascript
    let arr6 = [1, 2, 3];
    let arr7 = [4, 5];

    let concatedArr = arr6.concat(arr7); // [1, 2, 3, 4, 5]
    ```

---

### 순회와 탐색
1. forEach : 모든 요소를 순회하면서 각각의 요소에 특정 동작을 수행시키는 메서드
   
   ```javascript
    let arr1 = [1, 2, 3];

    arr1.forEach(function (item, idx, arr) {
        console.log(item); // 1, 2, 3
        console.log(idx); // 0, 1, 2
    });

    let doubledArr = [];
    arr.forEach((item) => {
        doubledArr.push(item * 2);
    });
    console.log(doubledArr); // [2, 4, 6]
    ```

2. includes : 배열에 특정 요소가 있는지 확인
   
   ```javascript
   let arr2 = [1, 2, 3];
   let isInclude = arr2.includes(1); // true
   ```

3. indexOf : 특정 요소의 인덱스(위치)를 찾아서 반환
   
   ```javascript
   let arr3 = [2, 2, 3];
   let index = arr3.indexOf(2); // 0
   let index = arr3.indexOf(20); // -1
   ```

4. findIndex
   - 특정 요소의 인덱스(위치)를 반환(콜백함수 만족)
   - indexOf 로는 객체를 찾을 수 없기 때문에 finxIndex를 이용함
   
   ```javascript
   let arr4 = [
    { name: "kim" },
    { name: "park" },
   ];

   let findIndex = arr4.findIndex(
    (item) => item.name === "park"
   ); // 1
   ```

5. find : 모든 요소를 순회하면서 콜백함수를 만족하는 요소를 찾는데 요소를 그대로 반환
   
   ```javascript
   let arr5 = [
    { name: "kim" },
    { name: "park" },
   ];

   let finded = arr5.findIndex(
    (item) => item.name === "park"
   ); // { name: "park" }
   ```

---

### 배열 변형
1. filter
   
   ```javascript
   let arr1 = [
    { name: "kim", hobby: "game" },
    { name: "park", hobby: "football" },
    { name: "choi", hobby: "game" },
   ];

   const gamePeople = arr1.filter(
    (item) => item.hobby === "game"
   ); // [{ name: "kim", hobby: "game" }, { name: "choi", hobby: "game" }]
   ```

2. map : 배열의 모든 요소를 순회하면서 각각 콜백함수를 실행하고 그 결과값들을 모아서 새로운 배열로 반환
   
   ```javascript
   let arr1 = [1, 2, 3];
   const mapResult = arr1.map((item, idx, arr) => {
     return item * 2;
   }); // [2, 4, 6];

   let arr2 = [
    { name: "kim", hobby: "game" },
    { name: "park", hobby: "football" },
    { name: "choi", hobby: "game" },
   ];
   let names = arr2.map((item) => item.name); // ["kim", "park", "choi"]
   ```

3. sort : 배열을 사전순으로 정렬
   
   ```javascript
   let arr1 = ["b", "a", "c"];
   arr1.sort(); // ["a", "b", "c"]

   let arr2 = [10, 3, 5];
   arr2. sort((a, b) => {
     // 오름차순
     if (a > b) {
        return 1; // b가 a 앞에 옴
     } else if (a < b) {
        return -1; // a가 b 앞에 옴
     } else {
        return 0; // 자리 바꾸지 않음
     }
   });
   ```

4. toSorted : 정렬된 새로운 배열을 반환
   
   ```javascript
   let arr1 = ["c", "a", "b"];
   const sorted = arr1.toSorted();

   console.log(arr1); // ["c", "a", "b"]
   console.log(sorted); // ["a", "b", "b"]
   ```

5. join : 배열의 모든 요소를 하나의 문자열로 합쳐서 반환
   
   ```javascript
   let arr1 = ["hi", "im", "owen"];
   const joined = arr1.join(" "); // "hi im owen"
   ```