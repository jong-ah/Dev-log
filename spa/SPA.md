# 단일 페이지 애플리케이션 (SPA: Single Page Application)

서버로부터 새 페이지(html)을 불러오지 않고 현재 페이지를 동적으로 다시 작성하는 애플리케이션이다.   
처음 주소를 통해 웹(앱)으로 들어가면 서버는 모든 페이지 정보가 담긴 html, css, javascript를 전달해준다.   
정확히 말하면 javascript에 모든 페이지 정보가 담겨 있고, 필요한 정보가 있다면 javascript를 통해 일부만 요청을 해서 다시 화면이 보여진다.   

이 방식은 서버가 아닌 클라이언트에서 렌더가 되기 때문에 **CSR(Client Side Rendering)방식**이라고도 한다.

> [장점] 화면 전체가 아닌 필요한 부분만 갱신하기 때문에 자연스러운 페이지 이동과 사용자 경험을 제공해 줄 수 있다.   
> [단점] 하지만 최초의(첫 화면) 렌더링할 때 모든 리소스를 보여줘야하기 때문에 시간이 오래 걸릴 수 있다.    
> [해결] 단점을 극복하는 방법으로 CSR + SSR(Server Side Rendering)방식이 합쳐진 Next.js(Nuxt.js)가 나왔다.   


<br>

### 참고자료

- [SPA vs MPA와 SSR vs CSR](https://hanamon.kr/spa-mpa-ssr-csr-%EC%9E%A5%EB%8B%A8%EC%A0%90-%EB%9C%BB%EC%A0%95%EB%A6%AC/)
- [SPA 등장 배경과 CSR](https://youtu.be/C6uELkDh-60)
