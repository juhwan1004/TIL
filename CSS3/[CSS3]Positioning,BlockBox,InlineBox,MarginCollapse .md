# FastCampus 3일차

김데레사 강사님

e-mail: seulbinim@gmail.com

github: https://github.com/seulbinim/fastCampus

추천도서: 웹디자인 2.0 고급 CSS (앤디 클락)

  

## **\<용어 정리>**

1. **margin collapse**: margin이 **세로 방향**으로 겹쳤을 때 마진 값이 더 큰 쪽을 따르게 되는 현상
   1. 형제 엘리먼트 간: 둘 중에 큰 margin값 하나만 적용된다.
   2. 부모/자식 엘리먼트 간: 부모가 시각적인 요소(border, 컨텐츠)를 가지고 있을 않을 때 자식의 margin값이 부모의 margin값 보다 작은 경우 겹쳐져 부모의 margin값으로 나타난다. 
   3. 시각적인 요소가 없는 엘리먼트 자체적으로: 상하 margin중에 큰 값만 적용된다. 그 아래 있는 요소의 margin값 역시 위의 요소보다 작은 margin값인 경우 겹침이 일어난다.
2. **!doctype**은 표준모드로 렌더링하기 위한 선언이다. 호환모드 선언 시 박스모델 width크기안에 padding border를 포함시킨다.(콘텐츠 내용이 줄어든다.)



### **\<Positioning>**

|                                  | 정적위치(static)           | 상대위치 (relative)                          | 절대위치 (absolute)                          | 고정위치(fixed) |
| -------------------------------- | ---------------------- | ---------------------------------------- | ---------------------------------------- | ----------- |
| 기준위치                             | 자기위치                   | 자기위치                                     | 문서(html), 시작 위치는 static 기준으로 원래의 위치에 맞춰져 있음. | 절대위치와 동일    |
| 부모의 크기                           | 자식의 크기에 따라 변경          | 자식의 크기에 따라 변경되지만 위치를 변경함에 따라 부모의 크기가 변경되지는 않음 | 부모의 크기에 영향을 끼치지 않음                       | 절대위치와 동일    |
| 자신의 크기                           | width:100%로 부모의 크기를 따름 | width:100%로 부모의 크기를 따름                   | 포함하고 있는 컨텐트의 크기 만큼 늘어남                   | 절대위치와 동일    |
| offset 사용(left,right.top,bottom) | 불가                     | 가능                                       | 가능                                       | 가능          |
| 스크롤                              | 따라감                    | 따라감                                      | 따라감                                      | 고정          |

- position:relative 성질이 바뀌지 않는다. 본인이 있던 위치 기준으로 이동, 다른 영역에 영향 없음

- position:absolute 설정 시 block의 성질을 가지며, static이 아닌 요소를 찾을때까지 상위요소를 탐색한다 (최종 body요소까지), 가까운 상위요소의 **content box 기준으로 offset값이 적용**된다.

- position:fixed 상하좌우 위치를 0px로하면 화면 가운데에 위치한다.

- 중요한 기능: display:**inline-block** -> inline의 모양을 유지하면서 block 크기를 갖는 것

- 가로정렬을 할 수 있는 기능들**flex, float, inline-block**

  - inline-block으로 가로정렬 시 사이에 틈이 발생, float은 틈이 없다.

    - 해결방법: ?

  - 기본 폰트 크기: 데스크탑:16px, 모바일: 14px

  - 하위 선택자 선택 시 중간단계는 제외하는 것을 권장한다.

  - display 설정 시 자식요소는 부모보다 더 큰 레벨가질 수 없다.

     ex) 부모가 inline-block일 경우 자식은 block은 안된다. 부모block 자식block가능

  - 박스모델은 상속 x, inhreit를 사용하면 상속 가능, 데코만 상속

- :link, :visited는 a태그에만 사용가능.

- **가상요소선택자**

