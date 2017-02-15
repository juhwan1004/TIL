# Node.nodeType

> nodeType property는 elements, text, comments 처럼 서로 다른 종류의 노드를 구별하는데 사용할 수 있습니다.

## Syntax  

`var type = node.nodeType;`  

`.nodeName` : 현재 노드의 이름을 문자열로 반환해줍니다.     

`.nodeType` : 각 노드 타입마다 해당하는 정수 값이 반환 됩니다.  

ELEMENT_NODE === 1  

TEXT_NODE === 3  

e.g.) 아래의 `<p>안녕하세요</p>` 에서 element node와 text 노드를 찾아보자  

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>nodeType</title>
</head>
<body>
  <p>안녕하세요</p>
</body>
</html>
```

![nodeType_img1](C:\Users\JuHwan\Desktop\nodeType_img1.png)

nodeName으로 Element 노드의 경우  Tag명이 반환된다.  

nodeType === 1  

![nodeType_img2](C:\Users\JuHwan\Desktop\nodeType_img2.png)

nodeName은 Text 노드의 경우 #text가 반환된다.  

nodeType === 3  



**참고 ** 

1. [MDN, nodeType](https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType)  
2. [MDN, nodeName](https://developer.mozilla.org/ko/docs/Web/API/Node/nodeName)



