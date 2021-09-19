# this

this의 값은 **함수를 호출한 방법에 의해 결정**된다. 실행중에는 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있다.

<br>

### 핵심 요약

- this는 일반적으로 window(Global)를 가르킨다.
- "use strict"(엄격모드)를 사용하면 this는 window가 아닌, undefined이다.
- Dot Notation으로 함수가 실행되면, this는 그 도트 앞에 써있는 객체 자체를 가리킨다. 
- call(), apply()를 사용해 매개변수를 넣으면 그 변수에 해당하는 값을 가르킨다. (명백한 바인딩 (Explicit Binding) / call, apply, bind)
- bind()를 호출하면 this를 값을 변경시킬 수 있으며, 한 번만 동작한다. (첫 번째 매개변수로 고정)
- 생성자 함수(new 키워드 사용한 함수)는 특이하게도 return문이 있음에도 불구하고 그 return문을 무시하고 this 객체를 return하는 특징이 있다. 그러나 생성자 함수도 리턴되는 대상이 객체라면 this객체 대신에 해당 객체가 리턴된다. (return < this < return object)


<br>

### this 제대로 이해했는 지 확인하는 예제


```
function programmer() {
this.isSmart = false;
this.upgrade = function (version) {
this.isSmart = !!version;
work();
}
}
function work() {
it (this.isSmart) {
window.alert('I can do my work! I am smart!');
}
}
var programmer = new programmer();
programmer.upgrade(1.1); 
```

<br>

위와 예제를 보면 alert이 실행될 것 같지만 실행되지 않는다. 함수 work는 실행되지만 그 안의 this.isSmart는 윈도우의 isSmart를 가르키는데 저 코드에서는 전역으로 준 것이 없어서 undefined로 alert이 실행되지 않는다.

<br>

```
function programmer() {
this.isSmart = false;
this.upgrade = function (version) {
this.isSmart = !!version;

var bindedwork = work.bind(programmer)
bindedwork();
}
}

function work() {
if (this.isSmart) {
window.alert('I can do my work! I am smart!');
}
}
var programmer = new programmer();
programmer.upgrade(1.1)
```

<br>

위와 같이 bind()로 명확하게 지정을 해줘야 alert창이 뜬다.

<br>


### 참고자료

- [This MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)
- [[JS/this] 자바스크립트, this의 4가지 역할](https://im-developer.tistory.com/96)
- [자바스크립트 this? 간단히 핵심만 파악하기](https://youtu.be/PAr92molMHU)
