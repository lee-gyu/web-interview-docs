# Web Layout - Percentage

> 부모의 크기에 따라 자식의 크기가 결정되는 퍼센티지 단위에 대해 알아보자.

## width / height

부모 요소의 정의된 `width`, `height`에 따라 자식 요소의 크기가 결정된다.\
만약, 부모 요소가 계산된 크기를 갖더라도, `width`, `height`를 정의하지 않았다면 자식 요소의 크기는 결정되지 않는다.

간단히 예를 들어, 부모는 `height` 값을 정의 하지 않았고, 자식은 `height: 100%`를 정의했다면, 자식 요소의 크기는 결정되지 않는다.

## margin / padding

여기서 `margin`, `padding`에 퍼센티지 단위를 사용하면 어떻게 될까?\
`margin`, `padding`은 `width`, `height`와 다르게 부모 요소의 크기가 아닌 자신의 크기에 따라 결정된다.

## translate

`translate`에 퍼센티지 단위를 사용하게 된다면 어떨까?

## links