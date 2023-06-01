# CORS (Cross-Origin Resource Sharing)

CORS는 http header를 기반으로한 메커니즘이다.\
이것은 서버에서 클라이언트로 보내는 http header를 통해 클라이언트가 서버에게 요청할 수 있는 리소스의 범위를 알려주는 것이다.\
origin은 domain, scheme, port로 구성되어 있고, 만약 origin이 다르다면 cross-origin이라고 한다.

CORS는 `preflight`라는 메커니즘을 사용한다.\
이는 실제 요청을 보내기 전에 서버에게 요청을 보내어, 요청을 보내도 되는지 확인하는 것이다.\

## CORS를 사용하는 요청들

- XMLHttpRequest, fetch (추후 서술할 과정을 따름)
- Web Fonts (CSS에서 `@font-face`를 사용할 때)
- WebGL Textures
- canvas에서 `drawImage()`를 사용할 때
- 이미지에서 CSS Shapes를 사용할 때

## 기능적인 개요

CORS 표준은 새로운 HTTP header들을 추가하는 것으로 동작한다.\
이것은 웹 브라우저가 허용된 origin인지 확인하는 것이다.\
추가적으로, HTTP 요청 메소드가 서버 데이터에 영향을 주는 경우에는 반드시 `preflight` 요청을 보내야 한다.\
이는 `POST`와 `PUT`같은 메소드들이다.

서버는 `credentials`를 요청에 포함시킬 수 있다.\
이는 Cookie와 같은 인증 정보를 의미한다.

## cors-safelisted request header

아래 사항들을 만족하는 헤더는 CORS-safelisted request header라고 한다.\
이것은 브라우저에서 `preflight` 요청을 보내지 않는 요청들이다.

## cors-safelisted response header

아래 사항들을 만족하는 헤더는 CORS-safelisted response header라고 한다.\
이러한 응답은 브라우저에서 `cors`에 대한 정책 검사 없이 요청을 읽을 수 있다.

## links

- <https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS>
- <https://developer.mozilla.org/en-US/docs/Glossary/CORS-safelisted_request_header>
- <https://developer.mozilla.org/en-US/docs/Glossary/CORS-safelisted_response_header>
