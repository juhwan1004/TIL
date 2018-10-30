#제어문

- noFallthroughCasesInSwitch 옵션: 기본은 false, switch 구문에서 fall through를 허용할 것인지에 대한 옵션

- for문에서 사용되는 변수에 타입을 설정하여 블록 레벨 스코프가 적용된다.

- for in문의 경우 index를 통해 값을 가져올 수 있다.
- for of문은 바로 값을 가져온다.  
일반적인 for문에서는 const의 사용이 안된다.  
for of문의 경우 Symbol.iterator의 구현을 통해 각 이터레이션 값의 요소를 가져오기 때문에 const를 사용할 수 있다.  

- [Symbol.iterator]() 메서드  
ES6에 추가된 특징, 배열, 맵, 셋과 같은 이터러블 객체를 순회하는 데 사용  


