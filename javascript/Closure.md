# 클로저 (Closure)

- 함수와 함수가 선언된 어휘적(lexical) 환경의 조합을 말한다. 이 환경은 클로저가 생성된 시점의 유효 범위 내에 있는 모든 지역 변수로 구성된다.
- **외부함수의 변수에 접근할 수 있는 내부함수**

<br>

### 어휘적 범위 지정(Lexical scoping)

어휘적 환경은 어휘적 범위(scope) 내에 있는 것을 말한다.   
아래 예시를 보면 function(z)안의 y가 선언되지 않았지만 밖에 선언된 y를 가져다 써서 재할당한 것을 확인할 수 있다.   
function(z)의 지역 범위 안에 없어 외부 범위에 있는 y를 가져다 쓴 것(스코프 체인)으로 서로 범위는 다르지만 내부는 외부 것을 가져다 쓸 수 있다는 것을 알 수 있다.
이것을 어휘적 범위가 다르다고 말하고, 어휘적 환경이 이를 통틀어 말한다.

<br>

클로저는 이 어휘적 환경을 함수 안에 만든다.   
var y = 1;이 makeAdder 함수 안에 선언되어 있고 내부 함수가 이를 활용한 것을 확인할 수 있다.   
add5와 add10은 makeAdder 함수의 어휘적 환경을 가져다 쓰며, 이를 클로저에 어휘적 환경이 저장된다고 한다.   
add5(2)를 살펴보면, y는 함수 안에 선언(100)되어 가져다 쓰고, x는 makeAdder 함수의 매개변수(5)로 있어 쓴다.   
z의 경우 할당된 게 없어 밖에서 밖으로 찾아나가 add5 함수의 매개변수(2)를 가져다 쓴다. 


<br>

```
function makeAdder(x) {
  var y = 1;
  return function(z) {
    y = 100;
    return x + y + z;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);
//클로저에 x와 y의 환경이 저장됨

console.log(add5(2));  // 107 (x:5 + y:100 + z:2)
console.log(add10(2)); // 112 (x:10 + y:100 + z:2)
//함수 실행 시 클로저에 저장된 x, y값에 접근하여 값을 계산
```  

<br>

### 클로저가 필요한 이유

- **전역변수를 줄일 수 있다.**  
  - 전역변수가 많으면 어디에서든지 실수로 접근할 수 있기 때문에 최대한 전역변수를 줄이는 것이 좋다.
- **모듈 패턴을 만들 수 있다.**
  - 어휘적 환경을 만들면 그것을 가져다 재사용할 수 있기 때문에 코드의 가독성이 좋아지고 자주 사용할 수 있다.
  - 자바와 몇몇 언어들은 프라이빗 메소드라고 제한적 접근만을 허용하여, 코드 관리를 잘하도록 하는 것이 있는데 자바스크립트는 클로저로 그 기능을 사용할 수 있다.  
  - 
클로저를 사용하여 객체지향 프로그래밍의 정보 은닉과 캡슐화 같은 이점들을 얻을 수 있다.

<br>

### 클로저의 실용적인 예시

- HTML 문자열 생성기

<br>

```
const tagMaker = tag => content => `<${tag}>${content}</${tag}>`

const divMaker = tagMaker('div');
divMaker('hello'); // '<div>hello</div>'

const anchorMaker = tagMaker('a');
anchorMaker('go'); // '<a>go</a>'
```

<br>

- 클로저 모듈 패턴

<br>

```
var makeCounter = function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  }
};

var counter1 = makeCounter();
var counter2 = makeCounter();
alert(counter1.value()); /* 0 */
counter1.increment();
counter1.increment();
alert(counter1.value()); /* 2 */
counter1.decrement();
alert(counter1.value()); /* 1 */
alert(counter2.value()); /* 0 */
```

<br>

### 주의할 점 : var

```
let funcArr =[]

for(var i = 0; i < 5; i++) {
 var c = i *2;
 funcArr.push( (_) => console.log(c))
}
funcArr.forEach( fn => fn() ) // 8,8,8,8,8
```

<br>

var은 블록스코프가 아니기 때문에 for문 밖에서도 접근이 가능하다. 그래서 마지막 값이 8만 나온다.   
var이 아닌, 블록스코프인 let, const를 쓰면 for문 안에서만 접근이 가능하기 때문에 문제가 생기지 않는다. 

<br>

```
let funcArr =[]

for(var i = 0; i < 5; i++) {
 let c = i *2;
 funcArr.push( (_) => console.log(c))
}
funcArr.forEach( fn => fn() ) // 0,2,4,6,8
```

<br>

### 참고자료

- [Clousure MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures)
- [[JS]클로져(closure)와 클로져의 사용 예제](https://velog.io/@proshy/JS%ED%81%B4%EB%A1%9C%EC%A0%B8closure%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%B8%EC%9D%98-%EC%82%AC%EC%9A%A9-%EC%98%88%EC%A0%9C)
- [Javascript - 나를 위한 클로저 예제 분석](https://pewww.tistory.com/21)
