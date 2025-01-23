---
title: React - 이벤트 핸들링
description: >-

author: owen
date: 2025-01-23 21:40:00 +0900
categories: [React, Basic]
tags: [react, event]
sitemap: 
  changefreq : daily
---

## React 이벤트 핸들링
- 이벤트
  - 웹 내부에서 발생하는 사용자의 행동
  - EX) 버튼 클릭, 메시지 입력, 스크롤 등등
- 이벤트 핸들링
  - 이벤트가 발생했을 때 그것을 처리하는 것
  - EX) 버튼 클릭시 경고창 노출
- 소스코드
  - src/compoments/Button.jsx

    ```javascript
    const Button = ({ text, color, children }) => {
      const onClickButton = (e) => {
        console.log(e); // 이벤트 객체
        console.log(text);
      };

      return(
        <button
          onClick={onClickButton}
          style={{ color: color }}
        >
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

- 합성 이벤트
  - 모든 웹 브라우저의 이벤트 객체를 하나로 통일한 형태
    
    ```javascript
    const onClickButton = (e) => {
      console.log(e); // 이벤트 객체
    };
    ```

