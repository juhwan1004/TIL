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

**1단계**

- **Branch란? **

  >  여러 사함이 동일한 소스코드를 기반으로 서로 다른 작업을 할 땐 개발자 마다 각각 다른 버전의 코드가 만들어 질 수 밖에 없다. 이럴 경우 동시에 다양한 작업을 할 수 있게 만들어 주는 기능이 바로 'Branch'이다. 각자 독립적인 작업 영역(repo) 안에서 마음대로 소스코드를 변경할 수 있다. 이렇게 분리된 작업 영역에서 변경된 내용은 나중에 원래 버전과 비교해서 하나의 새로운 버전으로 만들어 낼 수 있다. 각각의 브랜치는 다른 브랜치의 영향을 받지 않는다.
  >
  >  또한 이렇게 만들어진 브랜치들은 다른 브랜치와 Merge함으로써, 작업한 내용을 다시 새로운 하나의 브랜치로 모을 수 있다.
  >
  >  여럿이 동시에 작업을 할 때엔 다른 사람의 작업에 영향을 주거나 받지 않도록, 먼저 메인 브랜치에서 자신의 작업 전용 브랜치를 만든다. 그리고 각자 작업을 진행한 후, 작업이 끝난 사람은 메인 브랜치에 자신의 브랜치의 변경 사항을 적용한다. 이렇게 함으로써 다른 사람의 작업에 영향을 받지 않고 독립적으로 특정 작업을 수행하고 그 결과를 하나로 모아 나가게 된다. 이러한 방식으로 작업할 경우 '작업 단위' 즉 브랜치로 그 작업의 기록을 중간 중간에 남기게 되므로 문제가 발생했을 경우 원인이 되는 작업을 찾아내거나 그에 따른 대책을 세우기 쉬워진다.

- **master branch**

  >  Repository를 처음 만들면, Git은 바로 'master'라는 이름의 브랜치를 만들어 둔다. 이 새로운 저장소에 새로운 파일을 추가 한다거나 추가한 파일의 내용을 변경하여 그 내용을 Commit하는 것은 모두 'master'라는 이름의 브랜치를 통해 처리할 수 있는 일이 된다.
  >
  >  'master'가 아닌 또 다른 새로운 브랜치를 만들어서 '이제부터 이 브랜치를 사용할거야!'라고 선언(Checkout)하지 않는 이상, 이 때의 모든 작업은 'master' 브랜치에서 이루어 진다. 

- **브랜치 만들기**

  >  Git 에서는 작업에 따라 자유롭게 브랜치를 만들 수 있다. 그러나 효과적인 관리를 위해 함께 작업할 팀원들과 브랜치의 '이름은 어떤 규칙'으로 지을 것인지 또는 '어떤 상황에서 브랜치를 만들 지', 어느 시점에 통합할 것인지 등등의 팀간의 규칙을 정하는 것이 좋다.

- **Integration Branch(통합 브랜치)**

  >  Integration Branch란 언제든지 배포할 수 있는 버전을 만들 수 있어야 하는 브랜치다. 때문에 늘 안정적인 상태를 유지하는 것이 중요하다. '안정적인 상태'란 현재 작업 중인 소스코드가 모바일에서 동작하는 어플리케이션을 개발하기 위한 것이라면, '해당 어플리케이션의 모든 기능이 정상적으로 동작하는 상태'를 의미한다.

- **Topic Branch(토픽 브랜치)**

  >  Topic Branch란, 기능 추가나 버그 수정과 같은 단위 작업을 위한 브랜치다. 여러 개의 작업을 동시에 진행할 때는, 그 수만큼 토픽 브랜치를 생성할 수 있다.
  >
  >  토픽 브랜치는 보통 Integration Branch로부터 만들어 내며, 토픽 브랜치에서 특정 작업이 완료되면 다시 통합 브랜치에 Merge하는 방식으로 진행된다.  이러한 토픽 브랜치는 'Feature branch(피쳐 브랜치)' 라고 부르기도 한다.

