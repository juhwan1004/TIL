# 변수선언과 기본 타입
- 점진적 타입 검사(gradually type checking): 컴파일 시 type checking
- TS primitive types  
string, number, boolean, symbol(프로그램 전체에서 유일한 값), enum, 문자열 리터럴

- TS는 문자열에 큰따옴표("")사용을 권장함.

- TS에서 지원하는 객체타입 종류  
Array, Tuple, Function, 생성자, Class, Interface
- Tuple: 배열요소가 n개로 정해질 때 각 요소별로 타입을 지정한 타입.
- enum: 객체타입, number 하위타입, 컴파일 시간에 평가됨. 
named numeric constants(명명된 숫자 상수)의 집합을 정의할 때 사용
e.g.) enum Day {속성: 값, 속성: 값 ...}  
관련된 변수들을 모아서 사용하기 좋은듯..  
e.g.) enum WeekDay {Mon, Tue, Wed, Thu}

- TS에서 배열은 2가지 타입을 가진다
배열 타입 (array type): let myVar: number[] = [1,2,3,4,5];  
제네릭 배열 타입 (generic array type): let num:Array<number> = [1,2,3];  

- Tuple 타입  
튜플에 선언된 타입 수와 할당될 배열의 요소 수가 정확히 일치해야한다.  
e.g.) let x: [string, number] = ["tuple01", 100];

참고서적: 타입스크립트 퀵스타트
