## CommonJS와 ES Module의 차이점에 대해서 설명해주세요.

### CommonJS 등장 배경
Node.js가 등장하면서 백엔드에서 JavaScript로 개발을 가능해졌습니다. 
하지만 당시 JavaScript에는 다른 파일의 코드를 가져와 사용하는 모듈 시스템이 없었습니다. 
특히 파일 시스템접근, 네트워크 통신 등 서버 환경에 필수적인 기능들을 모듈화하여 관리할 필요성이 커졌고 이를 해결하기 위해 CommonJS가 나타났습니다.
`require()`함수를 사용해 다른 모듈을 불러옵니다.

### ES Module 등장 배경

프론트엔드에서도 CommonJS를 사용해 모듈을 불러오게 됐습니다. 
하지만, CommonJS의 **동기적 로딩 방식은 브라우저 환경에 적용하기 어려운** 측면이 있었고 ES6에 언어 표준 모듈 시스템으로 ES Module이 도입되었습니다.
`import`키워드를 통해 모듈을 불러옵니다.

### CJS ESM 비교

CJS의 require()는 **동기적으로 작동**해 해당 파일을 불러와 실행할 때 까지 다음 코드로 넘어가지 않습니다. 
서버 환경에서는 큰 문제가 되지 않지만, 브라우저 환경에서는 모듈을 불러올 때 까지 아무 동작도 하지 못하는 문제가 발생할 수 있습니다.
ESM은 **비동기로 동작**하며 import문은 실제 코드 실행 전 모듈 간 의존관계를 파악하고 필요한 파일들을 효율적으로 불러올 수 있게 설계되었습니다.
`import { function } from 'module'`같은 형태로 필요한 부분만 명시적으로 가져올 수 있습니다.
이 구조 덕분에 Webpack, Vite와 같은 **모듈 번들러에서 실제로 사용하지 않는 코드는 번들 결과물에서 제외하는 트리 쉐이킹**을 효과적으로 수행할 수 있습니다.

최근에는 백엔드에서도 ESM을 사용하는 추세입니다. 
