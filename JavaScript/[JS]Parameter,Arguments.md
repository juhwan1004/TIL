**매개변수(Parameter), 전달인자(Arguments)** 차이는?

전달인자: 함수가 실행될 때 전달되는 값

매개변수: 함수 선언 시 사용되는 변수

```javascript
 // 함수 정의할 때 사용되는 변수는 '매개변수'
function goto(where) {
  // null,undefined는 false
  if ( !where ) {throw new Error('Error');} 
  console.log('go to' + where);
}
// 함수 실행 시 전달하는 값을 '전달인자'라고 한다.
goto('School'); // 'go to School'

```



