# Promise 개념과 Callback 함수와의 차이점


### 자바스크립트의 비동기

Promise와 Callback 함수는 자바스크립트 비동기 처리에 사용된며 특정 로직이 끝났을 때 원하는 동작을 실행하게 한다는 공통점이 있습니다.

<br>

여기서 자바스크립트의 비동기 처리란 '특정 코드의 실행이 완료될 때까지 기다리지 않고 다음 코드를 먼저 수행하는 자바스크립트의 특성'을 의미합니다.   
예를 들어 a, b, c를 차례대로 출력하기로 코드를 입력했는데 그 중 b를 setTimeout으로 3초 뒤에 출력시킨다면 a,c,b 순으로 출력됩니다.   
이럴 때, a,b,c순으로 출력시키기 위해서 Promise와 Callback 함수를 사용합니다.   

<br>

### Promise 개념

- Promise는 'new Promise(), resolve(), then()와 같은 Promise API를 사용하고, 대기, 이행, 실패라는 3가지 상태가 있습니다.   
- 이행된다면 then으로 처리 결과를 받을 수 있고, 실패한다면 catch로 에러처리 할 수 있습니다.   

<br>

### Callback 함수와의 차이점

- Callback 함수는 Promise API같이 따로 처리할 수 있는게 없어 함수 안에 함수를 계속 넣어 연달아 실행시킵니다.
- 이럴 경우 Callback 지옥이라 불리는 형태로, 코드 가독성이 떨어지고 로직 변경하기가 어러워집니다

<br>

Promise는 Callback 함수처럼 함수 안에 함수를 넣는 것이 아닌 밖에 then으로 연달아 실행시킬 수 있게 하기 때문에 Callback 함수의 문제점을 해결합니다.

<br>

### 참고자료

- [Using promises MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Using_promises)
