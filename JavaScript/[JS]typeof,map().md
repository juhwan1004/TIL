|                     |                                          |
| ------------------- | ---------------------------------------- |
| ** 1. typeof 연산자 ** |                                          |
|                     | - 사용방법                                   |
|                     | typeof 변수 or 값                           |
|                     | typeof (변수 or 값)                         |
|                     | - 결과 값으로 6가지를 반환한다.                      |
|                     | 1) object (null 값을 포함한 객체)               |
|                     | 2) undefined (정의되지 않은 값)                 |
|                     | 3) string                                |
|                     | 4) number                                |
|                     | 5) boolean                               |
|                     | 6) function (함수 타입의 피연산자)                |
|                     |                                          |
|                     | ex)                                      |
|                     | var str1 = 'abc';                        |
|                     | typeof str1 === 'string' (결과는 true)      |
|                     | var str2                                 |
|                     | typeof str2 === 'undefined (결과는 true)    |
|                     |                                          |
|                     | ** Array map() Method **                 |
|                     | - array.map(function(currentValue,index,arr), thisValue) |
|                     | The map() method creates a new array with the results of calling a function for every array element. |
|                     |                                          |
|                     | The map() method calls the provided function once for each element in an array, in order. |
|                     |                                          |
|                     | Note: map() does not execute the function for array elements without values. |
|                     |                                          |
|                     | Note: map() does not change the original array. |
|                     |                                          |
|                     | #REFER                                   |
|                     | - http://www.w3schools.com/jsref/jsref_map.asp |
|                     |                                          |