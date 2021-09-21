# Javscript와 ES6+

자바스크립트(Javascript)는 일급 함수(함수를 다른 변수와 동일하게 다루는 언어)를 지원하는 언어이다. 또한 동적 언어이며 HTML과 CSS와 함께 웹에서 가장 굴직한 줄기를 차지하고 있다. 참고로 Java와는 전혀 다른 언어이다. 그런데 자바스크립트를 공부하다보면 ECMAScript, ES6, ES6+, ES7 … 등의 말을 보게 된다. ES는 ECMAScript의 줄임말이며 뒤에는 버전이라고 생각하시면 된다. ECMAScript는 자바스크립트의 표준이며 현재도 계속 ECMA International 표준화 기구에 의해 버전이 업데이트 되고 있다. 그리고 ECMAScript2015를 ES6라고 하며, ES6 이후 버전을 통칭하여 “ES6+” 라고 한다. 

<br>

### 특징

#### 1. let, const
- ES5 : 변수 var는 전역범위로 선언했으며, 호이스팅이 발생하고, 재선언, 재할당 가능하다.
- 호이스팅 (hoisting) : 자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언한다.
- ES6+ : 변수 let, const를 사용할 수 있다. 
  - 호이스팅이 안 되고, 재선언 불가능하고, 지역범위로 선언한다.
  - let은 재할당 가능, const는 재할당 불가능하다.

<br>

```
var apple = 1
var apple = 2
console.log(apple) // 2

let orange = 1
let orange = 2 // error
orange = 3
console.log(orange) // 3

const banana = 1
const banana = 2 // error
banana = 3 // error
console.log(banana) // 1
```

<br>

#### 2. Spread/Rest 문법

- Spread 문법 : 주로 배열을 풀어서 인자로 전달하거나, 배열을 풀어서 각각의 요소로 넣을 때에 사용합니다.
- Rest 문법 : 파라미터를 배열의 형태로 받아서 사용할 수 있습니다. 파라미터 개수가 가변적일 때 유용합니다.

<br>


```
// Spread 문법 예시
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2]; // [0, 1, 2, 3, 4, 5]


// Rest 문법 예시
const [a, b, ...rest1] = [10, 20, 30, 40, 50];
console.log(rest1) // [30, 40, 50]

const {c, d, ...rest2} = {c: 10, d: 20, e: 30, f: 40}
console.log(rest2) // {e: 30, f: 40}
```

<br>


#### 3. 구조 분해 (Destructuring)
- Spread 문법을 이용하여 값을 해체한 후, 개별 값을 변수에 새로 할당하는 과정이다.

<br>

```
const [a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2


const [c, d] = [1];
console.log(c); // 1
console.log(d); // undefined

const [e=5, f=7] = [1];
console.log(e); // 1
console.log(f); // 7
```

<br>

#### 4. 템플릿 문자열 (Template literals)
- 내장된 표현식을 허용하는 문자열 리터럴로, 여러 줄로 이뤄진 문자열과 문자 보간기능을 사용할 수 있다.
- 보간 : 변수 의 함수의 형태는 알 수 없으나 몇 가지 에 대한 함숫값 가 알려져 있을 때 그 사이의 임의의 에 대한 함숫값을 추정하는 것이다.

<br>

```
// ES5
var a = 5;
var b = 10;
console.log("Fifteen is " + (a + b) + " and\nnot " + (2 * a + b) + ".");
// "Fifteen is 15 and
// not 20."

// ES6+
var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and
not ${2 * a + b}.`);
// "Fifteen is 15 and
// not 20."
```

<br>

#### 5. 화살표 함수 (Arrow Function)
- ES5 : 함수 선언식, 함수 표현식
- ES6+ : 화살표 함수(in 함수 표현식)

<br>


```
// 함수 선언식
function getSum (a, b) {
  let sum = a + b
  return sum
}

// 함수 표현식
let getSum = function (a, b) {
  let sum = a + b
  return sum
}

// 화살표 함수1 (in 함수 표현식)
let getSum = (a, b) => {
  let sum = a + b
  return sum
}

// 화살표 함수2 (in 함수 표현식)
let getSum = (a, b) => a + b
```

<br>

#### 6. 함수 매개변수 (Function Parameter)
- 함수의 매개변수를 통해서 다양한 초기화가 가능하다.

<br>

```
// Default
const f = (x, y=10) => x + y;
f(1);	// 11
f(10, 5);	// 15

// Rest
const f = (x, ...y) => x * y.length;
f(10, 2, 3, 4, 5); // 10 * 4 = 40
f(10, 2); // 10 * 1 = 10

// Spread
const f = (x, y, z) => x + y + z;
const arr = [10, 20, 30];
f(...arr); // 10 + 20 + 30 = 60
f(...[1, 2, 3]); // 6
```

<br>

#### 7. for ... of 
- ES5 : for ... in 구문은 object의 key 값으로 반복한다.
- ES6+ : for ... of 구문은 배열에 대한 값을 출력한다.

<br>

```
// for ... in
for (var k in {a: 1, b: 2}) { console.log(k) } // a, b
for (var k in [10, 20, 30]) { console.log(k) } // 0, 1, 2

// for ... of
for (const v of [10, 20, 30]) { console.log(v) } // 10, 20, 30
```

<br>

#### 8. Object 할당 
- object에 값을 할당할 시, key의 name과 value의 variable name이 같을 경우, 생략이 가능하다.

<br>

```
// ES5
var a = 10, b = 20, c = 30;
var obj = { a: a, b: b, c: c};

// ES6+
const a = 10, b = 20, c = 30;
const obj = {a, b, c};
```

<br>

#### 9. Class 문법 
- 객체를 생성하기 위한 템플릿이다.
- Class body 안의 메서드나 constructor(클래스 안에 한 개만 존재하는 생성자)와 같은 Class 멤버를 정의한다.
- 상속을 지원하고 정적 메서드를 사용할 수 있다.

<br>

```
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Getter
  get area() {
    return this.calcArea();
  }
  // 메서드
  calcArea() {
    return this.height * this.width;
  }
}

const square = new Rectangle(10, 10);

console.log(square.area); // 100
```

<br>

#### 주의사항  

ES6+ spec은 모든 브라우저에서 지원 하는 것이 아닌, 일부 브라우저(chrome, firefox 등)에서 지원한다. 그래서 ES6 spec으로 작성한 문서를 babel이라는 도구를 통해서 ES5 spec으로 변환하여 사용해야 한다.

<br>

### 참고자료

- [신선함으로 다가온 ES6 경험](https://techblog.woowahan.com/2554/)
- [[javascript] ES6+ 기초 문법](http://junil-hwang.com/blog/javascript-es6-spec/)
- [[초보를 위한 자바스크립트] ES6? ES6+가 모지?](https://okky.kr/article/620045)
