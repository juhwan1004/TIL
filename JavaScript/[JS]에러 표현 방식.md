에러 표현 방식

1) console.error('error msg');

에러 메시지 출력되고 이후 나머지 코드들도 실행된다.

실행되지 않도록 하려면 return을 사용하여 함수를 종료시켜준다. 

```javascript
function sum(n1, n2) {
  if ( typeof n1 !== 'number' || typeof n2 !== 'number' ) {
    return console.error('전달된 인자가 숫자가 아닙니다.');
  }
  return n1 + n2;
}
```

2) throw new Error('error msg');

에러 메시지를 출력하며 이후 코드들은 실행되지 않는다.

```javascript
function sum(n1, n2) {
  if ( typeof n1 !== 'number' || typeof n2 !== 'number' ) {
    throw new Error('전달된 인자가 숫자가 아닙니다.');
    // 아래 코드들은 실행되지 않는다.
  }
  return n1 + n2;
}
```

