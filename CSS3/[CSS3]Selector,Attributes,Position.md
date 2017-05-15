# FastCampus 2일차

김데레사 강사님

e-mail: seulbinim@gmail.com

github: https://github.com/seulbinim/fastCampus

추천도서: 웹디자인 2.0 고급 CSS (앤디 클락)

## **<개념 정리>**

1. **Rendering**: DOM Tree, CSSOM(CSS Object Model) Tree를 사용하여 화면에 보여준다. [참고 youtube 영상](https://www.youtube.com/watch?v=ZTnIxIA5KGw) 

2. **Web 동작 방식**[(MDN link)](https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/%EC%9B%B9%EC%9D%98_%EB%8F%99%EC%9E%91_%EB%B0%A9%EC%8B%9D) 

3. **normal flow**: 일반적인 마크업 순서(위->아래)를 의미

4. **그룹핑**: 사이트 페이지에서 연관된 컨텐츠를 덩어리 짓는 것 

5. **주석 단축키**: ctrl+/ (주석은 보통 해당코드 바로위에 작성한다.)

   ​

## **\<CSS 기본 문법>**

[참조 사이트: CSS ZEN Garden](http://www.csszengarden.com/)

- CSS는 가장 마지막 값으로 적용된다.

- ```html
  The Beauty of
  <abbr title="Cascading Style Sheets">CSS</abbr>
  Design
  ```

- 태그안에 title 속성으로 tooltip을 표시할 수 있다.

- \<abbr>태그는 축약어를 표시할 때 사용하는 Tag 

1. **선택자** 

   ```css
   body {
     margin: 0;
   }
   .wrapper {
     background-color: #1d4fe7;
   }
   ```

   - **태그 선택자(요소(element) 선택자)**: 중괄호{} 안에 '속성(attribute):값(value)'을 넣어준다.
   - 두 가지 이상의 속성을 줄 경우 세미콜론(;)으로 구분해준다.
   - 클래스(.), id(#), 태그(태그명)으로 선택가능
   - Atom colorPicker 패키지 단축키(ctrl+alt+c)

2. **기본 스타일(agent style)**: 브라우저마다 기본으로 적용되어있는 CSS

3. **Box Model**

   - width: 가로 길이 (default: auto, 내용물에 맞춰진다. 사용자 지정가능)
   - height: 세로 길이 (default: auto, 내용물에 맞춰진다. 사용자 지정가능)
   - border: 테두리 선
   - padding: 내부 여백
   - margin: 외부 여백(**투명하다.**)

4. **em**

   - 0.83em = 기본픽셀(16px, 사용자 지정가능) x 0.83 = 19px 

5. **vh(viewport height)**: 모던 브라우저(최신 브라우저)만 지원

   - 화면크기에 따른 비율을 말함

   - ```css
     .wrapper {
       background-color: #1d4fe7;
       height: 100vh; // 100% 높이
     }
     ```


-  지정숫자/화면크기 ex) 10vh -> 화면의 10%크기

   - padding과 border 추가 시 화면 크기를 넘어가게 된다. (box-sizing:border-box로 조절가능)

6. **auto margin 기법**

   - margin:0 auto;으로 가운데 정렬을 하는 기법
   - width값을 갖는 block 객체에만 auto값을 줄 수 있다.
   - margin: 0 auto에서 auto는 브라우저가 자동으로 여백을 나눈다. 

7. **선택자 그룹핑**

   - ```css
     .header, .visual, .main-content, .slogan, .footer {
       width: 940px;
       margin: 0 auto;
     }
     ```

8. **box-sizing**

   - ```css
     .main-content {
       background-color: #66a142;
       height: 60vh;
       padding: 30px;
       box-sizing: border-box;
       border: 10px dashed blue;
     }
     ```

   - box에 여백 적용시 기존의 크기를 넘지 않도록 해주는 설정

9. **Flex Box(flexible box model)**

   - flex 이해에 도움되는 [미니게임](flexboxfroggy.com)


   - 부모 요소가 display:flex; 상태에서만 적용가능한 속성


   - 지원여부 확인 사이트[css3test](http://css3test.com/), [caniuse](http://caniuse.com/), [w3c](https://www.w3.org/Style/CSS/)-> WD:실험단계 기능, LC(last call):점검 CR:권고, PR:제안(표준화될 가능성 높음), REC(표준화됨)

   ```css
   .main-content {
     background-color: #66a142;
     height: 60vh;
     padding: 30px;
     display: flex;
     justify-content: center;
   }
   .column {
     background-color: pink;
     width: 250px;
   }
   ```

   1. 부모 영역(main-content)에 display:flex; 선언.(float를 대체하는 최신 기능)
   2. 자동으로 자식(column)영역의 block 객체의 위치를 조절할 수 있다.

   - justify-content: center;는 block 박스를 가운데 정렬해주는 속성 값
   - justify-content: space-between, space-around;은 자동으로 block 간의 간격을 띄어준다.

   3. flex-direction: column; 속성을 통해 일반적인 block처럼도 사용가능(default: row(가로) 방향)

      ```css
      flex-direction: row;
      flex-direction: row-reverse;
      flex-wrap: wrap;
      flex-flow:row wrap;

      .column1{
        order:2;
      }
      .column2{
        order:1;
      }
      .column3{
        order:3;
      }
      ```

      - column = 가로축, row = 세로축 기준

      - flex-wrap: wrap; 속성 사용 시 길이가 부족하면 개행이 일어난다.

        -> nowrap이 default 속성이고 개행 없이 해당 길이에 맞도록 재조정( 100x(block길이/전체block길이\) )되어 배치(개행x).

      - flex-flow: flex 속성(flex-direction,flex-wrap)의 단축 표현

      - **order 속성**을 통해 원하는 위치에 block을 배치할 수 있다.

10. **justify / align** 정렬관련 속성

   - justify: 단일 열/행 의 경우 적용(main축(가로)/cross축(세로)기준 정렬)
   - align: 여러 열/행 의 경우 적용(main축(가로)/cross축(세로)기준 정렬)

11. **CSS 문법검사**[w3c link](https://jigsaw.w3.org/css-validator/)

   - 에러나 부분에 문제가 안보이면 디버깅을 통해 상속된 곳을 살펴 봐야한다.
   - 상속되지 않는 것: margin,padding, border 등의 box model/배치 관련 속성
   - 상속되는 것: 데코레이션 관련 속성(폰트,컬러 등)

12. **color 속성**

   - rgba(255,255,255, 0)
   - hsla()

13. **암묵적 아웃라인**: wrapping에 관계없이 heading 태그의 숫자만으로 깊이를 판단

14. **명시적 아웃라인**: 아웃라인을 그려주어 같은 숫자의 heading도 상하관계가 생김

15. **overflow 속성**

   - auto, hidden 등의 값을 가짐

16. **Link 속성**

   - 기본 속성: 밑줄, 글자색, 마우스오버 시 커서모양을 가짐

17. **CSS 상속**

   - 현재 속성이 상속된 속성 보다 우선된다.

```css
a {
  color: inherit;
}
```

- inherit 값을 사용할 경우 기본값이 아닌 상위요소에서 상속받은 값이 적용된다.

20. **가상 클래스 선택자 (CSS pseudo-class)** [MDN link](https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes)

    ```css
    a:visited {
      color: #ccc;
    }
    a:hover, a:focus{
      color: #f00;
    }
    ```

    - a:visited의 경우 해당 링크를 방문 했을 경우 적용되는 스타일
    - **우선순위 이슈**: hover, focus의 경우 다른 선택자보다 나중에 선언돼야한다.

21. **숨김제목**

    - nav메뉴에 보이진 않지만 검색엔진 등 접근성을 높게 하기 위해 heading 태그를 통해 제목을 지정해주는 것.
    - **WAI-ARIA 기술**을 사용하면 숨김제목 없이 나태낼 수 있다.
    - 둘 중 하나를 선택하여 nav의 컨텐츠를 설명할 수 있는 제목을 달아줘야한다.

    ```css
    .hidden{
      background: red;
      position: absolute;
      /*숨긴다는 의미로 폰트크기의 9999배 왼쪽으로 날림*/ 
      left: -9999em;
      width: 1px;
      height: 1px;
      font-size: 0;
      line-height: 0;
    }
    ```

    - position: absolute;를 사용함
    - width/height 1px은 가상기기 인식을 위해 남겨둔 것(left만 해줘도 됨)

22. **Position** (default: static, absolute, fixed, relative)

    - normal flow: 일반적인 마크업 흐름을 말함


    - absolute / fixed: 해당 옵션은 붕 떠서 자리를 차지하지 않는다.(겹쳐진다 layer개념)

      - default 상태는 static이다.


      -  특징: block개체로 바뀜, default: w:auto h:auto

      - static이 아닌 부모 요소(absolute, relative, fixed) 기준으로 offset(top, bottom, left, right) 조정 가능

        |      | static(default) |     absolute     |  fixed   |  relative   |
        | :--: | :-------------: | :--------------: | :------: | :---------: |
        | 기준점  |   normal flow   | 상위요소 (static 제외) | viewport | normal flow |
        |  속성  |     offset      |        -         |    -     |      -      |

    - relative: absolute의 기준으로 많이 쓰임.

23. [웹 접근성 연구소 link](www.wah.or.kr) 에서 주소창 클릭 후 Tab 키 3번 누르면 본문 바로가기 나옴.

    ```html
    <a href="#" class="skip-nav">본문 바로가기</a>
    ```

    ```css
    .skip-nav{
      position: absolute;
      left: -9999em;
    }
    .skip-nav:focus{
      left: 0;
    }
    ```

- 옆으로 날려서 안보이게 한 뒤, Tab으로 포커싱 될 때 left값을 초기화 하면서 화면에 보이도록 만든다.

## **\<HTML5 Review>**

- html5-css3.pdf 파일 참조



## **\<After Class>**

- **NVDA 웹사이트**: 시각장애인을 위한 웹사이트 스크린 리더 [Link](http://www.nvaccess.org/) 

- Outline Algorithm

   HTML5 outliner는 Body요소에 들어오면서 **heading tag**s(h1-h6,hgroup)와 **sectioning contents**(article,aside,body,div,nav,sectioin)를 찾아서 문서의 outline을 만든다. 각 section의 첫번째 heading 요소가 해당 section의 heading이 된다.

   각각의 section(태그x, 구역)들은 하나의 heading 요소를 가질 수 있으며, 그 안에는 또 다른 section들이 중첩으로 포함될 수 있다.

  - header, footer요소는 sectioning content가 아니다. 새로운 콘텐츠를 소개하는 것이 아니기 때문이다.
  - address 요소 역시 sectioning content가 아니다. 

  ​

## **\<질문>**

- ​







 