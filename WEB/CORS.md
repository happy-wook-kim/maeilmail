## CORS란 무엇인가요?

CORS(Cross-Origin Resource Sharing)는 **웹 브라우저에서 서로 다른 Origin 간의 리소스 요청을 안전하게 제어하기 위한 메커니즘**입니다.

초기 웹은 프론트엔드와 백엔드가 동일한 서버에서 제공되는 정적 웹이 주를 이루었기 때문에 다른 서버의 리소스를 요청할 필요가 없었습니다.
그래서 브라우저는 보안상의 이유로 동일 출처 정책(Same-Origin Policy)을 적용해 다른 Origin의 요청을 제한했습니다.
CORS는 서버가 어떤 Origin의 요청을 허용할지 설정합니다.

오늘날 **웹 생태계는 프론트엔드와 백엔드가 분리되어 API 요청을 통해 동적으로 데이터를 주고받는 구조가 일반적**입니다.

프론트엔드에서 백엔드로 HTTP 요청을 보낼 때 브라우저는 `OPTIONS` 메소드를 사용한 Preflight 요청을 합니다.
이는 해당 서버의 CORS 정책을 확인하는 HTTP 요청으로 실제 요청 전 해당 서버에 CORS설정이 되어있는지 확인하기 위한 요청입니다
서버가 요청을 허용하면 실제 요청이 실행되고 응답이 캐싱되어 이후 요청을 더 효율적으로 처리됩니다.

### Origin이란?

Origin은 프로토콜, 도메인, 포트 번호로 구성됩니다.

아래의 경우 서로 다른 Origin으로 인식합니다.
* `https://www.exmaple.com`과 `http://www.example.com` 은 프로토콜이 다릅니다.
* `https://www.example.com`과 `https://www.examples.com` 은 도메인이 다릅니다.
* `https://www.example.com`과 `https://www.example.com:833` 은 포트 번호가 다릅니다.

### CORS 에러 해결 방법

CORS 에러는 프론트에서 다른 Origin의 API나 리소스를 요청할 때 서버가 해당 요청을 허용하지 않도록 설정된 경우 발생합니다.
백엔드에서 해결하는 방법은 서버에서 CORS 정책을 설정해 프론트엔드 도메인을 허용하도록 구성하고 Production 환경에서 도메인과 포트가 정확히 일치하는지 확인해야 합니다.
프론트엔드에서 해결하는 방법은 서버에서 CORS 정책을 수정할 수 없는 경우 프론트엔드에서 프록시 서버를 설정해 요청을 서버 Origin과 동일한 곳에서 요청하는 것 처럼 보이게 처리해야 합니다.
