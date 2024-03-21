<details>
  <summary>⭐️ 쿠키와 세션에 대해서 설명해주세요.</summary>
  서버는 stateless 하다. 이 말의 뜻은 서버는 클라이언트의 상태를 기억하지 않는다.

  이를 위해 쿠키와 세션 개념이 도입되었다. 따라서 둘은 stateful하다.

  쿠키와 세션의 가장 큰 차이는 정보가 저장되는 위치이다. 쿠키는 클라이언트 단에서 저장되며, 세션은 서버측에서 관리한다.

  쿠키는 로컬에 저장되어 있으며 브라우저가 Request할시에 자동으로 헤더에 넣어 전송한다. 로컬에서 관리하기 때문에 변질되거나 스니핑 당할 우려가 있다.

  세션은 서버에 관리되며, 클라이언트가 서버에 접속시 세션 ID를 발급 받는다. 클라이이언트는 세션 ID를 쿠키에 저장한다. 서버는 세션 ID를 받아서 세션에 있는 클라이언트 정보를 가져와서 사용한다.
  보안면에는 우수하나, 사용자가 많아질수록 서버 메모리를 많이 차지하게 되는 단점이 있다.

  https://interconnection.tistory.com/74
</details>

<details>
  <summary>JWT 토큰에 대해서 설명해주세요.</summary>
  Json Web Token으로 JSON 형태의 웹에서 사용하는 토큰이다.

  JWT는 헤더, 페이로드, 시그니처로 이루어져있다. 각각 base64로 인코딩되어 있다.
  
  헤더에는 시그니처 생성에 이용되는 알고리즘을 나타내는 alg와 JWT를 담는 typ으로 이루어진 객체이다.

  페이로드에는 실질적인 토큰의 정보가 저장되어 있다. 토큰발급자, 만료시각도 존재한다. 쉽게 디코딩할 수 있기 때문에 중요한 정보를 넣으면 안된다.

  시그니처는 [인코딩한_헤더.인코딩한_페이로드]를 비밀 키를 사용해서 암호화를 진행하고 암호화된 값을 다시 인코딩한다.

  이를 통해 세션과 달리 저장소를 거치지 않아도, 비밀키만 있으면 인증을 진행할 수 있어 서버의 부하와 메모리를 줄일 수 있다.

  https://velog.io/@cloud_365/%EB%A1%9C%EA%B7%B8%EC%9D%B8-JWT%EB%A1%9C-%EB%A7%8C%EB%93%A4%EC%97%88%EC%96%B4-JWT%EA%B0%80-%EC%9C%A0%ED%96%89%EC%9D%B4%EC%9E%96%EC%95%84#jwt-json-we
  
</details>

<details>
  <summary>SOP와 CORS에 대해서 설명해주세요.</summary>
  SOP: Same Origin Policy (동일 출처 정책)

  자바스크립트 엔진 표준 스펙의 보안 규칙으로 하나의 출처(Origin)에서 로드된 자원(문서나 스크립트)이 호스트나 프로토콜, 포트번호가 일치하지 않는 자원과 상호작용 하지 못하도록 요청 발생을 제한하고, 동일 출처(Same Origin)에서만 접근이 가능한 정책

  CSRF 등의 공격으로부터 보호하기 위한 1차적인 방어선

  CORS: Cross Origin Resource Sharing (교차 출처 리소스 공유)

  웹 애플리케이션은 자신의 출처와 동일한 리소스만 불러올 수 있으며, 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS 헤더를 포함한 응답을 반환해야 한다. 이는 시스템 수준에서 타 도메인 간 자원 호출을 승인하거나 차단하는 것을 결정하는 것이다.

  CORS 해결방법: 서버에서 Access-Control-Allow-Origin 헤더 추가

  https://hudi.blog/sop-and-cors/
  https://xionwcfm.tistory.com/235
</details>

