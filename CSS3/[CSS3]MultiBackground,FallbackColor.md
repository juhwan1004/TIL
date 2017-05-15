**Front-end School 3**
# Day5

## Index
1. CSS개념
    * [Multiple Backgrounds](#multiplebackgrounds)
    * [Fallback Color](#fallbackcolor)
2. 기타
    * [조은님 html-best-practices 번역](#조은님html-best-practices번역)
    * [효율적인 CSS 작성](#효율적인CSS작성)
    * [입력서식 markup 예시](#입력서식markup예시)
    * [CSS 속성을 눈으로 보자!](#CSS속성을눈으로보자!)
    * [유효성 검사](#유효성검사)  

---
## 1. CSS개념
### Multiple Backgrounds
**데레사쌤 tip**: 이미지명은 하이픈(-)으로 적용할 경우 더 빠르게 인식한다.

* 이미지들은 콤마(,)로 구분한다.
* 이미지들은 각각의 위에 쌓인다.
* 처음 선언된 이미지가 가장 위에 온다.  



**예제**
```css
#example1 {
    background-image: url(img_flwr.gif), url(paper.gif);
    background-position: right bottom, left top;
    background-repeat: no-repeat, repeat;
}
```    

**참고**  
1. [w3school](http://www.w3schools.com/css/css3_backgrounds.asp)  
2. [MDN](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Background_and_Borders/Using_CSS_multiple_backgrounds)


### Fallback Color    
`color`값을 지정하는 3가지 기본방법   
- hexadecimal format (`#00000`  or `#000`)
- named color (`red`)
- `rgb()`  

CSS3에서는 몇가지 색상 format이 더 추가되었다.
- `rgba()`
- `hsl()`
- `hsla()` 

새로운 포맷의 추가로 더 많은 색상의 표현이 가능해졌지만 오래된 익스플로러8버전 이전의 브라우저들은 추가된 format을 이해하지 못하고 color속성을 무시해버린다.    
이 문제에 대한 해결방법이 Fallback Color를 지정해주는 것이다.  

```css
.box {
    background: #000;
    color: blue;
    color: rgba(100, 100, 200, 0.5);
}
```   
오래된 브라우저가 rgba 포맷을 이해하지 못해 무시할 경우 `background: #000;` 색상을 대체해서 보여준다.    

**참고**  
1. [CSSLint](https://github.com/CSSLint/csslint/wiki/Require-fallback-colors) 

## 2.기타  
1. **조은님 html-best-practices 번역**
  - 조은님 [Github](https://github.com/techhtml/html-best-practices/blob/master/README.md)   
2. **효율적인 CSS 작성**  
  - [Writing Efficient CSS](https://developer.mozilla.org/ko/docs/Web/CSS/Writing_Efficient_CSS)  
3. **입력서식 markup 예시**  
  - [Web Forms 2.0 demo page](https://miketaylr.com/pres/html5/forms2.html)  
4. **CSS 속성을 눈으로 보자!**  
  - [cssreference](http://cssreference.io/)  
5. **유효성 검사**  
  - [w3c HTML](https://validator.w3.org/)  
  - [w3c CSS](https://jigsaw.w3.org/css-validator/)  
  
---
[Index 바로가기](#index)
