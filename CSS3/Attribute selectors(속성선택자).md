# Attribute selectors

**[attr]**: attr이라는 이름의 속성을 가진 요소를 선택합니다.

```css
/* "lang" 속성을 가지는 모든 span 요소의 폰트 굵기를 굵게 바꿉니다. */
span[lang] {font-weight:bold;}
```

**[attr=value]**: attr이라는 이름의 속성값이 정확히 'value'인 요소를 선택합니다.

```css
/* 언어 속성값이 포르투갈어인 모든 span 요소의 색상을 녹색으로 바꿉니다. */
span[lang="pt"] {color:green;}
```

**[attr~=value]**: attr이라는 이름의 속성값이 단어로 구성되어 있으며  사이 사이에 공백이 들어가 있을 때, 그 단어 중 하나가 'value'라는 단어이면 이 요소를 선택합니다.

```css
/* 언어 속성값이 en-us인 모든 span 요소의 색상을 파란색으로 바꿉니다.  */
span[lang~="en-us"] {color: blue;}
```

**[attr|=value]**: attr이라는 속성값을 가지고 있으며, 그 속성값이 정확히 'value'이거나 'value'로 시작하면서 '-' 문자가 곧바로 뒤에 따라 붙으면 이 요소를 선택합니다. 이 선택자는 언어 서브코드가 일치하는지 확인하고자 할 때 사용할 수 있습니다.

```css
/* 간자체(zh-CN) 혹은 번자체(zh-TW) 중국어 span  요소는 모두 붉은색으로 바꿉니다. */
span[lang|="zh"] {color: red;}
```

**[attr^=value]**: attr이라는 속성값을 가지고 있으며, 접두사로 'value'값이 포함되어 있으면 이 요소를 선택합니다.

```css
/* 모든 내부 링크 요소의 배경색을 금색으로 바꿉니다. */
a[href^="#"] {background-color: gold;}
/* 클래스명이 "main"으로 시작하는 모든 span 요소의 배경색을 노란색으로 바꿉니다. */
/* span 요소의 클래스명이 만약 "banner main"이면 영향을 받지 않을 것입니다. */
span[class^="main"] {background-color: yellow;}
```

**[attr$=value]**: attr이라는 속성값을 가지고 있으며, 접미사로 'value'가 값에 포함되어 있으면 이 요소를 선택합니다.

```css
/* url이 .cn으로 끝나는 모든 링크 요소의 색상을 붉은색으로 바꿉니다. */
a[href$=".cn"] {color: red;}
```

**[attr*=value]**: attr이라는 속성값을 가지고 있으며, 값 안에 'value'라는 문자열이 적어도 하나 이상 존재한다면 이 요소를 선택합니다.

```css
/* url안에 "example"이라는 단어를 포함하고 있는 모든 링크 요소의 배경색을 회색으로 바꿉니다. */
a[href*="example"] {background-color: #CCCCCC;}
```

**[attr operator value i]**: 괄호를 닫기 전에 i(혹은 I)를 붙여주며 값의 대소문자를 구분하지 않습니다.(ASCII 범위 내 문자에 한함)

```css
/* 모든 이메일 인풋 요소의 테두리를 파란색으로 바꿉니다. */
/* 대소문자를 구분하지 않습니다. "email", "EMAIL", "eMaIL" 모두 조건을 만족합니다. */
input[type="email" i] {border-color: blue;}
```

