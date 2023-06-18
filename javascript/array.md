# JavaScript Array Depp dive

> 자바스크립트의 Array는 Array가 아니다.

자바스크립의 Array는 일반적인 프로그래밍 언어의 Array와는 다르다. 보통의 Array는 메모리의 연속적인 공간에 데이터를 저장하는 자료구조이다. 하지만 자바스크립트의 Array는 연속적인 메모리 공간에 저장할까?

아래와 같은 코드를 어떻게 볼 수 있을까?

```js
const obj = {};
const arr = [1, 2, 3];

obj[0] = 1;
obj[1] = 2;
obj[2] = 3;
obj.length = 3;


```

object를 선언하여, 숫자 index에 요소를 할당하고, 그에 맞게 length를 지정해두었다. 이는 선언된 arr와 유사한 형태이다. 하지만 arr는 Array이고, obj는 Array가 아니다. 그렇다면 arr와 obj의 차이는 무엇일까?

자바스크립트 엔진은 



## Sparse Array

