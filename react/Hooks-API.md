# Hooks API

### Hooks API 개요

- Hook을 이용하여 기존 Class 바탕의 코드를 작성할 필요 없이 상태 값과 여러 React의 기능을 사용할 수 있습니다.
- Hooks API은 React 라이브러리에서 제공하는 기본 내장 API 함수입니다.
- 총 10가지가 있으며 그중 기본 Hook은 useState, useEffect, useContext 3가지가 있습니다.

<br>

### 기본 Hook

- **useState**
  - 가장 많이 사용하는 hook으로 상태 유지 값과 그 값을 갱신하는 함수를 반환합니다.
  - 프로젝트를 하면서는 검색어 선택 & 입력, 구독 이메일 입력 등 사용자가 입력된 값으로 갱신할 때 사용했습니다.
- **useEffect**
  - 모든 렌더링이 완료된 후 수행하는 함수입니다.
  - 프로젝트에선 Axios로 받은 데이터를 받아올 때나 상단에 시간을 지속적으로 나타낼 때 사용했습니다.
- **useContext**
  - 부모, 자식간에 필요한 props를 전역적으로 사용할 수 있게 도와줍니다.
  - createContext hook을 사용하여 단일 export할 변수를 생성하고 그 변수를 자식에서 props없이 useContext를 사용하여 전달해줄 수 있습니다. 
  - 프로젝트에선 Redux를 사용해 useContext를 사용하지 않았습니다.

그 외 useReducer, useCallback, useMemo, useRef, useImperativeHandle, useLayoutEffect, useDebugValue이 있습니다. 


<br>

### 참고자료

- [Hooks API Reference](https://ko.reactjs.org/docs/hooks-reference.html)
