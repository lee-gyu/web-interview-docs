# React Escape Hatches

> Escape Hatches: 비상 상황일 때의 탈출 방법

## Referencing Values with Refs

> Refs로 값 참조하기

컴포넌트가 특정 값을 기억해야하고, 그 값이 새로운 렌더를 트리거하지 않아야 하는 경우,\
`useRef`를 사용할 수 있다.

이번 장에서 배울 내용

- ref를 추가하는 방법
- ref를 업데이트하는 방법
- ref와 state의 차이점
- ref를 안전하게 사용하는 방법

```js
const ref = useRef(0); // returns { current: 0 }
```

### ref와 state의 차이점

| refs                                               | state                                        |
| -------------------------------------------------- | -------------------------------------------- |
| 값이 변경되어도 컴포넌트가 다시 렌더링되지 않는다. | 값이 변경되면 컴포넌트가 다시 렌더링된다.    |
| Mutable                                            | Immutable                                    |
| current를 통해 접근한다.                           | 매 렌더마다 가지게 되는 snapshot을 접근한다. |

### 언제 ref를 사용해야하는가?

- timeout, interval의 handler 기억
- DOM 요소들의 조작을 위해 DOM 요소 기억
- JSX에서 계산될 필요가 없는 정보들을 기억

### Best Practices for refs

- useRef는 비상 탈출구이다. (ref를 사용하지 않고도 해결할 수 있는 문제가 있다면, ref를 사용하지 말자.)
- 렌더링 중에, ref.current를 읽거나 쓰지 말자. (리액트는 렌더링 중에 ref.current가 변경되었는지 감지하지 못한다.)

### 정리

- ref는 비상 탈출구로로, 렌더링에 사용되지 않는 정보를 기억하기 위해 사용한다. 대부분 경우에서 사용할 필요가 없다.
- ref는 자바스크립트 오브젝트로, `current`라는 프로퍼티를 가진다.
- `useRef`를 통해 ref를 얻을 수 있다.
- 컴포넌트 리렌더 간에 내부 값이 유지된다.
- state와는 다르게 값을 변경하여도 re-render를 트리거하지 않는다.
- 컴포넌트가 렌더링 중에 ref.current를 읽거나 쓰지 말자.

### links.1

- <https://react.dev/learn/referencing-values-with-refs>

## Manipulating the DOM with Refs

> Refs를 사용하여 DOM 조작하기

리액트는 매 렌더마다 DOM을 자동으로 업데이트 한다.\
그래서 대부분의 경우, 직접 DOM을 조작하는 일은 없다.\
그러나, 가끔은 DOM을 직접 조작해야 하는 경우가 있다.\
예를 들면, 특정 요소에 focus를 주거나, 스크롤을 조작하거나 레이아웃으로 계산된 요소의 위치, 크기 등이 필요할 때가 있다.\
리액트 자체 적으로 지원하진 않으며, ref를 사용하여 직접 DOM을 조작할 수 있다.

이번 장에서 배울 내용

- ref 속성을 이용하여 DOM 요소에 접근하는 방법
- ref와 useRef Hook과의 관계
- 어떻게 다른 DOM 요소들을 참조하는지
- 어떤 케이스에서 불안정하게 DOM을 조작하는지

### ref를 통해 node 얻기

```jsx
import { useRef } from 'react';

// ...

const myRef = useRef(null);

// ...

<div ref={myRef}>

```

`useRef`를 통해 ref를 얻어, DOM 노드를 얻기 위한 컴포넌트의 `ref` 속성에 전달한다.

### links2

- <https://react.dev/learn/manipulating-the-dom-with-refs>