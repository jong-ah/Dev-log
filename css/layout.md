# layout

layout을 만들 때 사용할 수 있는 속성인 총 4개가 있다.    
레거시 방법으로 Position, Float가 있고, 현대적인 방법으로 Flexbox, Grids가 있다.    
Grids로 전체를, Flexbox로 요소로 적용해 사용하기도 한다.   
그러나 현대적인 방법을 일부 브라우저에선 적용 안 된다. 

<br>

### 1. Position

- 문서 상에 요소를 배치하는 방법을 지정한다. 

```
position: static; // 기본, 아무 설정 안 한 상태
position: relative; // 기본(static)을 기준으로 이동한다. 나의 경우, 주로 absolute의 부모요소(기준)로 사용했다.
position: absolute; // body 혹은 부모를 기준으로 위치한다.
position: fixed; // 따로 위치를 지정하지 않으면 스크롤 상관없이 기본 고정
position: sticky // 따로 위치를 지정하지 않으면 abolute와 같이 위로 쭉 올라가고 top:0으로 하면 해당 위치에서 고정
```

![css](https://user-images.githubusercontent.com/81145387/139180457-38734620-f5f0-4e78-b3da-fe725905e17a.gif)

<br>

### 2. Float

- 한 요소(element)가 보통 흐름(normal flow)으로부터 빠져 텍스트 및 인라인(inline) 요소가 그 주위를 감싸는 자기 컨테이너의 좌우측을 따라 배치되어야 함을 지정한다.
- 글과 그림이 있는 매거진을 생각하면 쉽다.
- float가 안 좋은 이유는 아래 이미지처럼 균형을 안 맞추기 때문이다.

```
float: none; // 초기값, 위 아래로 배치
float: left; // float 요소가 왼쪽으로 가고 오른쪽의 빈 공간을 다른 요소가 채워준다.
float: right; // float 요소가 오른쪽으로 가고 왼쪽의 빈 공간을 다른 요소가 채워준다.
```
![Screenshot from 2021-10-28 12-20-15](https://user-images.githubusercontent.com/81145387/139180659-5685e192-3f0a-47cd-8905-2e10affb8aa4.png)

<br>

### 3. Flexbox

- 인터페이스 내의 아이템 간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델 로 설계되었다.

```
// 부모(container)에 적용
display: flex;
flex-direction: row || column || row-reverse || column-reverse; // 가로(기본), 세로
flex-wrap: nowrap || wrap || wrap-reverse; // 화면의 크기가 줄어들었을 때 변화없음(기본), 크기가 줄어들었을 때 아래로 내려감(화면에 모든 요소가 보이도록)
justify-content: flex-start || flex-end || center || space-between || space-around; // 가로방향 오른쪽 정렬(기본), 왼쪽 정렬, 중앙 정렬, 여백있게 정렬
align-items: stretch || flex-start || flex-end || center; 세로로 쭉 늘어난다(기본), 위로 위치, 아래로 위치, 중앙 위치,
align-content: flex-start || flex-end || center || space-between || space-around; // wrap 상태여야 가능하고 세로 축으로 이동

// 자식(item)에 적용
flex-grow: 1; // 화면에 정해진 비율에 맞게 채워짐 (여백X), 컨텐이너가 아이템보다 늘어날 때
flex-basis: 0; // basis를 적용 안 하면(auto) grow는 여백의 비율, 적용하면 컨텐츠의 비율이 됨
flex-shrink: 1; // 컨테이너가 아이템보다 줄어들 때
flex: 1; // basis:0으로 설정되고 grow와 shrink가 섞여있다.
align-self: flex-start || flex-end || center; // 자식에서 각각 위치를 정할 수 있다.
order: 1; // item의 보여지는 순서를 바꿀 수 있다. html이 변경되는 것은 아님
```

<br>

### 4. Grids

-  shorthand property 입니다. 외재적인 속성인 (grid-template-rows (en-US), grid-template-columns (en-US), grid-template-areas (en-US)), 값과 내재적인 속성인 (grid-auto-rows (en-US), grid-auto-columns (en-US), grid-auto-flow (en-US)), 값을 한번에 설정합니다.


```
// 부모(container)에 적용
display: gird;
grid-template-columns: 40% 60%; // 가로로 비율이 정해짐
grid-template-columns: 4fr 6fr; // 이것을 더 많이 쓴다. gap쓸 때 가로 스크롤이 안 생기기 때문
grid-template-columns: repeat(3, 1fr); // 1fr 1fr 1fr와 같음
grid-template-columns: 200px 1fr; // px로 고정할 수 있다.
grid-auto-rows: 300px; // 컨텐츠 높이를 똑같이 맞출 수 있다.
gird-auto-rows: minmax(200px, auto); // 최소 200px이고 더 늘어날 수 있다.
gird-auto-rows: minmax(10em, auto); // 현재 폰트의 10배 높이가 최소
justify-items: start || center || end; // 가로축으로 정렬된다.
align-items: start || center|| end; // 세로축으로 정렬된다.
grid-gap: 1rem; // gap은 fr로 쓰는 것이 좋다.

// 자식(item)에 적용
justify-self: start || center || end; // 해당 자식 요소만 가로축 정렬
align-self: start || center || end; // 해당 자식 요소만 세로축 정렬
grid-column: 1/4; // 1부터 4까지의 모든 칼럼(행)을 다 차지한다 (가로 축이 넓어진다)
gird-column: 3; // row의 시작점을 지정해준다.
grid-row: 2/4; // 2부터 4까지의 모든 로우(열)을 다 차지한다. (세로 축이 길어진다)
gird-row: 3/5; // column 시작을 3으로 하고 3에서부터 5까지 차지하면 다른 요소와 겹칠 수 있다.
```

<br>

### 참고자료

- [CSS layout](https://medium.com/@madhur.taneja/css-layouts-cced6c7a8764)
- [CSS Layouts - Flexbox vs Grid vs Float](https://youtu.be/hYJvxsgnGMA)
- [position MDN](https://developer.mozilla.org/ko/docs/Web/CSS/position)
- [Css의 position - fixed, sticky](https://manbalboy.github.io/front/css-layout-07.html)
- [float MDN](https://developer.mozilla.org/ko/docs/Web/CSS/float)
- [flexbox MDN](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
- [grid MDN](https://developer.mozilla.org/ko/docs/Web/CSS/grid)
- [CSS Flexbox와 CSS Grid, 한번에 정리!](https://youtu.be/eprXmC_j9A4)
- [display 브라우저 적용범위](https://caniuse.com/?search=display%3A%20flex)
- [gird 브라우저 적용범위](https://caniuse.com/?search=grid)
