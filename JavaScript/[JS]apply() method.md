# apply 메서드(Function)(JavaScript)

함수를 호출하여 지정된 개체를 함수의 **this** 값으로 대체하고 지정된 배열을 함수의 인수로 대체합니다.

## [구문](undefined)

```
apply([thisObj[,argArray]])

```

## [매개 변수](undefined)

- *thisObj*

  선택 사항입니다. **this** 개체로 사용될 개체입니다.

- *argArray*

  선택 사항입니다.함수에 전달될 인수 집합입니다.

## [설명](undefined)

*argArray*가 올바른 개체가 아니면 "개체가 필요합니다." 오류가 발생합니다.

*argArray*나 *thisObj*가 제공되지 않으면 원래 **this** 개체가 *thisObj*로 사용되고 인수는 전달되지 않습니다.

다음 코드에서는 apply 메서드를 사용하는 방법을 보여 줍니다

[JavaScript](undefined)

```
function callMe(arg1, arg2){
    var s = "";

    s += "this value: " + this;
    s += "<br />";
    for (i in callMe.arguments) {
        s += "arguments: " + callMe.arguments[i];
        s += "<br />";
    }
    return s;
}

document.write("Original function: <br/>");
document.write(callMe(1, 2));
document.write("<br/>");

document.write("Function called with apply: <br/>");
document.write(callMe.apply(3, [ 4, 5 ]));

// Output: 
// Original function: 
// this value: [object Window]
// arguments: 1
// arguments: 2

// Function called with apply: 
// this value: 3
// arguments: 4
// arguments: 5

```