- ```css
  .lnb a::before{
    content: "가상요소 박스";
    background: aqua;
  }
  ```

  - a요소 앞에 가상의 박스를 추가해 줌 content 속성에서 내용을 지정가능
  - 가상의 박스는 선택이 안된다. 장식 용도로 자주 쓰임 
  - 가짜상자 만들기 :before, ::before, :after, ::after (콜론의 수는 무관, 같은 의미다.) 


-   태그뒤에 가상의 태그(가짜상자)를 만드는 방식

-   **구조선택자**

    - :first-child
    - :last-child

-   **float 속성**

    - 부모요소 기준(position 여부 관계없이 항상 부모기준) left, right, none 값을 가짐
    - 특징1:float 속성을 주면 inline성질의 태그도 block의 성질을 가지게된다.
    - 특징2: float속성은 컨텐츠와 겹칠 순 없지만 크기가 커지면 주변 요소 box에 영향을 줄 수 있다. -> 해결방법: 영향을 받는 곳에 clear:both 속성을 준다. clear는 자동적으로 분리를 하기위해 자동으로 margin값이 주어진다. 이후에 더 공간을 주기위해 margin값을 주면 자동으로 추가된 margin값 이하는 겹쳐진다. 그 이상을 줘야 겹침이상 margin값이 적용됨.
    - clear: left,right보단 both으로 대부분 사용
    - float의 부모요소에 overflow visible을 제외한 값을 사용해서 부모요소를 넘지 않도록 조절가능하다.

    ```css
        .box::after{
          content: "";
          background: gray;
          display: block;
          clear:both;
        }
    ```

    - 가상요소선택자로 float문제를 해결가능

    ```css
    .main-menu > li{
      float: left;
    }
    ```

    - 부등호(>)를 사용하여 .main-menu 모든 자식 li가 아닌 바로 아래 자식 li만 선택할 수 있다.

    ​

-   **기본 스타일 세팅**

    - 레이아웃 세팅 전에 해줘야한다.

    ```css
    *{
    	margin:0;
    	padding:0;
    }
    ```

    - p,h1 등 여백을 가진 개체들의 기본 값을 조정한다. *(유니버셜 셀렉터, 우선순위가 가장 낮다.)를 사용한다.

    ```css
    html,body,div,header,nav,section,aside,article,footer,figure,figcaption,ul,ol,li,dl,dt,dd,h1,h2,h3,h4,h5,h6,p,fieldset{
    	margin:0;
    	padding:0;
    }
    ```

    - 권장사항은 필요한 부분만 선택하여 세팅하는 것

-   **rem (렘) 단위 / em(엠) 단위**

    ```css
      html{
        font-size: 10px;
      }
      body {
        margin: 0;
        /**/
        font-size: 1.4rem;
      }
    ```

    - rem: root(html) 기준으로 배수 설정.(위에선 body폰트는 html을 기준으로 한다.)
    - em 단위는 상속이 되기 때문에 조심하게 사용해야한다.
    - 단점: 모던브라우저에서만 지원

-   폰트: noto sans 추천

    - 폰트 선언 방식

    ```css
    @font-face {
        font-family: 'Noto Sans Regular';
        font-style: normal;
        font-weight: 400;
        src: local('Noto Sans Regular'), local('NotoSans-Regular'),
        url('font/eot/NotoSansKR-Regular-Hestia.eot'),
        url('font/eot/NotoSansKR-Regular-Hestia.eot?#iefix') format('embedded-opentype'),
        url('font/woff/NotoSansKR-Regular-Hestia.woff') format('woff'),
        url('font/otf/NotoSansKR-Regular-Hestia.otf') format('opentype');
    }
    ```

    ​

    - ```css
      .main-menu > li > a{
        color: #fff;
        font-size: 1.6rem;
        font-family: "Noto Sans Bold";
        line-height: 45px;
        display: block;
      }
      ```

    - line-height 트릭: 한 줄의 메뉴를 가운데 정렬시킬 때 배경의 height만큼 line-height값을 준다. 그럼 자동으로 글자가 중간에 위치한다.

      -> 이렇게 하면 여백은 링크 클릭이 안됨 

      -> 해결 방법: display:block으로 해주면 링크의 크기가 여백만큼 늘어남

