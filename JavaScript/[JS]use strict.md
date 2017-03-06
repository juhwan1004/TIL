# 'use strict';

**"use strict"** (엄격한 자바스크립트)

- 느슨한 JS를 보다 엄격하게 관리
- 변수 선언 시 var 사용 안하면 에러발생
- 앞으로 함수 선언 시 써주는 것이 좋다.(특히 모듈)
- 주로 함수 내부에서 사용
- 함수 상단에 선언해주는 것이 좋다.

```javascript
// 느슨한 JS 코드 실행 영역
var temp = '임시 정부';
function fn() {
  // 엄격한 JS 코드 실행 영역
  'use strict';
  console.log(this);
  // 엄격한 모드에서 var없이 변수 선언하면 에러발생
} 
// 엄격한 모드에서 this는 함수를 실행하는
// context 객체가 암시적일 때 undefined를 반환한다.
fn(); // this === undefined
window.fn(); // this === window{}
```

e.g.) "use strict";를 선언하면 된다. use strict를 지원하면 strict 모드적용되고, 

지원하지 않으면 "use strict"를 문자열로 인식. -> 문제발생안함