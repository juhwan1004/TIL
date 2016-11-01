# 누구나 쉽게 이해할 수 있는 Git입문 

**1단계**

Q1. 처음 배울 때 알아할 기본적인 내용은 무엇인가?

- **Git 설치 / 초기 설정** 

- **새 저장소(로컬/원격) 만들기**

  >1. 새로운 저장소 만들기
  >2. 이미 생성된 Remote Repository를 Local Repository로 복사하기

  - Remote Repository: 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소입니다.

  - Local Repository: 내 PC에 파일이 저장되는 개인 전용 저장소입니다.

    ​

- **파일 Commit 하기**

  > 1. 파일 및 폴더의 추가/변경 사항을 Repository에 기록하기 위한 것
  > 2. 이전 Commit 상태부터 현재 상태까지의 변경 이력이 기록된 Commit(혹은 revision)이 만들어진다.
  > 3. Commit은 시간순으로 저장된다. 최근 Commit부터 거슬러 올라가면 과거 변경 이력과 내용을 알 수 있다.

  - 각 Commit에는 영문/숫자로 이루어진 40자리 고유 이름이 붙는다. 저장소에선 이 40자리 이름을 보고 각 커밋을 구분하고 선택한다.

    > Tips: 버그 수정, 기능 추가 등 특별한 의미가 있는 업데이트를 작업 별로 구분해서 각각 커밋하면, 나중에 이력을 보고 특정 변경 내용을 찾기 쉽다.

  - Commit은 이력을 남기는 중요한 작업이기 때문에 Commit 버튼을 누를 땐  Commit 메시지를 필수로 입력해야 한다. 메시지가 없으면 Commit이 실행되지 않는다.

    > Tips: 메시지는 명료하고 이해하기 쉽게 남겨야 본인 뿐만 아니라 다른 사람이 Commit 이력을 확인하기 쉽다. Git에서 권장하는 메시지 형식을 따르는 것도 좋다.
    >
    > 1번째 줄: Commit 내의 변경 내용을 요약
    >
    > 2번째 줄: 빈 칸
    >
    > 3번째 줄: 변경한 이유
    >
    > 주로 위 형식으로 메시지를 작성한다.

- **Work tree(작업 트리)와 Index(인덱스)**

  > Git에서는 우리가 흔히 말하는 폴더를 'Work tree(작업 트리)'라고 부른다. 그리고 Commit을 실행하기 전의 Repository와 Work tree사이에 존재하는 공간을 'Index'라고 한다.

  -  Git의 Commit 작업은 Work tree에 있는 변경 내용을 Repository에 바로 기록하는 것이 아니라 그 사이 공간인 Index에 파일 상태를 기록(stage -'' 스테이징 한다''고 표현하기도 함)하게 되어 있다. 따라서 Repository에 변경 사항을 기록하기 위해서는, 기록하고자 하는 모든 변경 사항들이 'Index'에 존재해야 한다.

     예를 들어, 10개의 파일을 수정했지만 그 중에 7개만 Repository에 공개하고 싶은 때를 생각해 보면, 변경한 10개의 파일 중 7개를 선택하는 작업이 바로 'Index에 등록' 또는 '스테이징(stage)'이라 표현하는 작업이다.

     이렇게 Index란 공간(가상의 공간)이  중간에 있는 덕분에 Work tree안에 있는 Commit이 필요 없는 파일들을 Commit에 포함하지 않을 수도 있고, 파일에서 내가 원하는 일부 변경 사항만 Index에 등록해 Commit할 수 있다.


- __Remote Repository에 Push 하기__

  > Remote Repository로 변경된 파일을 업로드하는 것을 Git에서는 Push라고 한다.  Push를 실행하면, Remote Repository에 내 변경 이력이 업로드되어 Remote Repository와 Local Repository가 동일한 상태가 된다.

- **Remote Repository에 Clone하기**

  > Clone이란 Remote Repository의 내용을 통재로 다운로드하는 것을 말합니다.  복제한 repo를 다른 PC에서 Local Repository로 사용할 수 있게 된다.
  >
  > Tips: 변경 이력도 함께 Local Repository에 복제되어 오므로, 원래 Remote Repository와 똑같이 이력을 참조하고 Commit을 진행할 수 있다.

- **Remote Repository에 Pull하기**

  > Remote Repository를 공유해 여러 사람이 함께 작업을 하면, 모두가 같은 Remote Repository에 Push한다. 그럼 다른 사람이 Remote Repository에 Push 변경 내용을 내 Local Repository에도 Pull할 필요가 있다.

- **변경 이력 Merge 하기**

  >  내가 끌어온 Repository가 최신 버전이 아닌 경우, 즉 내가 Pull을 실행한 후 다른 사람이 Push를 하여 Remote Repository를 업데이트 해버린 경우에는 내 Push 요청이 거부되어 버린다.
  >
  >  이런 경우 Merge 작업을 진행하여 다른 사람의 업데이트 이력을 내 Repository에도 갱신 해야한다. 만약 Merge하지 않은 채로 이력을 덮어쓰게 되면 다른 사람이 Push 한 업데이트 내역이 사라져 버리기 때문이다.

- **충돌 해결하기**

  > Merge 기능은 Git에서 변경한 부분을 자동으로 통합해 주는 기능이다. 그러나 경우에 따라 자동으로 Merge할 수 없는 경우도 있다.
  >
  >  바로 Remote Repository와 Local Repository 양쪽에서 파일의 동일한 부분을 변경한 경우이다. 이 경우 두 변경 내용 중 어느 쪽을 저장할 것인지 자동으로 판단 할 수 없기 때문에 충돌이 발생한다.
  >
  >  Git은 충돌이 발생한 파일 내용을 아래와 같이 표시한다.
  >
  > <<<<<<<<<<< // 충돌이 발생한 지점 표시
  >
  > Hello.
  >
  > ======= 
  >
  > // ''==='' 표시 위쪽이 Local repo, 아래쪽이 Remote repo의 변경 내용이다
  >
  > <strong>Hello</strong>
  >
  > \>>>>>>>>>>>
  >
  > 위와 같이 표시된 부분을 우리가 직접 수정 후 Commit 해야 한다.

Q2. 배워야 하는 범위는 어느 정도인가?

- chapter 4개 분량

Q3.80퍼센트 비중으로 사용하게 될 20퍼센트의 핵심 기술은 무엇인가?

- **Commit** / **Push** / **Pull** / **Clone** / **Merge** 
- **충돌 해결** 

[참조: 누구나 쉽게 이해할 수 있는 Git 입문](http://backlogtool.com/git-guide/kr/)

