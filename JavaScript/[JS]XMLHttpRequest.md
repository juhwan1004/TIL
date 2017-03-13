# XMLHttpRequest

자바스크립트에서 HTTP 요청을 생성하는 특별한 객체(생성자 함수)로, 현재 대부분의 브라우저에서 사용 가능하다.

HTTP 요청을 만드는 과정은 3단계로 이뤄진다.

1. XMLHttpRequest 객체(xhr)를 설정한다. 

   `var xhr = new XMLHttpRequest();`

2. readystatechange 이벤트에 대한 콜백 함수를 지정한다.

   `xhr.onreadystatechange = handleResponse;`

3. open()과 send() 메서드를 사용해 요청을 보낸다.

   GET: 빈 문자열을 인자로 전달

   POST: 데이터를 인자로 전달

   `xhr.open("HTTP 요청 방식", "URL", 비동기 여부);` 

   비동기 방식인 경우 응답을 기다리는 동안 브라우저가 중단되지 않는다.

   더 나은 사용자 경험을 제공하기 위해 true 사용(false: 동기 방식, 기본 값이 true이며 생략 가능하다)

   `xhr.open("GET", "page.html", true);`

   `xhr.send();`

   ​

