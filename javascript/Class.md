# Class

ES6에 추가된 class는 객체를 생성하기 위한 템플릿이다. 연관있는 데이터를 묶어 놓는 것(캡슐화)으로 property인 속성 field(ex, 나이, 이름...)와 function인 행동 method(ex, 말하다, 걷다...)가 있다. (fields만 있는 것을 Data class라고 한다.) 그리고 class를 이용해 상속과 다양성이 이뤄지는 등 객체지향적이다.

ES5에는 class로 템플릿을 만들지 않고, 바로 object를 만들었으며 function으로 틀을 만들었다.

<br>

### 1. Class 선언

class body안에는 하나의 contructor(생성자)이 있고 그 안에 field를 정의한다.   
그 외에 speak와 같이 method가 여러개 있다.

```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  speak() {
    console.log(`${this.name}, hello!`};
  }
}

const jongah = new Person('jongah', 20);
console.log(jongah.name); // 'jongah'
console.log(jongah.age); // 20
jongah.speak(); // jongah, hello!
```

<br>

### 2. Getter and setters

잘못된 값이 들어왔을 때, 변경해줄 수 있다.
get 키워드를 이용해 값을 리턴하고 set 키워드를 이용해서 값을 설정할 수 있다.
set은 값을 설정하기 때문에 value를 받아와야 한다.

```
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  get age() {
    return this._age;
  }
  
  set age(value) {
    this._age = value < 0 ? 0 : value;
  }
}

const user1 = new User('jongah', -1);
console.log(user1.age); // 0
```

<br>

### 3. Fields (public, private)

보안을 위해 은닉화하고 싶은 데이터는 #(해시)를 사용하여 접근이 불가능하게 한다.

```
class Secret {
  publicField = 2;
  #privateField = 0;
}

const secret = new Secret();
console.log(secret.publicField); // 2
console.log(secret.privateField); // undefined
```
<br>

### 4. Static properties and methods

static은 object와 상관없이 class 자체에 연결되어 있다.   
메모리의 사용을 줄여줄 수 있다.

```
class Article {
  static publisher = 'jongah';
  constructor(articleNumber) {
    this.articleNumber = articleNumver;
  }
  
  static printPublisher() {
    console.log(Article.publisher);
  }
}

const article1 = new Article(1);
console.log(article1.publisher) // undefined
console.log(Article.publisher) // 'jongah'
Article.printPublisher(); // 'jongah'
```
<br>

### 5. 상속

extends로 상속받을 수 있고, 상속받은 내용을 변경(다양성)할 수 있다.   
super을 통해 상속받은 내용도 같이 보여줄 수 있다.

```
class Shape {
  constructor(width, height, color) {
    this.width = width;
    this.height = height;
    this.color = color;
  }
  
  draw() {
    console.log(`drawing ${this.color} color!`);
  }
  
  getArea() {
    return this.width * this.height;
  }
}

class Rectagle extends Shape {}
class Triangle extends Shape {
  draw() {
    super.draw();
    console.log('change');
  }

  getArea() {
    return (this.width * this.height) / 2;
  }
}

const rectangle = new Rectangle(20, 20, 'blue);
retangle.draq(); // 'drawing blue color!'
console.log(rectangle.getArea()); // 400

const triangle = new Triangle(20, 20, 'red');
triangle.draw(); // 'drawing red color!' 'change'
console.log(triangle.getArea()); // 200
```

<br>

### 6. instanceof 

상속 받은 것인지 아닌 지 boolean 값으로 확인한다.

```
console.log(rectangle instanceof Rectangle); // true
console.log(triangle instanceof Rectangle); // false
console.log(triangle instanceof Shape); // true
consoloe.log(triangle instanceof Object); // true
```

<br>

### 참고자료

- [클래스와 오브젝트의 차이점, 객체지향 언어 클래스 정리](https://youtu.be/_DLhUBWsRtw)
- [Class vs Factory Function, 더 나은 선택은?](https://urbanbase.github.io/dev/2021/03/28/ECMAScript6.html)
- [Classes MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)
