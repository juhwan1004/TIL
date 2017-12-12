# Pickupscanner's Front-end Git branch strategy (beta version)
- 이유: master branch에서 프론트엔드 영역의 모든 테스트/배포가 이루어지는 상태에 대한 개선이 필요하다고 생각함. 
- 적용대상: 픽스 프론트엔드 개발팀
- 사용하려는 전략: [Github flow](https://guides.github.com/introduction/flow/)  
## Github Flow?
- **master**: 언제든 deploy가능한 상태로 유지한다.
    - 버그가 발생 시 HEAD를 과거로 돌린다.
    - 테스트 후 master branch에 merge
- **branch**: 다른 개발자가 보더라도 어떤 기능인지 알수있도록 branch명을 작성하고, 모든 작업을 할 때 새로운 브랜치를 생성한다. (실제 개발이 이루어 지는 branch)
    - 새로운 기능 추가
    - 버그 수정
## 네이밍
- branch명은 [Camel case](https://en.wikipedia.org/wiki/Camel_case)를 
적용한다.
## 작업 흐름
작업별 branch 생성 -> 개발(최소단위의 commit) -> PR -> master에 merge  
## Commit 메시지 작성
- 첫 번째 줄: commit에서 변경된 내용을 요약(최소단위로 하나씩)
- 두 번째 줄: 빈 칸
- 세 번째 줄: 변경한 이유

