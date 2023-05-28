# AHA Programming

> AHA Programming is a way of thinking about programming that I've found to be
> AHA 프로그래밍은 나에게 매우 유용한 프로그래밍에 대한 생각의 방식이다.

## DRY

> Don't Repeat Yourself
> Every piece of knowledge must have a single, unambiguous, authoritative representation within a system
> 모든 지식의 조각은 시스템 내에서 단일하고 모호하지 않으며 권위있는 표현을 가져야 한다.

코드 중복(Code Duplication)의 가장 큰 문제는 한 지점에서 버그를 수정했을 때 다른 지점에서는 수정하지 않았을 때 발생한다.\
큰 코드 베이스에서 이는 코드 신뢰성에 큰 영향을 미친다.\
그러므로, 중복이 일어나는 부분에 있어서 코드를 재사용할 수 있는 방법을 찾아야 한다.

## WET

> Write Everything Twice
> You can ask yourself "Haven't I written this before?" two times, but never three.
> 너는 스스로 "나는 이것을 이전에 썼지 않았나?" 라고 두 번 물어볼 수 있지만, 세 번은 물어볼 수 없다.

이것은 DRY의 반대 개념이다.\
DRY는 코드 중복을 피하라는 것이고, WET는 코드 중복을 허용하라는 것이다.\
WET는 코드 중복을 허용하므로써 코드를 재사용할 수 있는 방법을 찾지 않아도 된다.\
과도한 추상화의 부작용으로 코드가 더 복잡해지고, 이해하기 어려워지는 것을 방지할 수 있다.

항상 추상화가 좋은 것은 아니다.

## AHA

> Avoid Hasty Abstractions
> 성급한 추상화를 피하라.

DRY와 WET의 중간 지점에 있는 개념이다.\
DRY는 코드 중복을 피하라는 것이고, WET는 코드 중복을 허용하라는 것이다.\
AHA는 코드 중복을 피하되, 과도한 추상화를 피하라는 것이다.

추상화를 할지, 중복을 허용할지 무조건 적으로 따를 필요는 없다.\
변화에 유연한 코드를 작성하기 위해서는 추상화와 중복을 적절히 사용해야 한다.

## links

- <https://kentcdodds.com/blog/aha-programming#aha->
