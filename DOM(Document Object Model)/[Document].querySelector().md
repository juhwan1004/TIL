# Document.querySelector()

> document 내의 첫 번째 element를 반환합니다. 

## Syntax

`element = document.querySelector(selectors);`

일치하는 것을 찾지 못하면 null을 반환합니다. 

querySelector의 문자열 인자는 반드시 css 선택자 형식을 따라야 합니다.

## e.g.

## `var el = document.querySelector(".myclass");`

"myclass" 클래스는 사용하는 문서의 첫 번째 element를 반환

`var el = document.querySelector("div.user-panel.main input[name=login]");`

<div class="user-panel main">내에서 <input name="login" >를 사용하는 첫 element를 반환



**참고**: [MDN: Document.querySelector()](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector)