<details>
  <summary>⭐️ REST에 대해서 설명해주세요.  Restful API는 뭘까요?</summary>
  REST란?

  1. HTTP URI를 통해 자원을 명시
  2. HTTP Method를 통해
  3. 해당 자원에 대한 CRUD 연산 적용

  Restful API란? 위의 REST 원리를 지키고 아래의 설계 규칙을 따르는 API

  1. URI는 동사보다는 명사를, 대문자보다는 소문자를 사용
  2. 마지막에 슬래시 포함하지 않음
  3. 언더바 대신 하이폰 사용
  4. 파일확장자는 URI에 포함하지 않음
  5. 행위를 포함하지 않음

  https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80
</details>

<details>
  <summary>⭐️ REST 제약 조건에 대해 설명해주세요.</summary>
  아래 중 하나라도 지켜지지 않는다면 REST API라 할 수 없음
  
  1. Client-Server
  2. Stateless
  3. Cache
  4. Uniform Interface
  5. Layered System
  6. Self-Descriptiveness

  https://dev-coco.tistory.com/97

</details>

<details>
  <summary>URL, URI, URN 차이가 뭘까요?</summary>
  URI: Unirofm Resource Identifier, 인터넷의 자원을 식별할 수 있는 문자열을 의미

  URL: Uniform Resource Locator, 어떻게 리소를 얻을 것이고 어디에서 가져와야 하는지 명시하는 URI <br/>
  웹상의 주소를 나타내는 문자열로 더 효율적으로 리소스에 접근하기 위해 클린한 URL작성을 위한 방법론

  URN: Uniform Resource Name, 리소르를 어떻게 접근할 것인지 명시하지 않고 경로와 리소스 자체를 특정하는 것을 목표로 하는 URI <br/>
  실제자원을 찾기 위해서는 URN을 URL로 변환하여 이용

  http://www.naver.com/index.html?page=1232950&id=776 <- 전체는 URI, query string을 뺀 부분이 URL

  https://inpa.tistory.com/entry/WEB-🌐-URL-URI-차이 

</details>

<details>
  <summary>XSS 공격이 무엇이고, 방어하는 방법을 설명해주세요.</summary>
  웹 애플리케이션에서 웹사이트 관리자가 아닌 이가 웹 페이지에 악성 스크립트를 삽입하는 것 (innerHTML이나 insertAdjacentHTML로 가능)

  방어 방법
  1. 정규표현식 사용
  2. 입력값 치환: 특수문자를 문자열로 치환하기
  3. 직접 출력 금지: c:out으로 그대로 문자열로 출력

</details>

<details>
  <summary>CSRF 공격이 무엇이고, 방어하는 방법을 설명해주세요.</summary>
  Cross-site request forgery
  
  사용자가 자신의 의지와 무관하게 공격자가 의도한 행동을 하여 보안을 취약하게 한다거나 수정, 삭제 등의 작업을 하게하여 공격. 예를 들어, 피해자의 전자 메일 주소를 변경하거나 암호를 변경하거나 자금이체를 하는 등의 동작을 수행하게 할 수 있음.

  세션 방식을 사용할 때만 일어난다. 쿠키에 세션 ID를 담아두고, 요청시마다 헤더에 무조건 담겨가기 때문. jwt 토큰을 만들어서 로컬 스토리지에 보관하면 쿠키와 다르게 서버에 자동으로 전송이 안되고 항상 수동으로 Header에 담아줘야 하기 때문

  방어방법
  1. Referer check: 보통이라면 host와 Refferer 값이 일치
  2. CAPtCHA 도입
  3. CSRF 토큰 사용: 사용자 세션에 임의의 값을 저장하여 모든 요청마다 해당 값을 포함하여 전송하도록 함. 클라이언트에서는 화면에 hidden값으로 박아넣음. 서버에서 요청을 받을때마다, 세션에 저장된 값과 요청으로 전송된 값이 일치하여 검증하여 방어하는 방법
  
  프론트엔드에서 Axios를 사용하면 CSRF 토큰 값을 넣어서 보내기 때문에 CSRF Protection 기능을 제공, 우선 서버는 인증된 사용자에게 csrftoken을 setCookie의 형태로 response header에 담아 전송한다. 이를 받은 클라이언트는 이후부터 자신의 header와 cookie에 토큰을 담은 채로 api call을 하게 됨

  axios csrf token: https://jangsus1.tistory.com/2
