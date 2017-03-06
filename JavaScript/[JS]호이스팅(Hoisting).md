### 호이스팅(Hoisting)

JavaScript는 선언문을 모두 **호이스트(Hoist)**한다. 호이스트란 `var` 구문이나 `function` 선언문을 해당 스코프의 맨 위로 옮기는 것을 말한다.

```javascript
bar();
var bar = function() {};
var someValue = 42;

test();
function test(data) {
    if (false) {
        goo = 1;

    } else {
        var goo = 2;
    }
    for(var i = 0; i < 100; i++) {
        var e = data[i];
    }
}
```

코드를 본격적으로 실행하기 전에 JavaScript는 `var` 구문과 `function` 선언문을 해당 스코프의 맨위로 옮긴다.

```javascript
// var 구문이 여기로 옮겨짐.
var bar, someValue; // default to 'undefined'

// function 선언문도 여기로 옮겨짐
function test(data) {
    var goo, i, e; // Block Scope은 없으므로 local 변수들은 여기로 옮겨짐
    if (false) {
        goo = 1;

    } else {
        goo = 2;
    }
    for(i = 0; i < 100; i++) {
        e = data[i];
    }
}

bar(); // bar()가 아직 'undefined'이기 때문에 TypeError가 남
someValue = 42; // Hoisting은 할당문은 옮기지 않는다.
bar = function() {};

test();
```

블록 스코프(Block Scope)는 없으므로 for문과 if문 안에 있는 `var` 구문들까지도 모두 함수 스코프 앞쪽으로 옮겨진다. 그래서 `if` Block의 결과는 좀 이상해진다.

원래 코드에서 `if` Block은 *전역 변수* `goo`를 바꾸는 것처럼 보였지만 호이스팅(Hoisting) 후에는 *지역 변수*를 바꾼다.

*호이스팅*을 모르면 다음과 같은 코드는 `ReferenceError`를 낼 것으로 생각할 것이다.

```javascript
// SomeImportantThing이 초기화됐는지 검사한다.
if (!SomeImportantThing) {
    var SomeImportantThing = {};
}
```

`var` 구문은 *전역 스코프*의 맨위로 옮겨지기 때문에 이 코드는 잘 동작한다.

```javascript
var SomeImportantThing;

// SomeImportantThing을 여기서 초기화하거나 말거나...

// SomeImportantThing는 선언돼 있다.
if (!SomeImportantThing) {
    SomeImportantThing = {};
}
```

```javascript
// if문 예제
// 호이스팅 되기 전
if ( some ) {
  var some = '행복한 사람들';
} else {
  some = '행복하지 않은 사람들';
}
console.log('some:', some); // '행복하지 않은 사람들' 출력

why???

// 호이스팅 된 결과
  
호이스팅 된 변수 var some는 '영역 최상위 위치'로 끌어 올려진다.
var some; // 1) undefined로 파일 제일 위에 변수값을 제외한 선언문만끌어올려져 선언됨
if ( some ) { // 2) undefined는 false이므로
  some = '행복한 사람들';
} else {
  some = '행복하지 않은 사람들'; // else문에서 복사된 값이 출력
}

Tip, 변수 선언을 가장 위에 모아두면 호이스트를 예방할 수 있다.
함수의 블록은 지역이 된다.
//---------------------------------------------------------------

// for문 예제, 다음 for문을 호이스팅 된 형태로 바꾸시오.
// 호이스팅 적용 전
var links = document.querySelectorAll('a');
for (var i=document.querySelectorAll('a').length-1; i>=0; i--) {
  document.querySelectorAll('a')[i];
}
// 호이스팅 적용 후: 변수들이 끌어올려진다.
var links = document.querySelectorAll('a'),
    i = links.length-1,
    link = null;

for ( ; (link = links[i]); ) { // 변형된 형태의 for문
  console.log('link:',link);
  i--;
}
```

