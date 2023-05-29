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

`useRef`를 통해 ref를 얻어, DOM 노드를 얻기 위한 컴포넌트의 `ref` 속성에 전달한다.\
React가 이 div DOM 요소를 만들 때, 리액트는 `myRef.current`에 div DOM 요소를 할당한다.\
이제 `myRef.current`를 통해 div DOM 요소에 접근할 수 있다.

### 다른 컴포넌트의 DOM 요소 접근하기

기본적으로 리액트는 다른 컴포넌트의 DOM 요소에 접근할 수 없다.\
이는 ref를 사용하는 것은 최대한 피하게 하려는 목적도 있다.\
그러므로, 다른 리액트 컴포넌트에서 DOM 요소에 접근하려면, `forwardRef`를 사용해야 한다.\

- *low-level component: Buttons, Inputs 같은 원자성의 작은 컴포넌트
- *high-level component: Form, List, Dialog, Page 같은 복잡한 컴포넌트

### useImperativeHandle

`useImperativeHandle`은 `forwardRef`와 함께 사용되는 Hook이다.\
이를 이용하여 컴포넌트 DOM 요소의 API를 노출할 수 있다.

### 리액트는 언제 refs를 첨부하는가?

리액트의 매 업데이트는 render와 commit 2가지 단계로 나뉜다.

- Render: 리액트는 컴포넌트를 호출하고, 화면에 처리할 내용을 찾는다.
- Commit: 리액트는 DOM에 변경사항을 반영한다.

일반적으로는, 렌더링 할 때 ref를 참조해서는 안된다.\
first-render 과정에서 ref는 null이다.\
한번의 렌더 과정 이후에 ref는 초기화되기 때문에, 렌더링 중에 ref를 참조하면 안된다.

가능하면, event-handler를 통한 동작에서 ref를 사용하자.\

### flushSync

flushSync를 통해서, state 변경 후에 동작하는 로직을 작성할 수 있다.\
단, flushSync는 흐름을 blocking하므로, 사용에 주의하여야 한다.

### ref를 이용하여 DOM 조작 시, 주의사항

- DOM에 대한 조작은 가능하면 React에 맡겨야한다.
- 만약, ref를 통해 DOM을 지우거나 새로 추가한다면, React는 이를 알지 못한다.\
  이는 React가 DOM을 업데이트하는 방식과 충돌을 일으킬 수 있다.

### 정리

- ref은 범용적인 용도로 사용하지만, 많은 경우 DOM 요소 조작을 위해 사용된다.
- JSX 컴포넌트의 ref 속성에 ref를 전달하여 DOM 요소를 할당한다.
- 일반적으로, 스크롤링, 포커스, 레이아웃 크기/위치 등의 이유로 사용한다. (앱에 영향을 주지 않는 행동들, non-destructive actions)
- 리액트 컴포넌트는 기본적으로 DOM 요소를 노출하지 않는다. 이는 forwardRef를 사용하여 해결할 수 있다.
- DOM 관리는 React에 맡겨라. (ref를 통해 DOM을 추가하거나 제거하지 말자.)
- 만약, DOM을 건드리면 React에서 변경사항을 알지 못하므로, 충돌이 발생할 수 있다.

### links.2

- <https://react.dev/learn/manipulating-the-dom-with-refs>