</details>

<details>
  <summary>SQL Injection 공격이 무엇이고, 방어하는 방법을 설명해주세요.</summary>
  임의의 SQL 문을 주입하고 실행되게 하여 DB가 비정상적인 동작을 하도록 조작. OR 1=1 삽입하여 모든 정보를 다빼올 수 있다

  방어방법
  1. 입력 값 검증: 서버단에서 화이트리스트 기반
  2. 저장 프로시저 사용: 동적 SQL가 아닌 저장 프로시저를 사용하여 지정된 형식의 데이터가 아니면 쿼리가 실행되지 않도록

</details>

<details>
  <summary>웹 캐시에 대해 설명해주세요.</summary>
  브라우저가 웹 서버에 접속하여 받아온 정적 컨텐츠를 메모리 또는 디스크에 저장해놓은 것

  해시 옵션 설정하기
  1. Cahce-Control
  2. Last-Modified(HTTP1.0) < ETag(HTTP 1.1)

  https://hahahoho5915.tistory.com/33

</details>

<details>
  <summary>프록시 서버에 대해서 설명해주세요.</summary>
  클라이언트와 서버 사이의 중계자 역할로, 대신 요청을 처리한다.

</details>

<details>
  <summary>⭐️ 포워드 프록시에 대해서 설명해주세요.</summary>
  일반적인 프록시 서버

  포워드 프록시는 클라이언트들 앞에 위치. 내부망에서 클라이언트와 프록시 서버가 통신하여 인터넷을 통해 외부에서 데이터를 가져온다.

  예를 들어 naver.com에 요청하면 포워드 프록시 서버가 naver.com 리소스를 대신 받아 클라이언트에게 내밀어준다. 이로써 서버에게 클라이언트가 누구인지 감출 수 있다

  사용 이점: 클라이언트 보안(방화벽), 캐싱, IP 우회 및 보안

</details>

<details>
  <summary>⭐️ 리버스 프록시에 대해서 설명해주세요.</summary>
  리버스 프록시는 웹 서버/WAS 앞에 위치. 내부망에서 Proxy 서버와 내부망 서버가 통신하여 인터넷을 통해 요청이 들어오면 Proxy 서버가 응답

  즉, 클라이언트는 웹서비스에 접근시 웹서버에 요청하는게 아니라 프록시 서버로 요청. 이로써 본 서버의 IP정보를 숨길 수 있는 효과

  사용이점: 로드 밸런싱, 서버 보안, 캐싱, 암호화

  https://lazywon.tistory.com/69

</details>

<details>
  <summary>L7 로드 밸런서에 대해서 설명해주세요.</summary>
  애플리케이션 계층에서 동작. 주로 HTTP 및 HTTPs 프로토콜을 기반으로 클라이언트와 서버간의 트래픽 분산. 요청내용(URL, 헤더, 쿠키등)을 기반으로 로드 밸런싱 수행

  장점: 다양한 기능 및 유연성을 제공. 요청 내용을 분석하여 특정 요청을 특정 서버로 전달하거나, 캐싱 및 압축 등의 다양한 기능을 구현 가능. 
  
  단점: 처리 속도가 느림

  https://velog.io/@moonblue/L4%EC%99%80-L7-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%84%9C%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90

</details>

<details>
  <summary>커넥션 타임아웃과 리드 타임아웃에 대해 설명해주세요.</summary>
  커넥션 타임아웃: TCP 연결 (3 way handshake)시 정한 시간을 넘기면 연결할 수 없는 것으로 판단하고 타임아웃
  
  리드 타임아웃: 연결된 이후 정한 시간을 넘기면 데이터를 받을 수 없는 것으로 판단하고 에러

  https://alden-kang.tistory.com/20
</details>

