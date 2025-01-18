---
title: Javascript - 비동기
description: >-
  
author: owen
date: 2025-01-18 17:59:00 +0900
categories: [Javascript, Advanced]
tags: [javascript, Asynchronous, async, await]
sitemap: 
    changefreq : daily
---

## Javascript 비동기
### 동기 VS 비동기
- 동기 : 여러개의 작업을 순서대로 하나씩 처리하는 방식
  - 단점
    - 자바스크립트 엔진에는 쓰레드가 1개 밖에 없음
    - Task A(0.1초) --> Task B(10초) --> Task C(0.2초) : Task C는 Task B에 영향을 받음

- 비동기 : 작업을 순서대로 처리하지 않음
  - 비동기 작업들은 자바스크립트 엔진이 아닌 Web APIs에서 실행됨
  - 아래 실행시 1 -> 3 -> 2 순으로 출력됨

      ```javascript
      console.log(1);

      // 자바스크립트 엔진 : Web APIs에 setTimeout과 콜백함수를 전달 -> 다음 구문(console.log(3)) 실행
      setTimeout(() => {
         // Web APIs : 10초 후 실행함
         console.log(2);
      }, 10000);

      console.log(3);
      ```

---

### Promise
- 비동기 작업을 감싸는 객체
- 효능
  - 비동기 작업 실행
  - 비동기 작업 상태 관리
  - 비동기 작업 결과 저장
  - 비동기 작업 병렬 실행
  - 비동기 작업 다시 실행
  - 기타 등등...
- 상태 (3가지)
  1. 대기 (Pending)
  2. 성공 (Fulfilled) : Pending -> Fulfilled
  3. 실패 (Rejected) : Pending -> Rejected
- 예시
   ```javascript
   const promise = new Promise((resolve, reject) => {
      // 비동기 작업 실행하는 함수
      // executor
      setTimeout(() => {
         const num = 10;

         if (typeof num === "number") {
            // [[Prototype]]: Promise
            // [[PromiseState에]]: "fulfilled"
            // [[PromiseResult에]]: 20
            resolve(num + 10); 
         } else {
            // [[Prototype]]: Promise
            // [[PromiseState에]]: "rejected"
            // [[PromiseResult에]]: "num이 숫자가 아님"
            reject("num이 숫자가 아님");
         }


         // [[Prototype]]: Promise
         // [[PromiseState에]]: "fulfilled"
         // [[PromiseResult에]]: "result"
         resolve("result"); 
      }, 2000);

      // then 메서드
      // -> 그 후에
      promise
         .then((value) => {
         console.log(value); // 20
         })
         .catch((error) => {
            console.log(error); // "num이 숫자가 아님"
         });
   })
   ```

---

### async
- 어떤 함수를 비동기 함수로 만들어주는 키워드
- 함수가 프로미스를 반환하도록 변환해주는 메서드
- 예시
   ```javascript
   async function getData() {
      return {
         name: "owen",
         id: "owenpark",
      };
   }

   // Promise가 반환됨
   // [[Prototype]]: Promise
   // [[PromiseState]]: "fulfilled"
   // [[PromiseResult]]: Object
   //   id: "owenpark"
   //   name: "owen"
   console.log(getData());
   ```

---

### await
- async 함수 내부에서만 사용이 가능한 키워드
- 비동기 함수가 다 처리되기를 기다리는 역할
- 예시
   ```javascript
   async function getData() {
      return {
         name: "owen",
         id: "owenpark",
      };
   }

   async function printData() {
      const data = await getData();
      console.log(data);
   }

   printData(); // {name: "owen", id: "owenpark" } 결과값이 반환됨
   ```