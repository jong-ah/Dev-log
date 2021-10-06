# javascript 의 null, undefined, undeclared 차이점

<br>

| 차이점 | 선언 | 할당 | 타입  |
| -------------- | -- | -- | -- |
| **null**       | ⭕ | ⭕ | ⭕ |
| **undefined**  | ⭕ | ❌ | ❌ |
| **undeclared** | ❌ | ❌ | ❌ | 

<br>

### null (빈값 할당)
- 저는 useState에서 숫자 값을 할당받기 전에 null을 초깃값으로 넣어두거나, 로그인 하기 전에 화면이 보여지지 않기 위해 null을 썼습니다. 

```
let n = null;
console.log(n);	// null
console.log(typeof n);	// object

console.log(undefined == null); //true 
console.log(undefined === null); //false
```

<br>

### undefined (미할당)
- 저는 찾고자 하는 정보가 undefined로 할당받지 못한 상태인지 아닌지 여부에 따라 로그인 여부를 판단하는데 사용했습니다.

```
let u;
console.log(f);	// undefined
console.log(typeof f);	// undefined
```

<br>

### undeclared (미선언)
- 프로젝트 작업하면서는 기능에 맞는 변수명 처리와 필요한 변수 사용만을 위해 주의했기 때문에 undeclared 오류를 발견하지 않았습니다.

```
console.log(c);	// Uncaught ReferenceError: c is not defined at <anonymous>:1:13
```

<br>

### 참고자료

- [undefined vs undeclared vs null의 차이점](https://sudo-heedongdev.tistory.com/6)
