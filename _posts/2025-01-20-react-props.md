---
title: React - Props
description: >-

author: owen
date: 2025-01-23 21:19:00 +0900
categories: [React, Basic]
tags: [react, props]
sitemap: 
  changefreq : daily
---

## React Props
- src/App.jsx

  ```javascript
  import "./App.css";
  import Button from "./components/Button";

  function App() {
    const buttonProps = {
      text: "메일",
      color: "red",
    };

    return(
      <>
        <Button {...buttonProps} />
        <Button />
      </>
    );
  }
  ```

- src/compoments/Button.jsx

  ```javascript
  const Button = ({ text, color, children }) => {
    return(
      <button style={{ color: color }}>
        {text} - {color}
        {children}
      </button>
    );
  };

  Button.defaultProps = {
    color: "black",
  };

  export default Button;
  ```