- **브랜치 전환하기**

  >  Git 에서는 항상 작업할 branch를 미리 선택해야 한다. 처음에 Git을 설치하게 되면 'master'브랜치가 선택되어 있다. 현재 선택된 브랜치가 아닌 다른 브랜치에서 작업하고 싶을 때는, 'checkout' 명령어를 실행하여 원하는 브랜치로 전환할 수 있다. 체크아웃을 실행하면, 우선 브랜치 안에 있는 마지막 commit 내용이 작업 트리에 펼쳐집니다. 브랜치가 전환 되어있으므로 이후에 실행한 commit은 전환한 브랜치에 추가된다. 

- **HEAD**

  > 'HEAD' 란 현재 사용 중인 브랜치의 선두 부분을 나타내는 이름이다. 기본적으로는 'master'의 선두 부분을 나타낸다. 'HEAD' 를 이동하면, 사용하는 브랜치가 변경된다.
  >
  > Tips: Commit을 지정할 때, '~(틸드, 물결기호)'와 '^(캐럿, 삽입기호)'을 사용하여 현재 commit으로부터 특정 commit의 위치를 가리킬 수 있다. 이 때 자주 사용하는 것이 'HEAD'로써, '~(틸드)'와 숫자를 'HEAD'뒤에 붙여 몇 세대 앞의 commit을 가리킬 수 있다. '^(캐럿)'은, 브랜치 병합에서 원본이 여럿 있는 경우 몇 번째 원본인지를 지정할 수 있습니다. ![틸드(물결기호)와 캐럿(삽입기호)을 이용 중인 커밋으로부터의 상대적인 위치 지정](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_3_2.png)

- **stash**

  >  Commit하지 않은 변경 내용이나 새롭게 추가한 파일이 인덱스와 작업 트리에 남아 있는 채로 다른 브랜치로 체크아웃하면, 그 변경 내용은 기본 브랜치가 아닌 전환된 브랜치에서 commit할 수 있다. 
  >
  >  단, commit 가능한 변경 내용 중에 전환된 브랜치에서도 한 차례 변경이 되어 있는 경우에는 체크아웃에 실패 할 수 있다. 이 경우 이전 브랜치에서 commit하지 않은 변경 내용을 먼저 commit하거나, stash를 이용해 일시적으로 변경 내용을 다른 곳에 저장하여 충돌을 피하게 한 뒤 체크아웃을 해야 한다. 
  >
  >  **stash** 란, 파일의 변경 내용을 일시적으로 기록해두는 영역이다. stash를 사용하여 작업 트리와 인덱스 내에서 아직 commit하지 않은 변경을 일시적으로 저장해 둘 수 있습니다.  이 stash에 저장된 변경 내용은 나중에 다시 불러와 원래의 브랜치나 다른 브랜치에 commit할 수 있다. 

  ![stash](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_3_3.png)

