# 자바스크립트 Prototype

자바스크립트는 프로토타입 기반 언어라고 불립니다. 모든 객체들이 메소드와 속성들을 상속 받기 위한 템플릿으로써 프로토타입 객체(prototype object)를 가지기 때문입니다. 예시를 들어 속성과 메소드가 어떻게 상속받는지 알려드리겠습니다.

<br>

```
function Person() {
  this.eyes = 2;
  this.nose = 1;
}

// kim은 프로토타입을 Person(함수)으로 가지는 오브젝트이다.
const kim = new Person();

console.log(kim.eyes); // => 2
console.log(kim.nose); // => 1
console.log(kim.mouth); // => undefined
```

Person()이라는 prototype object를 만들었습니다.   

kim은 new를 활용해 Person을 상속받고, 그러므로 kim에는 없지만 상위 프로토타입인 Person에 있는 eyes와 nose 속성을 사용할 수 있습니다. 상위에도 없는 속성은 undefined를 출력합니다. (이렇게  자신에게 없는 속성을 상위 프로토타입에 상속받는 것을 프로토타입 체인이라고 합니다.)

<br>

```
Person.prototype.eat = function(){ return `I eat ${this.foods  ?  this.foods + this.food : this.food}`};
kim.food = `milk`;

// park은 프로토타입을 kim(변수)으로 가지는 오브젝트이다.
const park = Object.create(kim);

park.foods = `choco`

console.log(kim.eat()); // => I eat milk
console.log(park.eat()); // => I eat chocomilk

// lee은 프로토타입을 Person(함수)으로 가지는 오브젝트이다.
const lee = new Person();

console.log(lee.eat()); // => I eat undefined
```
다음은 메소드 상속을 알아보기 위해 Person에 새로운 메소드, kim에는 새로운 속성을 추가하였습니다.   
kim을 프로토타입으로 가지는 park도 만들었습니다.   

park은 자신이 가진 속성과 kim의 속성과 Person의 메소드를 활용하였습니다.   
그렇기에 같은 메소도를 상속받았더라도 kim과는 다른 결과를 출력합니다.   

lee는 Person을 상속받았지만 Person에는 food 속성값이 없기 때문에 I eat undefined를 출력합니다.   
이처럼 Person의 eat()메소드가 하위 프로토타입에 영향을 주는 것(상속)을 확인할 수 있습니다.

#### 이와 같이 자바스크립트는 프로토타입을 활용하여 eat()이라는 하나의 메소드를 모두 사용할 수 있고, kim, park의 food처럼 다른 속성값을 가질 수 있습니다. 저의 경우, 다른 매개변수를 받지만 동일한 메소드를 활용하여 다른 결과를 보여주는 검색 기능에서 활용했습니다.

<br>

* Prototype vs Class
다른 언어(Java, pythone 등)에서 사용했던 개념인 class를 자바스크립트에서 class 문법이라고 추가하기 이전부터 class처럼 prototype으로 객체지향 언어로 상속 받을 수 있습니다. (prototype에선 new()와 create()를 활용해서 상속받습니다.) (class문법이 추가된 것이지 자바스크립트가 클래스 기반으로 바뀌었다는 것은 아닙니다.)


<br>

### 참고자료

- [Object prototypes MDN](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes)
- [[Javascript ] 프로토타입 이해하기](https://medium.com/@bluesh55/javascript-prototype-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-f8e67c286b67)
