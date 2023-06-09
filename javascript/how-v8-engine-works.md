# V8 엔진은 어떻게 동작하는가?

- 원문: <https://cabulous.medium.com/how-v8-javascript-engine-works-5393832d80a7>

v8 엔진은 총 5단계의 step을 거쳐 동작한다.

1. 환경 초기화
2. 코드 컴파일
3. 바이트코드 생성
4. 바이트코드 실행
5. 바이트코드 최적화

## 1. 환경 초기화

기술적으로, 이것은 v8의 역할은 아니다. 브라우저의 렌더러 프로세스가 아래 2가지를 초기화한다.

- Host 환경
- v8 엔진

브라우저는 다중 렌더러 프로세스를 가진다. 각 브라우저 탭은 별도의 렌더러 프로세스와 v8 인스턴스를 가진다.

host 환경이란 무엇인가? 이 글에서는 브라우저 맥락에서 설명한다. 브라우저에서의 host 환경이라는 것에 유의하여 글을 읽어보길 바란다. 여기서 또다른 host 환경은 Node에서의 host 환경이 있다.

### Host 환경

Host 환경은 자바스크립트 엔진이 의지하게 되는 모든 것을 제공한다. 아래를 포함한다.

- 콜 스택
- 힙
- 콜백 큐
- 이벤트 루프
- Web API와 Web DOM

웹 페이지에서의 유저 인터랙션은 이벤트를 트리거한다. 브라우저는 콜백 큐에 연관된 콜백 함수를 추가한다. 이벤트 루프는 무한 루프처럼, 큐로부터 콜백을 반복적으로 꺼내 실행한다. 그러고나서 콜백의 자바스크립트는 컴파일되고 실행된다. 약간의 데이터들이 콜 스택에 저장되고, 배열이나 객체 같은 일부 데이터는 힙에 저장된다.

왜 브라우저는 콜 스택과 힙 같이 다른 영역에 데이터를 저장하는가?

- 교환 공간의 속도를 위해

콜 스택은 연속적인 공간을 요구하고, 이것은 실행을 빠르게 한다. 그러나 연속적인 공간은 메모리에서 찾기 어렵다. 이 이슈를 해결하기 위해, 브라우저 설계자는 최대 크기를 지정해두었다. 이것은 스택 오버 플로우 에러를 발생시킨다. 보통은 브라우저는 콜스택에 제한된 크기의 데이터를 저장한다.

- 교환 공간의 공간을 위해

힙은 연속적인 공간을 요구하지 않는다. 그 트레이드오프로, 힙은 상대적으로 데이터를 처리하는 성능이 느리다.

저자의 의견으로, 콜스택과 이벤트 루프는 자바스크립트 동작을 이해하는데 있어 2가지 중요한 메커니즘이다. (콜스택과 이벤트 루프는 다른 포스트에서 다루겠음.)

### v8 엔진은 host 환경에 의존한다.