## **\<블럭 박스 / 인라인 박스>**

**컨테이닝 박스**(containing box) : 부모요소는 하위요소를 위해 컨테이닝 박스를 생성합니다. 부모의 컨테이닝 블록을 기준으로 하위요소의 박스 위치나 크기등을 결정합니다.

![img](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/484/1356.gif)

**블럭박스**(block box):  div, p, h1~h6와 같은 블럭레벨 요소들은 블럭 박스를 생성합니다.
**인라인박스**(inline box):
 span, a, img와 같은 인라인레벨 요소들은 인라인 박스를 생성합니다. 인라인 요소는 부모요소의 컨테이닝 박스에 수평으로 
연이어 배치되며 부모요소의 크기를 넘어갈 경우 자동으로 줄이 바뀌어 "행(line)"을 형성합니다. 

<그림 추가>

## 가명 블럭 박스(anonymous block box)

위 코드는 div요소의 블럭박스 안에 인라인 박스("Some text" 부분)와 블럭 박스(p안의  "More text" 부분)가 섞여 있는것 처럼 보이지만, "Some text"부분도 블럭박스로 취급됩니다. 이렇게 생성된 박스를 가명 블럭 박스라고 합니다.

## 가명 인라인 박스(anonymous inline box)

위 코드는 p요소의 블럭 박스 안에 strong요소로 둘러 싸여 있는 "More text"만 인라인블럭을 생성하는 것 처럼 보이지만, 실제로는 Some text부분도 인라인 블럭으로 취급됩니다.

## display 속성

display속성을 이용하면 블럭레벨 요소 혹은 인라인레벨의 요소를 만들 수 있습니다.
임의의 요소를 블럭레벨 요소로 만들려면 display의 block, list-item, table값을 이용하면 됩니다.
임의의 요소를 인라인 레벨 요소로 만들려면 inline, inline-table값을 이용하면 됩니다.

참조: [생활코딩](https://opentutorials.org/module/484/4124)

## **\<Overflow:hidden>**

- CSS2.1 에서 overflow:hidden에 관련하여 명시가 되어있다.[10.6.6 / 10.6.7](https://www.w3.org/TR/CSS21/visudet.html#block-root-margin)

>“일반적인 문서 흐름(normal flow)에서 블록 레벨 요소의 `overflow` 값이 `visible`이 아니고 `height`가 `auto`면 그 자손 요소에 따라서 6.7절에 명시된대로 높이가 결정된다.”

 >6.7절
 >
 >“만약 요소가 `float`된 자손 요소를 갖고 이 자손 요소의 하단 마진 경계(bottom margin-edge)가 요소 박스 아래에 있으면 요소 박스의 높이는 자손 요소의 하단 마진 경계를 포함하도록 늘어난다.”



하나의 부모요소 안에서 자식요소에 float를 적용 시킬 경우 아래의 요소가 아래로 겹쳐짐을 막기 위해 overflow:visible을 제외한 값(hidden 등)을 적용하면 float가 적용된 요소와 그 아래의 요소가 겹쳐지지 않는다.(부모의 height값 = float요소 height+나머지 자식요소 height)

참조: [wystan's tales](http://blog.wystan.net/)

## **<사이트 설계 순서>**

1. 구조 설계: html 마크업 후(틀 만들기)
2. 네이밍(클래스명 등)
3. 아웃라인 설계(heading 명 설정)
4. 레이아웃 제작(표준은 없고 내가 생각한 구조로 만든 뒤 주석달기)



## **\<After Class>** 

- slack 자료보고 정리양식 따라해보기
- 생활코딩 CSS 강좌 보기
- [참조사이트](http://naradesign.net/wp/):굉장히 양질의 자료가 있음 매일 볼 것
- position.html 예제 파일 학습