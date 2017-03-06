# Scope

**전역과 구분되는 지역 공간을 만들려면?** 함수를 정의한다.

'함수안의 함수'는 지역 내부의 지역이 된다.

함수의 블록문({})은 상위 영역과 구분되는 별도의 영역을 가진다.

```javascript
//전역(global scope)
var is_global_scope = true;

//함수 선언문(정의)
function localScope() {
  // 상위 영역과 구분되는 독립된 지역 공간이 생성
  // 함수 내에서 var 형태로 선언하는 것이 좋다.
  // var 없이 암시적으로 변수 선언 시 '스코프 체이닝'현상으로
  // JS엔진이 함수 밖에서 'var 변수명' 형태로 변수를 선언해준다.
  var is_local_scope = true;
  console.log('local:', is_local_scope); // true
}

// 함수 실행
localScope(); // true

console.log('global:', is_global_scope); // true
console.log('local:', is_local_scope); // Error, 지역변수를 참조하려고 해서 에러 발생
```

