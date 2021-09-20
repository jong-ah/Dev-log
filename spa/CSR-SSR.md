# CSR과 SSR의 개념적 차이와 동작 방식 

### CSR과 SSR의 개념

- CSR은 client side rendering 줄임말로 웹페이지를 클라이언트 브라우저에서 렌더링한다는 의미입니다.
- SSR은 server side redering 줄임말로 웹페이지를 서버에서 렌더링한다는 의미입니다.

<br>

### CSR 동작방식

CSR은 처음 보여지는 싱글 페이지에서 HTML을 포함한 초기 데이터를 서버에 요청 받아 보여지고,다음 페이지로 이동시엔 html이 없는 필요한 데이터만 서버에게 받아 클라이언트에서 렌더링하는 방식입니다.

<br>

> 단점은 클라이언트에서 렌더하기 때문에 렌더 속도가 느리다는 점과 검색엔진최적화가 어렵다는 점입니다.   
> 장점은 자연스러운 페이지 전환과 필요한 리소스만 요청할 수 있어 성능이 좋고, 컴포넌트별 개발이 용이하다는 점이 있습니다.   
> 그러므로 CSR은 SNS처럼 사용자와 상호작용이 많아 서버 요청이 많은 사이트에서 사용하는 방식입니다.

<br>

### SSR 동작방식

SSR은 페이지를 이동할 때마다 html을 포함한 데이터를 서버에서 렌더해서 클라이언트에서 전달해주는 방식입니다.

<br>

> 단점은 데이터를 받기 전의 브라우저에서 잠깐 흰화면이 보이는 '깜빡'거림 현상이 겪고, 서버 부하가 걸릴 수 있다는 점이 있습니다.   
> 장점은 빠른 렌더가 가능하고, html 매 페이지에서 받아오기 때문에 검색엔진최적화가 된다는 점이 있습니다.   
> 그러므로 SSR은 검색 사이트나 회사 소개처럼 서버 요청이 거의 없는 사이트에서 사용되는 방식입니다.

<br>

### 참고자료

- [The Benefits of Server Side Rendering Over Client Side Rendering](https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8)
