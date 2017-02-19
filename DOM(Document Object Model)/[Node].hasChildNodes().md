# Node.hasChildNodes()

> `Node.hasChildNodes()` 메소드는 현재 노드(Node)에게 자식노드(child nodes)가 있는지를 `Boolean`값으로 반환합니다.

## Syntax

`node.hasChildNodes()`

```html
<div id="page">
  <div class="container" title="Bootstrap Style Grid System"> // containers[0]
    <div class="row">
      <div class="col-xs-12 col-sm-6 col-sm-offset-3">
        <h1 data-role="heading 1">
          <a
             title="open new tab window"
             href="../sass/node-info.sass" target="_blank">FAST CAMPUS</a>
        </h1>
      </div>
    </div>
  </div>
</div>
<div class="container"></div> // containers[1]
<div class="container"></div> // containers[2]
```

```css
// hasChildNodes() 결과
var containers = document.getElementsByClassName('container');

console.log(containers[0].hasChildNodes()); // true
console.log(containers[1].hasChildNodes()); // false
console.log(containers[2].hasChildNodes()); // false
```

