# Arrow Function

특징

- 함수 표현식에서만 사용이 가능하다.
- 1개의 매개변수만 전달할 경우 매개변수를 감싸는 괄호 생략가능
- 함수를 한 줄로 작성할 경우 return 키워드, 중괄호 생략이 가능하다.

```javascript
// ex1
document.body.me = function() {
  console.log(this);
  document.onclick = function {
    console.log(this); // this === document
  }

document.body.me = function() {
  console.log(this);
  document.onclick = ()=> {
    console.log(this); // this === body
  }
}
```

```javascript
// ex2
// 1
(function(){
  'use strict';
  console.log(this);
})(); // this === undefined
// 2
(function(){
  console.log(this);
})(); // this === window
// 3
(()=>{
  'use strict';
  console.log(this);
})(); // this === window
```

---

화살표 함수 식(**arrow function expression**)은 [function 식](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/function)에 비해 구문이 짧고 (자신의 [this](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this),[arguments](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments), [super](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/super) 또는 [new.target](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/new.target)을 바인딩 하지 않는) [this](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this) 값을 렉시컬(lexically, 정적) 바인딩 합니다. 화살표 함수는 항상 [익명](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/name)입니다.

## 구문

### 기본 구문

```
(param1, param2, …, paramN) => { statements }
(param1, param2, …, paramN) => expression
          // 다음과 동등함:  => { return expression; }

// 괄호는 매개변수가 하나뿐인 경우 선택사항:
(singleParam) => { statements }
singleParam => { statements }

// 매개변수가 없는 함수는 괄호가 필요:
() => { statements }
```

 

### 고급 구문

```
// 객체 리터럴 식을 반환하는 본문(body)을 괄호 속에 넣음:
params => ({foo: bar})

// 나머지 매개변수 및 기본 매개변수가 지원됨
(param1, param2, ...rest) => { statements }
(param1 = defaultValue1, param2, …, paramN = defaultValueN) => { statements }

// 매개변수 목록 내 비구조화도 지원됨
var f = ([a, b] = [1, 2], {x: c} = {x: a + b}) => a + b + c;
f();  // 6

```

