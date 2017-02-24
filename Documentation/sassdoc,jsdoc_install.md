# JS DOC 설치하기  

## 준비사항  

- npm 설치  
- SASS DOC / JS DOC 주석이 있는 파일  
- (1)~(5)번 순서로 빠른 설치 가능

## 설치 준비  

1. `mkdir documentation`: jsdoc 관리용 폴더 생성  (1)
2. `cd documentation ` (2)
3. `npm init -y`: package.json 생성  (3)

## 전역/지역 개발 모듈 (node_modules)설치    

- 전역 설치  

`npm install --global jsdoc`: JSDOC 전역 설치  

`npm install --global sassdoc`: SASSDOC 전역 설치  

`npm install --global jsdoc sassdoc`: 둘 다 전역 설치

- 지역 설치  

`npm install --save-dev jsdoc`: JSDOC 지역 설치  

`npm install --save-dev sassdoc`: SASSDOC 지역 설치  

`npm install --save-dev jsdoc sassdoc`: 둘다 지역 설치 (4)

전역 / 지역 설치를 완료하면 node_moduels 디렉토리가 생성된다.  

##  JSDOC website 생성

- `node_modules\.bin\jsdoc doc-file.js`: doc-file.js 파일 내에서 jsdoc 형식으로 작성된 주석을 out 디렉토리에 .html파일을 생성해준다. (5)
- `node_modules\.bin\jsdoc doc-file.js -d path`: `-d`명령어를 사용하여 원하는 path에 .html 파일을 만들어 줄 수도 있다.  

생성된 폴더의 index.html에 JSDOC 사이트가 완성되어 있다.

## minami 테마 설치

1. `npm install --save-dev minami`: documemtation 디렉토리에 설치 후 테마를 지정할 js 파일과 minami 테마가 설치된 경로를 지정하여 설치한다. 
   - 전역 설치 된 경우: `jsdoc doc-file.js -t path\to\minami`  
   - 지역 설치 된 경우 `node_modules\.bin\jsdoc doc-file.js -t path\to\minami`   
2. `package.json` 파일에 minami가 설치되어 있으면 정상적으로 설치 된 것


## 삭제

`rm -rf 디렉토리이름`

## github 공유

- 설치 된 디렉토리에서 `git init` 명령어로 관리를 시작하고
- `vi .gitignore`: vim 편집기로 .gitignore 파일에 git으로 관리하지 않을 파일명 작성 후 저장. (e.g. node_modules) 
- package.json 파일만 잘 관리해주면 된다.

## 팀원과 공유

- npm이 설치된 팀원에게 package.jason 파일을 보내주고
- github에 있는 doc을 팀원이 fork 한 후 해당 디렉토리에서 `npm i`명령어로  node_modules 설치하면 끝!
- package.json에서 내가 설정한 단축 명령어 사용가능








