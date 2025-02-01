---
title: Typescript - 함수
description: >-
  함수 타입 정의, 호출 시그니처, 함수 타입 호환성, 함수 오버로딩, 사용자 정의 타입 가드
author: owen
date: 2025-02-01 10:38:00 +0900
categories: [Typescript, Basic]
tags: [typescript, function]
sitemap: 
  changefreq : daily
---

## 함수 타입 정의
- 함수를 설명하는 가장 좋은 방법
- 어떤 <U>**타입**</U>의 매개변수를 받고, 어떤 <U>**타입**</U>의 결과값을 반환하는지 이야기
- 소스코드 예시
  
  ```typescript
  // 1. 반환값은 타입 추론으로 자동으로 number가 됨
  function func(a: number, b: number) {
    return a + b;
  }

  // 2. 화살표 함수의 타입을 정의하는 방법
  const add = (a: number, b: number) => a + b;

  // 3. 매개변수에 디폴트값을 주면 타입 추론으로 해당 디폴트값의 타입으로 설정됨
  function func2(name = "owen", age?: number) {
    console.log(`name : ${name}`);
    if (typeof age === "number") {
      console.log(`age : ${age}`);
    }
  }

  func2("owen", 30);
  func2("owen");

  // 4. rest 매개변수 타입 정의
  // 4-1. 배열
  function getSum1(...rest: number[]) {
    let sum = 0;
    rest.forEach((it) => (sum += it));

    return sum;
  }
  getSum1(1, 2, 3);

  // 4-2. 튜플
  function getSum2(...rest: [number, number]) {
    let sum = 0;
    rest.forEach((it) => (sum += it));

    return sum;
  }
  getSum2(1, 2);
  ```

## 함수 타입 표현식
```typescript
// 1. 타입 별칭 이용
type Operation = (a: number, b: number) => number;

const add: Operation = (a, b) => a + b;
const sub: Operation = (a, b) => a - b;
const multiply: Operation = (a, b) => a * b;
const divide: Operation = (a, b) => a / b;

// 2. 표현식만 이용
const add: (a: number, b: number) => number = (a, b) => a + b;
```

## 호출 시그니처
```typescript
type Operation = {
  (a: number, b: number): number;
  name: string;
};

const add: Operation = (a, b) => a + b;
const sub: Operation = (a, b) => a - b;
const multiply: Operation = (a, b) => a * b;
const divide: Operation = (a, b) => a / b;

add(1, 2);
console.log(add.name);
```

## 함수 타입 호환성
- 특정 함수 타입을 다른 함수 타입으로 취급해도 괜찮은가를 판단
  1. 반환값의 타입이 호환되는가
  2. 매개변수의 타입이 호환되는가
- 기준1. 반환값이 호환되는가

  ```typescript
  type A = () => number;
  type B = () => 10;

  let a: A = () => 10; // number
  let b: B = () => 10; // number 리터럴

  a = b;
  b = a; // 에러 발생
  ```

- 기준2. 매개변수가 호환되는가
  - 2-1. 매개변수의 개수가 같을 때
  
    ```typescript
    type C = (value: number) => void;
    type D = (value: 10) => void;

    let c: C = (value) => {};
    let d: D = (value) => {};

    c = d; // 에러 발생 (업캐스팅인데 왜?)
    d = c;

    type Animal = {
      name: string;
    };

    type Dog = {
      name: string;
      color: string;
    };

    let animalFunc = (animal: Animal) => {
      console.log(animal.name);
    }

    let dogFunc = (dog: Dog) => {
      console.log(dog.name);
      console.log(dog.color);
    }

    // 에러 발생
    // color 프로퍼티가 없기 때문에 함수 매개변수의 경우에는 업캐스팅이 에러가 발생하는 것임
    animalFunc = dogFunc;
    ```

  - 2-2. 매개변수의 개수가 다를 때

    ```typescript
    type Func1 = (a: number, b: number) => void;
    type Func2 = (a: number) => void;

    let func1: Func1 = (a, b) => {};
    let func2: Func2 = (a) => {};

    func1 = func2;
    func2 = func1; // 에러 발생
    ```

## 함수 오버로딩
- 함수를 매개변수의 개수나 타입에 따라 여러가지 버전으로 정의하는 방법
- 소스코드 예시

  ```typescript
  // 버전들 -> 오버로드 시그니쳐
  function func(a: number): void;
  function func(a: number, b: number, c: number): void;

  // 실제 구현부 -> 구현 시그니쳐
  // 모든 오버로드 시그니쳐가 적용될 수 있도록 구성해야함
  function func(a: number, b?: number, c?: number) {
    if(typeof b === "number" && typeof c === "number") {
      console.log(a + b + c);
    } else {
      console.log(a * 20);
    }
  }

  func(1); // 20
  func(1, 2, 3); // 6
  ```

## 사용자 정의 타입 가드
```typescript
type Dog = {
  name: string;
  isBark: boolean;
};

type Cat = {
  name: string;
  isScratch: boolean;
};

type Aniaml = Dog | Cat;

// 반환값이 true 이면, Dog 타입이라고 말해줌 (animal is Dog)
function isDog(animal: Animal): animal is Dog {
  return (animal as Dog) animal.isBark !== undefined;
}

// 반환값이 true 이면, Cat 타입이라고 말해줌 (animal is Cat)
function isCat(animal: Animal): animal is Cat {
  return (animal as Cat) animal.isScratch !== undefined;
}

function warning(animal: Animal) {
  if (isDog(animal)) {
    animal;
  } else if (isCat(animal)) {
    animal;
  }
}
```