상세한 구문 예는 [여기](http://wiki.ecmascript.org/doku.php?id=harmony:arrow_function_syntax)에서 볼 수 있습니다.

## 설명

[Hacks 블로그 "ES6 In Depth: Arrow functions" 포스트](https://hacks.mozilla.org/2015/06/es6-in-depth-arrow-functions/) 참조.

화살표 함수 도입에 영향을 준 두 요소: 짧은 함수 및 렉시컬(lexical) `this`.

### 짧은 함수

일부 함수 패턴에서는, 짧은 함수를 환영합니다. 비교해 보세요:

```
var a = [
  "Hydrogen",
  "Helium",
  "Lithium",
  "Beryl­lium"
];

var a2 = a.map(function(s){ return s.length });

var a3 = a.map( s => s.length );
```

### 렉시컬 `this`

화살표 함수 도입까지, 모든 새로운 함수는 자신의 `this` 값을 (생성자인 경우 새로운 객체, [엄격 모드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode)함수 호출에서는 undefined, 함수가 "객체 메서드"로서 호출된 경우 문맥 객체 등으로) 정의했습니다. 이는 객체 지향 스타일 프로그래밍에 성가신 일임이 드러났습니다.

```
function Person() {
  // Person() 생성자는 `this`를 자신의 인스턴스로 정의.
  this.age = 0;

  setInterval(function growUp() {
    // 비엄격 모드에서, growUp() 함수는 `this`를
    // 전역 객체로 정의하고, 이는 Person() 생성자에
    // 정의된 `this`와 다름.
    this.age++;
  }, 1000);
}

var p = new Person();
```

ECMAScript 3/5 에서는, 이 문제를 `this` 값을 폐쇄될 수 있는 (비전역) 변수에 할당하여 해결했습니다.

```
function Person() {
  var self = this; // 일부는 `self` 대신 `that`을 선택.
                   // 하나 골라 일관되게 사용.
  self.age = 0;

  setInterval(function growUp() {
    // 콜백은 값이 예상한 객체인
    // `self` 변수를 참조.
    self.age++;
  }, 1000);
}
```

또, [바인딩한 함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)는 적절한 `this` 값이 `growUp()` 함수에 전달될 수 있도록 생성될 수 있습니다.

화살표 함수는 (자신을) 둘러싸는 문맥의 `this` 값을 담습니다(capture), 그래서 다음 코드는 예상대로 작동합니다.

```
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| 는 정확히 person 객체를 참조
  }, 1000);
}

var p = new Person();
```

#### 엄격 모드와의 관계

`this`가 렉시컬(lexical, 정적)임을 감안하면, `this`에 관한 [엄격 모드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode) 규칙은 그냥 무시됩니다.

```
var f = () => {'use strict'; return this};
f() === window; // 또는 전역 객체
```

엄격 모드의 나머지 규칙은 평소대로 적용합니다.

#### call 또는 apply를 통한 피호출

`this`는 이미 렉시컬(lexically, 정적) 바인딩되었기에, `call()` 또는 `apply()` 메서드를 통한 화살표 함수 호출은 인수로 전달할 수 있을 뿐 `this`에 아무 영향이 없습니다:

```
var adder = {
  base : 1,
    
  add : function(a) {
    var f = v => v + this.base;
    return f(a);
  },

  addThruCall: function(a) {
    var f = v => v + this.base;
    var b = {
      base : 2
    };
            
    return f.call(b, a);
  }
};

console.log(adder.add(1));         // 이는 2가 콘솔에 출력될 것임
console.log(adder.addThruCall(1)); // 이도 2가 콘솔에 출력될 것임
```

### 렉시컬 `arguments`

화살표 함수는 코드에 [`arguments` 객체](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments)를 노출하지 않습니다: `arguments.length`, `arguments[0]`,`arguments[1]` 등은 호출될 때 화살표 함수에 제공되는 인수를 참조하지 않습니다. 대신, `arguments`는 그저 둘러싸는 범위(scope) 내 이름에 대한 참조입니다.

```
var arguments = 42;
var arr = () => arguments;

arr(); // 42

function foo() {
  var f = (i) => arguments[0]+i; // foo 함수의 암시된 arguments 바인딩
  return f(2);
}

foo(1); // 3
```

화살표 함수는 자신의 `arguments` 객체가 없지만, 대부분의 경우에 [나머지 매개변수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/rest_parameters)가 좋은 대안입니다:

```
function foo() {
  var f = (...args) => args[0];
  return f(2);
}

foo(1); // 2
```

### `new` 연산자 사용

화살표 함수는 생성자로서 사용될 수 없으며 `new`와 함께 사용하면 오류가 발생합니다.

### `yield` 키워드 사용

`yield` 키워드는 화살표 함수의 본문(그 안에 더 중첩된 함수 내에서 허용한 경우를 제외하고)에 사용될 수 없습니다. 그 결과, 화살표 함수는 생성기(generator)로서 사용될 수 없습니다.

## 함수 본문

화살표 함수는 "간결한 본문"이든 보통 "블록 본문"이든 하나를 가질 수 있습니다.

블록 본문 형태는 자동으로 값을 반환하지 않습니다. 명시된 `return` 문을 사용할 필요가 있습니다:

```
var func = x => x * x;                  // 간결한 구문, 암시된 "return"
var func = (x, y) => { return x + y; }; // 블록 본문이면, 명시된 "return"이 필요
```

## 객체 리터럴 반환

간결한 구문 `params => {object:literal}`을 사용한 객체 리터럴 반환은 예상대로 작동하지 않음을 명심하세요:

```
var func = () => {  foo: 1  };               // func() 호출은 undefined를 반환!
var func = () => {  foo: function() {}  };   // SyntaxError: function 문은 이름이 필요함
```

이는 중괄호({}) 안 코드가 일련의 문(즉 `foo`는 라벨처럼 취급됩니다, 객체 리터럴 내 키가 아니라)으로 파싱(parse, 구문 분석)되기 때문입니다.

객체 리터럴를 괄호로 감싸는 것을 기억하세요:

```
var func = () => ({ foo: 1 });
```

## 예

```
// empty 화살표 함수는 undefined를 반환
let empty = () => {};

(() => "foobar")() // "foobar" 반환

var simple = a => a > 15 ? 15 : a;
simple(16); // 15
simple(10); // 10

let max = (a, b) => a > b ? a : b;

// 쉬운 배열 필터링, 매핑, ...

var arr = [5, 6, 13, 0, 1, 18, 23];
var sum = arr.reduce((a, b) => a + b);  // 66
var even = arr.filter(v => v % 2 == 0); // [6, 0, 18]
var double = arr.map(v => v * 2);       // [10, 12, 26, 0, 2, 36, 46]

// 더 간결한 프로미스 체인
promise.then(a => {
  // ...
}).then(b => {
   // ...
});
```