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
### 4.1 Use the literal syntax for array creation. eslint: no-array-constructor
```js
// bad
const items = new Array();

// good
const items = [];
```
### 4.2 Use Array#push instead of direct assignment to add items to an array.
```js
const someStack = [];

// bad
someStack[someStack.length] = 'abracadabra';

// good
someStack.push('abracadabra');
```
### 4.3 Use array spreads ... to copy arrays.
```js
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i += 1) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```
### 4.4 To convert an array-like object to an array, use spreads ... instead of [Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from).
```js
const foo = document.querySelectorAll('.foo');

// good
const nodes = Array.from(foo);

// best
const nodes = [...foo];
```
### 4.5 Use [Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) instead of spread ... for mapping over iterables, because it avoids creating an intermediate array.
```js
// bad
const baz = [...foo].map(bar);

// good
const baz = Array.from(foo, bar);
```
### 4.6 Use return statements in array method callbacks. It’s ok to omit the return if the function body consists of a single statement returning an expression without side effects, following 8.2. eslint: array-callback-return
```js
// good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});

// good
[1, 2, 3].map(x => x + 1);

// bad - no returned value means `memo` becomes undefined after the first iteration
[[0, 1], [2, 3], [4, 5]].reduce((memo, item, index) => {
  const flatten = memo.concat(item);
  memo[index] = flatten;
});

// good
[[0, 1], [2, 3], [4, 5]].reduce((memo, item, index) => {
  const flatten = memo.concat(item);
  memo[index] = flatten;
  return flatten;
});

// bad
inbox.filter((msg) => {
  const { subject, author } = msg;
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee';
  } else {
    return false;
  }
});

// good
inbox.filter((msg) => {
  const { subject, author } = msg;
  if (subject === 'Mockingbird') {
    return author === 'Harper Lee';
  }

  return false;
});
```
### 4.7 Use line breaks after open and before close array brackets if an array has multiple lines
```js
// bad
const arr = [
  [0, 1], [2, 3], [4, 5],
];

const objectInArray = [{
  id: 1,
}, {
  id: 2,
}];

const numberInArray = [
  1, 2,
];

// good
const arr = [[0, 1], [2, 3], [4, 5]];

const objectInArray = [
  {
    id: 1,
  },
  {
    id: 2,
  },
];

const numberInArray = [
  1,
  2,
];
```
## **5. Destructuring**
### 5.1 Use object destructuring when accessing and using multiple properties of an object. eslint: prefer-destructuring jscs: requireObjectDestructuring
Why? Destructuring saves you from creating temporary references for those properties.
```js
// bad
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;

  return `${firstName} ${lastName}`;
}

// good
function getFullName(user) {
  const { firstName, lastName } = user;
  return `${firstName} ${lastName}`;
}

// best
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}
```
### 5.2 Use array destructuring. eslint: prefer-destructuring jscs: requireArrayDestructuring
```js
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```
### 5.3 Use object destructuring for multiple return values, not array destructuring. jscs: disallowArrayDestructuringReturn
Why? You can add new properties over time or change the order of things without breaking call sites.
```js
// bad
function processInput(input) {
  // then a miracle occurs
  return [left, right, top, bottom];
}

// the caller needs to think about the order of return data
const [left, __, top] = processInput(input);

// good
function processInput(input) {
  // then a miracle occurs
  return { left, right, top, bottom };
}

// the caller selects only the data they need
const { left, top } = processInput(input);
```
## **6.Strings**
### 6.1 Use single quotes '' for strings. eslint: quotes jscs: validateQuoteMarks
```js
// bad
const name = "Capt. Janeway";

// bad - template literals should contain interpolation or newlines
const name = `Capt. Janeway`;

// good
const name = 'Capt. Janeway';
```
### 6.2 Strings that cause the line to go over 100 characters should not be written across multiple lines using string concatenation.
Why? Broken strings are painful to work with and make code less searchable.
```js
// bad
const errorMessage = 'This is a super long error that was thrown because \
of Batman. When you stop to think about how Batman had anything to do \
with this, you would get nowhere \
fast.';

// bad
const errorMessage = 'This is a super long error that was thrown because ' +
  'of Batman. When you stop to think about how Batman had anything to do ' +
  'with this, you would get nowhere fast.';

// good
const errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';
```
### 6.3 When programmatically building up strings, use template strings instead of concatenation. eslint: prefer-template template-curly-spacing jscs: requireTemplateStrings
Why? Template strings give you a readable, concise syntax with proper newlines and string interpolation features.
```js
// bad
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// bad
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// bad
function sayHi(name) {
  return `How are you, ${ name }?`;
}

// good
function sayHi(name) {
  return `How are you, ${name}?`;
}
```
### 6.4 Never use eval() on a string, it opens too many vulnerabilities. eslint: no-eval
### 6.5 Do not unnecessarily escape characters in strings. eslint: no-useless-escape
Why? Backslashes harm readability, thus they should only be present when necessary.
```js
// bad
const foo = '\'this\' \i\s \"quoted\"';

// good
const foo = '\'this\' is "quoted"';
const foo = `my name is '${name}'`;
```
