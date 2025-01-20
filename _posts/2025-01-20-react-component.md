---
title: React - 컴포넌트
description: >-

author: owen
date: 2025-01-20 19:04:00 +0900
categories: [React, Basic]
tags: [react, component]
sitemap: 
  changefreq : daily
---

## React 컴포넌트
- Header 컴포넌트
  - 파일경로 : src/components/Header.jsx
  - 소스코드

    ```javascript
    const Header = () => {
      return (
        <header>
          <h1>Header</h1>
        </header>
      );
    };

    export default Header;

    ```

- Main 컴포넌트
  - 파일경로 : src/components/Main.jsx
  - 소스코드

    ```javascript
    const Main = () => {
      return (
        <main>
          <h1>Hello React</h1>
        </main>
      );
    };

    export default Main;
    
    ```

- Footer 컴포넌트
  - 파일경로 : src/components/Main.jsx
  - 소스코드

    ```javascript
    const Main = () => {
      return (
        <main>
          <h1>Hello React</h1>
        </main>
      );
    };

    export default Main;
    
    ```

- App.jsx
  - 파일경로 : src/App.jsx
  - 소스코드

    ```javascript
    import './App.css';
    import './components/Header';
    import './components/Main';
    import './components/Footer';

    function App() {
      return (
        <>
          <Header />
          <Main />
          <Footer />
        </>
      );
    };

    export default App;
    
    ```