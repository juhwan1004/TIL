# Node.nodeValue

> 노드의 값을 가져오거나 설정합니다.

## Syntax

`value = node.nodeValue;`

node.nodeValue가 존재하는 경우 value는 노드의 값을 포함하는 문자열입니다.

노드, comment노드, CDATA노드는 nodeValue노드의 내용을 반환합니다. attribute노드는 속성 값을 반환합니다.

값이 없는 경우 null 반환

# Node.nodeType

> 노드의 유형을 나타내는 정수 코드를 반환합니다.

## Syntax

`var type = node.nodeType;`

ELEMENT_NODE  === 1 (자주쓰임)

TEXT_NODE === 3 (자주쓰임)

---

# Example

```html
<h1 data-role="heading 1">
  <a
     title="open new tab window"
     href="../sass/node-info.sass" target="_blank">FAST CAMPUS</a>
</h1>
```

```css
// h1 변수가 참조하는 객체의 자식 텍스트 노드에 접근하려면?
var h1 = h1_link.parentNode;

console.log(h1_link.firstChild);
console.log(h1_link.firstChild.nodeType);

console.log(h1_link.firstChild);
console.log(h1_link.firstChild.nodeValue.nodeType);
```

.firstChild.nodeType의 경우 "FAST CAMPUS"라는 요소노드의 nodeType값인 정수 3을 반환

.firstChild.nodeValue.nodeType의 경우 "FAST CAMPUS"라는 요소노드의 문자열 값을 반환하는데 문자열의 경우 nodeType이 없으므로 undefined를 반환한다.

![nodetype_img2](https://cloud.githubusercontent.com/assets/13896252/23104222/d1135b38-f70c-11e6-97f7-dbc68d23d1ca.png)




**참고** 

1.[MDN: nodeValue](https://developer.mozilla.org/ja/docs/Web/API/Node/nodeValue)   

2.[MDN: nodeType](https://developer.mozilla.org/ja/docs/Web/API/Node/nodeType)  

