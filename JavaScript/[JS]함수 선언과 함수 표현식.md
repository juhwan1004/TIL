## 함수 선언과 함수 표현식

JavaScript에서 함수는 First Class Object다. 즉, 함수 자체가 다른 함수의 인자가 될 수 있고, 함수 반환도 가능하다. 그래서 익명 함수를 비동기 함수의 콜백으로 넘기는 것도 이런 특징을 이용한 일반적인 사용법이다.

- 함수는 return이 없을 경우 암시적으로 undefined를 반환한다.
- function 리터럴: 변수에 참조되는 함수 e.g.) var variable = **function() {...}**;

###  함수 선언

```javascript
function foo() {} // function foo() {} 전체가 호이스팅 된다.
```

위와 같이 선언한 함수는 프로그램이 실행하기 전에 먼저 [호이스트(Hoist)](http://bonsaiden.github.io/JavaScript-Garden/ko/#function.scopes) (스코프가 생성)되기 때문에 정의된 스코프(Scope) 안에서는 어디서든 이 함수를 사용할 수 있다. 심지어 함수를 정의하기 전에 호출해도 된다.

```javascript
foo(); // 이 코드가 실행되기 전에 foo가 만들어지므로 잘 동작한다.
function foo() {}
```

### 함수 표현식

```javascript
var foo = function() {};
```

위 예제는 `foo` 변수에 *익명* 함수를 할당한다.

```javascript
foo; // 'undefined'
foo(); // TypeError가 난다.
var foo = function() {};
```

'var'문을 이용해 선언하는 경우, 코드가 실행되기 전에 'foo' 라는 이름의 변수를 스코프의 맨 위로 올리게 된다.(호이스트 된다) 이때 foo 값은 undefiend로 정의된다.

하지만 변수에 값을 할당하는 일은 런타임 상황에서 이루어지게 되므로 실제 코드가 실행되는 순간의 `foo`변수는 기본 값인 [undefined](http://bonsaiden.github.io/JavaScript-Garden/ko/#core.undefined)이 된다.

### 이름있는 함수 표현식

이름있는 함수를 할당할때도 특이한 경우가 있다.

```javascript
var foo = function bar() {
    bar(); // 이 경우는 동작 하지만, 
}
bar(); // 이 경우는 참조에러를 발생시킨다. 
```

foo 함수 스코프 밖에서는 foo 변수 외에는 다른 값이 없기 때문에 `bar`는 함수 밖에서 사용할 수 없지만 함수 안에서는 사용할 수 있다. [이와 같은 방법](http://bonsaiden.github.io/JavaScript-Garden/ko/#function.scopes)으로 자바스크립트에서 어떤 함수의 이름은 항상 그 함수의 지역 스코프 안에서 사용할수있다. 재귀함수에 사용가능