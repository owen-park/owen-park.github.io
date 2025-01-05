---
title: Javascript - 함수
description: >-
  function
author: owen
date: 2025-01-05 17:55:00 +0900
categories: [Javascript, Basic]
tags: [javascript, function]
sitemap: 
    changefreq : daily
---

## Javascript 함수
1. 함수

    ```javascript
    let area = getArea(10, 20);

    // 호이스팅(끌어올림)
    // 함수를 밑에 선언해도 자바스크립트가 선언문을 위로 끌어 올려서 호출문에서 정상적으로 동작하게 만듦
    function getArea(width, height) {
        // 중첩 함수
        function another() {
            console.log("another");
        }

        another();

        let area = width * height;
        return area;
    }
    ```

2. 함수 표현식

    ```javascript
    // 함수 표현식은 호이스팅의 대상이 되지 않아서 선언문 다음에 호출을 해야함
    let func1 = function () {
        console.log("function");
    }
    func();
    ```

3. 화살표 함수

    ```javascript
    let func2 = (value) => {
        console.log(value);
        return value + 1;
    }
    console.log(func2(10)); // 11
    ```

4. 콜백함수

    ```javascript
    function main(value) {
        value();
    }

    function sub() {
        console.log("sub");
    }

    main(sub); // 함수가 인수로 전달됨
    ```

5. 콜백함수 활용
    - AS-IS

        ```javascript
        function repeat(count) {
            for(let idx = 1; idx <= count; idx++) {
                console.log(idx);
            }
        }

        function repeatDouble(count) {
            for(let idx = 1; idx <= count; idx++) {
                console.log(idx * 2);
            }
        }

        repeat(5);
        repeatDouble(5);
        ```

    - TO-BE
        ```javascript
        function repeat(count, callback) {
            for(let idx = 1; idx <= count; idx++) {
                callback(idx);
            }
        }

        repeat(5, (idx) => {
            console.log(idx);
        });
        repeat(5, (idx) => {
            console.log(idx * 2);
        });
        ```