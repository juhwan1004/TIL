# arguments Object

JS 함수는 arguments라는 특별한 변수가 있다. 이 변수는 함수에 넘겨진 모든 인자에 대한 정보가 담겨 있다.

함수 내부에서만 존재하며 함수를 실행할 때 전달한 인자들의 집합을 참조하는 객체이다.

arguments Object는 배열이 아닌 유사배열이며, length 속성을 가진다.

```javascript
// 전달된 숫자 집합의 총 합을 구하여 값을 반환하는 sum 함수
function sum() {
  for( var total=0, i=arguments.length-1; i>=0; i-- ) {
    total += arguments[i];
  }
  return total;
}
```

