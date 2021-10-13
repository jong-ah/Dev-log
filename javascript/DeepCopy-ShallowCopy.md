# Deep copy vs Shallow copy


### 깊은 복사(Deep Copy)
- 깊은 복사(Deep Copy)는 값 자체를 복사하는 것입니다. 이 복사는 number, string, boolean, null, undefined와 같이 원시타입에서 볼 수 있습니다. (두 개의 화분에 하나씩 꽃이 있는 느낌)

```
let num = 10, numCopy = num;

console.log(numCopy); // 10

num = 20;

console.log(numCopy); // 10 => 원본이 변해도 복사본의 값이 변하지 않는다.
```

<br>

### 얕은 복사(Shallow copy)
- 얕은 복사(Shallow copy)는 참조(주소)값을 복사하는 것입니다. 이 복사는 원시타입을 제외한 object, array, function과 같이 참조 타입에서 볼 수 있습니다. 

```
const obj = { key : val };
const objCopy = obj;

console.log(objCopy.key); // val

obj.key = value;

console.log(objCopy.key); // value => 같은 주소값을 사용하기 때문에 원본이 변하면 복사본도 변한다.
```

<br>

### 객체가 깊은 복사하는 방법
```
// 1. Object.assign()
const obj1 = { a : 1 };
const obj2 = Object.assign({}, obj1);

// 2. 전개 연산자(Spread Operator)
const obj3 = { b : 2 };
const obj4 = {... obj3};

// 3. JSON 객체 메소드 
const obj5 = { c : 3 };
const obj6 = JSON.parse(JSON.stringify(obj5));

// 4. 커스텀 재귀 함수
function deepCopy(obj) {
  if (obj === null || typeof obj !== "object") {
    return obj;
  }

  let copy = {};
  for (let key in obj) {
    copy[key] = deepCopy(obj[key]);
  }
  return copy;
}

const obj7 = { d : 4 };
const obj8 = deepCopy(obj7);

// 5. lodash 모듈의 cloneDeep()
// npm i lodash
 
const lodash = require("lodash");

const obj9 = { e : 5 };
const obj10 = lodash.cloneDeep(obj9);
```

1,2번의 경우 중복 객체는 깊은 복사가 이뤄지지 않습니다.  
3번은 성능이 느리고, 함수는 undefined 처리합니다.  
4번과 같이 커스텀할 수 있고, 5번과 같이 오픈소스를 활용할 수도 있습니다.  

<br>

### 참고자료

- [얕은 복사(Shallow Copy)와 깊은 복사(Deep Copy)](https://velog.io/@recordboy/JavaScript-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%ACShallow-Copy%EC%99%80-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%ACDeep-Copy)
- [얕은 복사, 깊은 복사 간단히 살펴보기](https://hasudoki.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%AC-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%AC-%EA%B0%84%EB%8B%A8%ED%9E%88-%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0Learn-Deep-Shallow-Copy-with-Tricky-JavaScript-Questions)
- [[개발상식] lodash 알고 쓰자](https://velog.io/@kysung95/%EC%A7%A4%EB%A7%89%EA%B8%80-lodash-%EC%95%8C%EA%B3%A0-%EC%93%B0%EC%9E%90)
