# Event Bubbling / Capturing

### 이벤트 버블링(Event Bubbling)

- target > ... > body > html
- 기본적으로 버블링으로 설정되어 있다.

![Screenshot from 2021-10-19 23-55-35](https://user-images.githubusercontent.com/81145387/137937780-7cf23274-2ab6-45dd-af18-ec84d29a5da4.png)

<br>

### 이벤트 캡처링(Event Capturing)

```
target.addEventListener(type, listener[, useCapture]);
```
- html > body > ... > target
- addEventListner()의 세 번째 인자로 캡처링 여부를 결정한다.

![Screenshot from 2021-10-19 23-55-30](https://user-images.githubusercontent.com/81145387/137937883-f62f38da-4073-4125-aa9f-5b2266693704.png)

<br>

### 이벤트 전파 막기

```
pinkDiv.addEventListener('click', function(e) {
  e.stopPropagation()
  console.log('pink div')
})

```

- e.stopPropagation()로 이벤트 전파를 막는다.

![Screenshot from 2021-10-19 23-58-12](https://user-images.githubusercontent.com/81145387/137938009-9de7b6ed-2a36-4fc1-8a62-f3222fca4610.png)

<br>

### 참고자료

- [이벤트 캡쳐링과 버블링 알아보기](https://www.howdy-mj.me/dom/event-capturing-and-bubbling/)
