# [Tip] .getAttribute()로 속성 

Node.id | className | title과 같은 예전 방식으로는 **custom속성(data-) | aria- 의 원치 않은 속성값을 가져오는 경우가 있다.**

.getAttribute() 메서드를 사용하면 원하는 속성 값을 가져올 수 있다.

## e.g.

로컬에서 동작 시 href의 값을 해당 파일의 절대경로를 반환하는 경우가 있음

`.getAttribute('data- | aria label')`은 지정한 상대경로를 제대로 반환해준다.

![nodetype_img1](C:\Users\JuHwan\Desktop\nodetype_img1.png)