- **브랜치 통합하기**

  >  작업이 완료된 Topic branch는 최종적으로 Integration branch에 Merge된다. branch 통합에는 merge를 사용하는 방법과 'rebase'를 사용하는 방법의 2가지 종류가 있다. 어느 쪽을 사용하느냐에 따라 통합 후의 브랜치의 이력이 크게 달라진다.
  >
  > - merge
  >
  >   >  merge를 사용하면, 여러 개의 브랜치를 하나로 모을 수 있다.
  >   >
  >   > 예를 들어, 아래 그림과 같이 'master' 브랜치에서 분기하는 'bugfix'라는 브랜치가 있다고 가정해 보자.
  >   >
  >   > ![브랜치](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_1.png)
  >   >
  >   >  이 'bugfix' 브랜치를 'master' 브랜치로 병합할 때, 'master' 브랜치의 상태가 이전부터 변경되어 있지만 않으면 매우 쉽게 병합할 수 있다. 'bugfix' 브랜치의 이력은 'master' 브랜치의 이력을 모두 포함하고 있기 때문에, 'master' 브랜치는 단순히 이동하기만 해도 'bugfix' 브랜치의 내용을 적용할 수 있다. 또한 이 같은 병합은 '**fast-forward**(빨리 감기) 병합'이라고 부른다.
  >   >
  >   > ![fast-forward(빨리감기) 병합](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_2.png)
  >   >
  >   >  하지만 'bugfix' 브랜치를 분기한 이후에 'master' 브랜치에 여러 가지 변경 사항이 적용되는 경우도 있다. 이 경우에는 'master' 브랜치 내의 변경 내용과 'bugfix' 브랜치 내의 변경 내용을 하나로 통합할 필요가 있다.
  >   >
  >   > ![브랜치 분기 후 'master'에 변경 사항이 생긴 경우](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_3.png)
  >   >
  >   >  따라서 양쪽의 변경을 가져온 'merge commit(병합 커밋)'을 실행하게 된다. 병합 완료 후, 통합 브랜치인 'master' 브랜치로 통합된 이력이 아래 그림과 같이 생기게 된다.
  >   >
  >   > ![양쪽의 변경을 적용한 'merge commit(병합 커밋)'](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_4.png)
  >   >
  >   > **Tips**: 병합 실행 시에 'fast-forward 병합'이 가능한 경우라도 '**non fast-forward 병합**' 옵션을 지정하여 아래 그림과 같이 만들어 낼 수도 있다.
  >   >
  >   > ![non fast-forward 병합](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_5.png)
  >   >
  >   > 'non fast-forward 병합'을 실행하면, 브랜치가 그대로 남기 때문에 그 브랜치로 실행한 작업 확인 및 브랜치 관리 면에서 더 유용할 수 있다.
  >
  > - rebase
  >
  >   >  위와 마찬가지로, 'master' 브랜치에서 분기하는 'bugfix' 브랜치가 있다고 가정한다.
  >   >
  >   > ![브랜치](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_6.png)
  >   >
  >   >  이제 rebase 를 이용해 어떻게 브랜치를 통합할 수 있는지 알아볼 차례다. 아래 그림과 같이 '**non fast-forward 병합**' 방식으로 진행되는 시나리오를 만들어 보자.
  >   >
  >   > ![rebase를 사용하여 브랜치 통합](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_7.png)
  >   >
  >   >  우선 'bugfix' 브랜치를 'master' **브랜치에 rebase 하면, 'bugfix' 브랜치의 이력이 'master' 브랜치 뒤로 이동하게 된다.** 그 때문에 그림과 같이 이력이 하나의 줄기로 이어지게 된다.
  >   >
  >   >  이 때 이동하는 커밋 X와 Y 내에 포함되는 내용이 'master'의 커밋된 버전들과 충돌하는 부분이 생길 수 있다. 그 때는 각각의 커밋에서 발생한 충돌 내용을 수정할 필요가 있다.
  >   >
  >   > ![rebase를 사용하여 브랜치 통합](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_8.png)
  >   >
  >   >  'rebase'만 하면 아래 그림에서와 같이, 'master'의 위치는 그대로 유지됩니다. 'master' 브랜치의 위치를 변경하기 위해서는 'master' 브랜치에서 'bugfix' 브랜치를 fast-foward(빨리감기) 병합 하면 됩니다.
  >   >
  >   > ![rebase를 사용하여 브랜치 통합](http://backlogtool.com/git-guide/kr/img/post/stepup/capture_stepup1_4_9.png)
  >   >
  >   > **Tips**: merge / rebase 특징
  >   >
  >   > - **merge**
  >   >   변경 내용의 이력이 모두 그대로 남아 있기 때문에 **이력이 복잡해짐.**
  >   > - **rebase**
  >   >   이력은 단순해지지만, 원래의 커밋 이력이 변경됨. **정확한 이력을 남겨야 할 필요가 있을 경우에는 사용하면 안됨.**
  >   >
  >   >  merge 와 rebase 는 팀 운용 방침에 따라 구별해 쓸 수 있다. 
  >   > 예를 들어 이력을 하나로 모두 모아서 처리하도록 운용한다고 치면 아래와 같이 구별해 사용할 수 있습니다.
  >   >
  >   > - 토픽 브랜치에 통합 브랜치의 최신 코드를 적용할 경우에는 rebase 를 사용,
  >   > - 통합 브랜치에 토픽 브랜치를 불러올 경우에는 우선 rebase 를 한 후 merge

- **토픽 브랜치와 통합 브랜치에서의 작업 흐름 파악하기**

  > 추후 추가.

[참조: 누구나 쉽게 이해할 수 있는 Git 입문](http://backlogtool.com/git-guide/kr/)

