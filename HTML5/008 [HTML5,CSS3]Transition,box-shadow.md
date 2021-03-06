**Front-End School 3**

# Day8  

## Index  

1. [아침 액티비티](#아침액티비티)
2. [탭 메뉴 구현](#탭메뉴구현)
3. [IR기법](#ir법)
4. [Transition](#transition) 
5. [box-Shadow](#box-shadow)  
6. [sprite 이미지](#sprite이미지)
7. [오늘의 구조도](#오늘의구조도)
8. [한 줄 Tip](#한줄tip)  

---

### 아침 액티비티    

   1. [Sololearn](https://www.sololearn.com/Courses/)  
   2. 그리드 시스템이란?
      - [그리드 시스템에 대해서 알아보자](http://inmoon99.tistory.com/m/34)
      - [웹 그리드 시스템](https://github.com/yamoo9/PSD2HTML-CSS/wiki/%EC%9B%B9-%EA%B7%B8%EB%A6%AC%EB%93%9C-%EC%8B%9C%EC%8A%A4%ED%85%9C)
      - [웹 그리드 시스템을 위한 가이드](http://slowalk.tistory.com/2270)   

### 탭 메뉴 구현  

```javascript
$(function(){    
  $('.tab').on('click',function(e){      
    e.preventDefault();      
    $(this).parent().parent().addClass('act').siblings().removeClass('act');
  });  
});
```

### IR기법 

접근성을 높이면서 이미지를 보여주기 위한 방법

   * 패딩 트릭: h0, p을 이미지 높이로 사용 후 넘치는 부분을 hidden  
   
   ```css
   .branding{
     background: #000 url(css/images/title.png) no-repeat;
     width: 290px;
     height: 0;
     padding-top: 195px;
     overflow: hidden;
   }
   ```  

   * 글자를 배경으로 덮는 방법  

   ```css
   .ir-bg{
     background:url(css/images/title.png) no-repeat;
     width: 290px;
     height: 195px;
     position: absolute;
     top: 0;
     left: 0;
   }
   ```  
 * 네이버 메인도 글자위에 글자이미지를 덮어 씌운 것


### Transition  

#### [공식문서](# https://www.w3.org/TR/css3-transitions/)
#### 트랜지션(transitions)은 애니메이션의 속도를 조절할 수 있는 CSS 속성이다.

![transition-img](https://cloud.githubusercontent.com/assets/13896252/22286890/020e875e-e334-11e6-9a6c-9887946d04fb.png)

#### 활용법
`transition-property`

트랜지션을 적용해야 하는 CSS 속성의 이름 혹은 이름들을 명시합니다. 여기에 나열한 속성만 트랜지션하는 동안 움직입니다. 또한, 다른 모든 속성에 대한 변화는 보통 때와 같이 즉시 일어납니다.

`transition-duration`

트랜지션이 일어나는 지속 시간을 명시합니다. 트랜지션 동안 모든 속성에 적용하는 단일 지속 시간을 명시하거나, 다른 주기로 각 속성이 트랜지션하게 하는 여러 지속 시간을 명시할 수 있습니다.

`transition-delay`

속성이 변한 시점과 트랜지션이 실제로 시작하는 사이에 기다리는 시간을 정의합니다.

단축 문법
```css
div {
    transition: <property> <duration> <timing-function> <delay>;
}
```

#### [cssreference.io 예제](# http://cssreference.io/transitions/)
transition을 활용한 다양한 예제가 시각적으로 잘 정리되어 있어 공부하기 좋습니다.

#### 수업에서 다룬 예제
```css
img {
  transform: rotate(0deg);
  transition: transform 1s, border-radius 1s 2s;
  background: red;
  border: 10px solid lime;
  width: 200px;
  height: 200px
}
img:hover, img:focus {
  transform: rotate(360deg);
  background: blue;
  border: 10px dashed silver;
  border-radius: 50%;
}
```

**참고**

[MDN CSS Transition 사용하기](# https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
   
### box-shadow    

- IE8 이하의 브라우저를 제외한 모든 브러우저에서 지원  
- 그래픽 프로그램을 이용하지 않고도 그림자 효과를 추가할 수 있다.  
- CSS3의 새로운 box-shadow 속성은 4개의 값을 가지며 최소 3개 이상의 값을 유지 해야한다.  

![browse](https://cloud.githubusercontent.com/assets/13896252/22287736/4cf3fe40-e337-11e6-824c-08cbf799e2c4.png)  

* `box-shadow` 의 기본값 `none`
* `box-shadow`: **X축**(1), **Y축**(2), blur-distance(3), spread-distance(4), 그림자색상(5), inset(6);
```
box-shadow: 0px 15px 15px 0px rgba(0,0,0,0.3);                       
```  

![box-shadow](https://cloud.githubusercontent.com/assets/13896252/22287706/22f102dc-e337-11e6-9d5d-995fa7ffe65d.png)

1. **X축**: 그림자의 가로 길이 양수는 오른쪽 음수는 왼쪽(필수값)
2. **Y축**: 그림자의 세로 길이(필수값)
3. **blur distance**: 흐려지기 시작하는 곳과 끝 사이의 길이 값을 설정(미설정시 선명한 그림자 효과)
4. **spread distance**: 그림자 확산 거리
5. **그림자 색상**: 16진수 값이나 컬러 상수 값으로 세팅할 수 있음
6. **inset**: 내부그림자 설정 
 
**참고**  
[html5around](http://html5around.com/wordpress/tutorials/css-box-shadow/)
[mainia](http://mainia.tistory.com/3511)  

### sprite 이미지       

 웹페이지를 제작할때 사용하는 아이콘,배너,버튼등을 한개의 그림파일에 넣어놓고
 css의 background-position속성을 사용하여 해당그림을 사용하는 방식.  
 
### 오늘의 구조도  
![오늘의 구조도](https://cloud.githubusercontent.com/assets/13896252/22288255/7045cf66-e339-11e6-885c-cfae0b8c013b.png)

### 한 줄 Tip  
   * [Zen Garden](http://www.csszengarden.com/) - CSS 참고  
   * 글자 강조를 위한 시맨틱 태그: 강한 강조 `<strong>`, 일반적인 강조 `<em>`  
   * [그리드 관련 사이트css-tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)    
   * outline 속성: `border: 1px` 는 박스의 크기에 포함되지만 outline은 포함되지 않는다.    
   * list 생성 단축키: Ctrl + Alt + W [Windows] , Ctrl + Option + W [Mac]     

**만들고자 하는 리스트 의 텍스트 입력 후**  

패스트캠퍼스  
생산성 본부  
멀티 캠퍼스  
웹접근성 연구소  
W3C  

**단축표현 입력**  

`ul.related-list>li*>a[#]`  

**완성**  

```html  
<ul class="related-list">
  <li>패스트캠퍼스</li>
  <li>생산성 본부</li>
  <li>멀티 캠퍼스</li>
  <li>웹접근성 연구소</li>
  <li>W3C</li>
</ul>
```  

