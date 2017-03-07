# 메서드 빌려쓰기 패턴

```javascript
Function.prototype // Function.prototype 속성안에
{
  'call': function() {} // 이러한 능력이 있다.
  'apply': function() {}
  'bind': function() {}
}
```

함수의 .call(), .apply(), .bind() 메서드를 사용

```javascript
var bird = {
  'kind': 'small bird',
  'fly': function() { console.log(this.kind + ' 날다.')}
};
var human = {
  'kind': 'Giant',
  'walk': function() { console.log(this.kind + ' 걷다.')}
};
// bird 객체의 능력(메서드)을 human이 빌려썼다.
// bird.fly의 this가 human을 가리키도록 call했다.
bird.fly.call(human) // 'Giant 날다'
```

| 메서드 명   | 실행 시기                          | 전달 인자     |
| ------- | ------------------------------ | --------- |
| call()  | this가 가리키는 context가 바뀐 뒤 바로 실행 | 콤마(,)로 구분 |
| apply() | this가 가리키는 context가 바뀐 뒤 바로 실행 | 배열 집합 전달  |
| bind()  | 바로 실행되지 않는다.                   | 콤마(,)로 구분 |

this의 context를 변경해줄 수 있다.

```javascript
function assignArgs() {
  console.log('this': this);
  console.log('arguments:': arguments);
}
// 전역함수assignArgs내부 this의 context를 window -> document.body로 변경하고 1,2,3을 arguments 객체에 전달해준다.
window.assignArgs.call(document.body, 1,2,3);

// 실행 결과
this: docuement.body
arguments = [1,2,3];
```













