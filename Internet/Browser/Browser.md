## 📒 브라우저란?
* 웹 페이지, 이미지, 비디오 등의 콘텐츠를 수신, 전송 및 표현하는 **소프트웨어**이다.<br>
`e.g.) 크롬,파이어폭스,엣지,사파리 등등`
## 📕 브라우저 주요 기능
* 사용자가 선택한 자원을 서버에 요청하고 브라우저에 표시
* 자원의 주소는 URI에 의해 정해짐
* 자원은 HTML, PDF, 이미지 혹은 다른 형태
## 📗 브라우저 기본 구조
1. **사용자 인터페이스** - 주소 표시줄, 이전/다음 버튼, 북마크 메뉴 등. 요청한 페이지를 보여주는 창을 제외한 나머지 모든 부분이다.
3. **브라우저 엔진** - 사용자 인터페이스와 렌더링 엔진 사이의 동작을 제어.
4. **렌더링 엔진** - 요청한 콘텐츠를 표시. 예를 들어 HTML을 요청하면 HTML과 CSS를 파싱하여 화면에 표시함.
5. **통신** - HTTP 요청과 같은 네트워크 호출에 사용됨. 이것은 플랫폼 독립적인 인터페이스이고 각 플랫폼 하부에서 실행됨.
6. **UI 백엔드** - 콤보 박스와 창 같은 기본적인 장치를 그림. 플랫폼에서 명시하지 않은 일반적인 인터페이스로서, OS 사용자 인터페이스 체계를 사용.
7. **자바스크립트 해석기** - 자바스크립트 코드를 해석하고 실행.
8. **자료 저장소** - 이 부분은 자료를 저장하는 계층이다. 쿠키를 저장하는 것과 같이 모든 종류의 자원을 하드 디스크에 저장할 필요가 있다.<br>
  HTML5 명세에는 브라우저가 지원하는 '웹 데이터 베이스'가 정의되어 있다.
<div align="center">
  <img src="./img/Browser.png"><br>
  `크롬은 대부분의 브라우저와 달리 각 탭마다 별도의 렌더링 엔진 인스턴스를 유지하는 것이 주목할만하다.`<br>
  `각 탭은 독립된 프로세스로 처리된다.`
</div>

## 📘 렌더링 엔진
렌더링 엔진의 역할은 요청 받은 내용을 브라우저 화면에 표시하는 일이다.

렌더링 엔진은 HTML 및 XML 문서와 이미지를 표시할 수 있다. 물론 플러그인이나 브라우저 확장 기능을 이용해 PDF와 같은 다른 유형도 표시할 수 있다. 그러나 이 장에서는 HTML과 이미지를 CSS로 표시하는 주된 사용 패턴에 초점을 맞출 것이다.
#### 📍렌더링 엔진들
이 글에서 다루는 브라우저인 파이어폭스와 크롬, 사파리는 두 종류의 렌더링 엔진으로 제작되었다. 파이어폭스는 모질라에서 직접 만든 게코(Gecko) 엔진을 사용하고 사파리와 크롬은 웹킷(Webkit) 엔진을 사용한다.

웹킷은 최초 리눅스 플랫폼에서 동작하기 위해 제작된 오픈소스 엔진인데 애플이 맥과 윈도우즈에서 사파리 브라우저를 지원하기 위해 수정을 가했다.<br> 더 자세한 내용은 [webkit.org](www.webkit.org)를 참조한다.
#### 📍동작 과정
`HTML 문서를 파싱` > `브라우저 화면에 랜더링하기위해 다루기 쉬운 구조로 바꿈` > `css파일 파싱` > `렌더트리 구축` > `렌더트리 배치` > `렌더트리 그리기`<br>
<div align="center">
  <img src="./img/Dom_process.png">
</div>

렌더링 엔진은 HTML 문서를 파싱하고 "**콘텐츠 트리**" 내부에서 태그를 [DOM](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction) 노드로 변환한다.<br>
그 다음 외부 CSS 파일과 함께 포함된 스타일 요소도 파싱한다. 스타일 정보와 HTML 표시 규칙은 "**렌더 트리**"라고 부르는 또 다른 [트리](../../ETC/ETC.md#트리(Tree)란?)를 생성한다.<br><br>
렌더 트리는 색상 또는 면적과 같은 시각적 속성이 있는 사각형을 포함하고 있는데 정해진 순서대로 화면에 표시된다.<br><br>
렌더 트리 생성이 끝나면 배치가 시작되는데 이것은 각 노드가 화면의 정확한 위치에 표시되는 것을 의미한다. 다음은 UI 백엔드에서 렌더 트리의 각 노드를 가로지르며 형상을 만들어 내는 그리기 과정이다.<br><br>

일련의 과정들이 점진적으로 진행된다는 것을 아는 것이 중요하다. 렌더링 엔진은 좀 더 나은 사용자 경험을 위해 가능하면 빠르게 내용을 표시하는데 모든 HTML을 파싱할 때까지 기다리지 않고 배치와 그리기 과정을 시작한다. 네트워크로부터 나머지 내용이 전송되기를 기다리는 동시에 받은 내용의 일부를 먼저 화면에 표시하는 것이다.<br>

<div align="center">
  <img src="./img/Webkit_process.png">

  <br>`다음은 '웹킷'의 동작과정이다.`
</div>
