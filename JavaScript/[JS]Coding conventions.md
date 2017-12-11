# Pickupscanner Front-end JS Coding conventions
[Airbnb JS Coding convetions](https://github.com/airbnb/javascript) 중에서  픽업스캐너 프론트엔드 JS Coding conventions에 적용할 부분만 정리한 문서입니다.
## **1. Types**
### 1.1 Primitives: When you access a primitive type you work directly on its value.
- string
- number
- boolean
- null
- undefined
- symbol
```js
const foo = 1;
let bar = foo;

bar = 9;

console.log(foo, bar); // => 1, 9
```
Symbols cannot be faithfully polyfilled, so they should not be used when targeting browsers/environments that don't support them natively.

## **2. References**
### 2.1 Use const for all of your references; avoid using var. eslint: prefer-const, no-const-assign
Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
```js
// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;
```
### 2.2 If you must reassign references, use let instead of var. eslint: no-var jscs: disallowVar
Why? let is block-scoped rather than function-scoped like var.
```js
// bad
var count = 1;
if (true) {
  count += 1;
}

// good, use the let.
let count = 1;
if (true) {
  count += 1;
}
```
### 2.3 Note that both let and const are block-scoped.
```js
// const and let only exist in the blocks they are defined in.
{
  let a = 1;
  const b = 1;
}
console.log(a); // ReferenceError
console.log(b); // ReferenceError
```
## **3. Objects**
### 3.1 Use the literal syntax for object creation. eslint: no-new-object
```js
// bad
const item = new Object();

// good
const item = {};
```
### 3.3 Use object method shorthand. eslint: object-shorthand jscs: requireEnhancedObjectLiterals
```js
// bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```
### 3.4 Use property value shorthand. eslint: object-shorthand jscs: requireEnhancedObjectLiterals
Why? It is shorter to write and descriptive.
const lukeSkywalker = 'Luke Skywalker';
```js
// bad
const obj = {
  lukeSkywalker: lukeSkywalker,
};

// good
const obj = {
  lukeSkywalker,
};
```
### 3.5 Group your shorthand properties at the beginning of your object declaration.
Why? It’s easier to tell which properties are using the shorthand.
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';
```js
// bad
const obj = {
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  lukeSkywalker,
  episodeThree: 3,
  mayTheFourth: 4,
  anakinSkywalker,
};

// good
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  episodeThree: 3,
  mayTheFourth: 4,
};
```
### 3.6 Only quote properties that are invalid identifiers. eslint: quote-props jscs: disallowQuotedKeysInObjects
Why? In general we consider it subjectively easier to read. It improves syntax highlighting, and is also more easily optimized by many JS engines.
```js
// bad
const bad = {
  'foo': 3,
  'bar': 4,
  'data-blah': 5,
};

// good
const good = {
  foo: 3,
  bar: 4,
  'data-blah': 5,
};
```
## **4. Arrays**

