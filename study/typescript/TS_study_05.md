# 연산자
## 산술 연산자
| 사칙연산, %
- ES7의 exponentiation operator(지수 연산자) 지원함, Math.pow(10,3)로 변환되어 컴파일 된다.
```js
console.log(10 ** 3) --> 1000
```
- 숫자 값과 불리언 값은 연산할 수 없다.
```js
// ----- js
console.log(1 + false) // 1 + 0 
// ----- ts
console.log(1 + false) // error
```

## 비교,논리,조건 연산자
| 조건문에 사용할 수 있는 연산자  
- 피연산자 간에 타입이 다르면 연산을 허용하지 않는다.  
```js
// ----- js
console.log(1 == true) // true
// ----- ts
console.log(1 == true) // error
```
- 논리 연산자는 피연산자 간에 타입이 달라도 된다.  
## Destructuring
| 객체의 구조를 분해 후 할당이나 확장같은 연산을 수행
### object destructuring
- destructuring assignment(디스트럭처링 할당): 객체의 속성값을 변수에 할당
```js
let { id, company } =  {id: 1, company: "TSComp"};
console.log(id); // 1
console.log(compnay); // TSComp
```
- property renaming(속성명 재할당): 할당하면서 객체 속성명 변경
```js
let {code, country} = {id: 1, company: "TSComp"};
console.log(code); // 1
console.log(country); // TSComp
```
- 함수 매개변수 기본값 설정 가능
```js
function member({id, company = "TS"}) {
    console.log(id); // 33
    console.log(company); // TS
}
member({id: 33});
```
### array destructuring
- 변수 할당이 편리하다. 콤마(,)로 배열 값의 위치를 조정하여 할당 할 수 있다.
```js
let arr = [1,2,3,4,5];
let [item1, item2] = arr;
console.log(item1); // 1
console.log(item2);  // 2

let [,,item1,item2] = arr;
console.log(item1); // 3
console.log(itme2); // 4
```
- 배열값을 매개변수로 전달할 수 있다.
```js
function member([id, compnay]:[number, string]) {
    console.log(id); // 300
    console.log(company); // arrComp
}
member([300, "arrComp"]);
```
## Spread operator
| 나머지 매개변수 선언, 배열 요소 확장, 객체 요소 확장 시 사용된다.
- ...spreadParams
- 객체는 shallow copy한다. (shallow copy: 값의 레퍼런스 복사, deep copy: 값 복사)
