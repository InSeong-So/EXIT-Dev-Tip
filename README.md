# Sis 전용 개발자 팁
> 스스로가 필요하다고 생각되는 개발팁을 작성하는 저장소

<hr>
<br>

# Q&A
- 웹 보안의 패킷 변조부분에서 공격자가 웹 프록시를 통해 패킷을 변조해 권한이 없는 게시물에 접근하려고 할때, 게시물에 비밀번호가 설정되어 있는 경우 공격자가 확인이 가능한지 여부
> 비밀번호가 설정되어 있으면 공격자가 게시물 확인 불가

- 웹 보안의 세션관리에서 공격자가 서버와의 정상적인 인증을 통해 세션 값을 받은 후, 인증을 받은 아이디가 아닌, 다른 아이디를 서버에서 받은 세션 값과 함께 다른 계정으로 로그인한 것 처럼 웹서비를 이용할 수 있다고 하는데, 그럼 이상황에서 모든 사용자는 같은 세션 값을 사용하고 있는지의 여부
> 로그인 값은 처음 한번만 확인하고, 그 이후는 세션값을 통해서만 이용하기 때문에 위의 상황이 가능하다.

- 데이터 링크 계층의 프레임 표현 방식의 문자 프레임은 데이터의 전, 후에 DLE, STX문자를 추가하는데, 만약 데이터 중에 DLE 문자가 들어있는 경우 구별을 위해 DLE 뒤에 DLE 문자 하나를 더 추가한다고 하는데, 그럼 만약에 원래 데이터에 DEL 문자가 2개라면, 그 상황에서 수신 호스트는 위의 상황과 어떻게 구별하는지 알고 싶다.
> 이 경우에는 DLE 문자가 4개가 들어가게 된다. 그 이유는 디코딩 할때, 수신 호스트는 처음 2개의 DLE 문자에서 마지막 문자를 삭제하게 되고, 마지막 2개의 DLE 문자에서 마지막 DLE를
삭제하게 되기 때문에, 결국 데이터에는 원본처럼 2개의 DLE만 남게된다.

<hr>
<br>

# 리팩토링
## 문서
- [나는 왜 리팩토링을 하는가?](http://www.dbguide.net/upload/data/technical/maso20030903.pdf)
- [리팩토링(마틴 파울러) 요약본](http://sarghis.com/blog/1142/)
- [나쁜 디자인 코드를 좋은 디자인으로 바꾸는 방법](http://pds26.egloos.com/pds/201301/18/75/Refactoring_Part_2.pdf)
- [코드 리뷰 사례로 알아보는 좋은 JavaScript 코드](https://cimfalab.github.io/deepscan/2016/09/code-review-2)
- [코드리뷰 가이드라인](http://flyburi.com/576)
- [자바 코드 리뷰(예시 포함)](http://www.java-success.com/30-java-code-review-checklist-items/)
- [DAO 리팩토링](https://github.com/slipp/jwp-book/tree/master/chapter7)

## 관련 동영상
- [문자열 계산기 구현 및 리팩토링 1단계](https://youtu.be/08YYZ0acYNE)
- [문자열 계산기 구현 및 리팩토링 2단계](https://www.youtube.com/watch?v=AAMap-pXXN4&feature=youtu.be)
- [문자열 계산기 구현 및 리팩토링 3단계](https://www.youtube.com/watch?v=weE5PVX9D60)
- [4-4. 중복 제거, clean code, 쿼리 보기 설정](https://youtu.be/DaqWKDvdmAk)

<hr>
<br>

# 디자인 패턴
## 문서
- [디자인 패턴에 대한 개념 설명](https://ocw.dongguk.edu/contents/2013/2013024132838/pdf2013024132838.pdf)
  - 왜 디자인 패턴이 필요한지, 패턴을 사용하면 어떤 점이 좋은지를 설명
- [예제 소스와 설명이 있는 블로그](http://egloos.zum.com/oniondev/v/9662639)
- [GoF 디자인 패턴을 자바를 통해 설명하는 강좌](https://www.inflearn.com/course/%EC%9E%90%EB%B0%94-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4/)
- [디자인 패턴을 JDK 소스를 이용하여 설명](http://blog.naver.com/2feelus/220642212134)
- 디자인 패턴 사용 이유, 적용 방법, 코드 예시
  - [1번](http://secretroute.tistory.com/category/Programming/Design%20Pattern)
  - [2번](http://iilii.egloos.com/tag/디자인패턴)
- [JavaScript에서 잘 쓰이는 패턴](https://scotch.io/bar-talk/4-javascript-design-patterns-you-should-know)
  - `Module`, `Prototype`, `Observer`, `Singleton`
- [개발자들이 알아야하는 8가지 디자인 패턴](http://www.thedevpiece.com/design-patterns-that-every-developer-should-know/)
  - `Singleton`, `State`, `Strategy and Factory`, `Template method`, `Builder`, `Chain of Responsibility`

<hr>
<br>

# UML
## 문서
- [UML을 왜 사용해야하는가](http://www.slideshare.net/ohyecloudy/uml-1735845)
  - 의사소통, 로드맵, 코드를 읽는 것보다 쉽게 파악 가능
  - 다이어그램을 언제 그려야 할지, 언제 그리지 말아야할지를 구분해서 설명
  - 다른 사람에게 이해시켜야 할 때 혹은 의견이 다르면 그려야 함
  - 다이어그램을 그리고 나서 코딩은 하지 않는 것이 좋음
  - 각 다이어그램들이 실전에서 어떻게 쓰여야 하는 지를 설명해 줌
- UML distilled(마틴 파울러)
  - 처음 UML에 대해 배울 때 보기 좋은 책
  - 책 요약한 블로그 http://blog.naver.com/goolungsoi/10128601760

## 관련 동영상
- [UML 2.0 동영상 강의](https://www.youtube.com/watch?v=OkC7HKtiZC0&index=1&list=PLGLfVvz_LVvQ5G-LdJ8RLqe-ndo7QITYc)
  - tutorial, activity, class, sequence, communication, timing, component, state machine, deployment diagram에 대해서 설명
  - 각 다이어그램에 대해서 세세하게 설명해줌

<hr>
<br>

# JAVA
## 문서
- [자바 버전 이력](http://blog.naver.com/2feelus/220670342427)
- 객체 지향 개발 5가지 원리
- 정의, 적용방법, 적용사례, 적용이슈
- 객체 지향 개발의 특징 
- [구글의 자바 코딩 스타일 가이드](http://kkangeva.tistory.com/39)
- [오라클에서 제공하는 자바 코딩 스타일 가이드](http://kwangshin.pe.kr/blog/java-code-conventions-%EC%9E%90%EB%B0%94-%EC%BD%94%EB%94%A9-%EA%B7%9C%EC%B9%99/)
- [읽기 좋은 코드가 좋은 코드다(요약)](http://www.jpstory.net/2013/01/the-art-of-readable-code/)
- [객체 지향 개발 5가지 원리](http://www.nextree.co.kr/p6960/)
  - 정의, 적용방법, 적용사례, 적용이슈 4부분으로 나누어서 자세하게 설명해줌
- [객체 지향 개발의 특징](http://krvision.tistory.com/entry/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8DObject-Oriented-Programmin)
- JAVA 코드 스타일/샘플 코드
  - [자바 샘플 코드](http://www.javapractices.com/home/HomeAction.do)
    - 주제에 따라 샘플 코드를 제공해주는 사이트 (조금 더 자세히 살펴봐야함)

<hr>
<br>

# Spring Framework
## 문서
- [스프링 버전이력](https://opentutorials.org/module/2269/12946)
- [스프링 프레임워크 기본 개념 설명](http://ooz.co.kr/170)
- [Next의 스프링부트를 이용한 웹 프로그래밍 교육](https://slipp.net/wiki/pages/viewpage.action?pageId=25529113)

<hr>
<br>

# JavaScript
## 문서
- [DOM에 관련한 개념, HTML과 다른 점, JavaScript와 비교](https://css-tricks.com/dom/)
- [DOM 정의](https://www.w3.org/TR/DOM-Level-2-Core/introduction.html)
- [JavaScript 정의](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction#What_is_JavaScript)
- [JavaScript 1급 객체](http://bestalign.github.io/2015/10/18/first-class-object/)
  - JavaScript 에서 함수는 객체이기 때문에, 인자로 넘겨주고 변수로 선언 할 수 있음
- [JavaScript 익명 함수, 즉시 실행 함수](http://www.nextree.co.kr/p4150/)
- [JavaScript 느슨한 타입(변수 선언 시 타입 지정 없음)](http://bestalign.github.io/2015/10/21/understanding-loose-typing-in-javascript/)
- [JavaScript Scoping, Hoisting 부분](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
- [함수 호출 방식에 따른 this의 바인딩](https://blog.outsider.ne.kr/439)
  - [예제](http://www.codejs.co.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%95%A8%EC%88%98-4%EA%B0%80%EC%A7%80-%ED%8C%A8%ED%84%B4%EC%97%90%EC%84%9C%EC%9D%98-this-%EC%82%AC%EC%9A%A9/)
- [Closure 개념 설명 및 코드 예시](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- [자바스크립트 프로토타입 설명](http://m.blog.naver.com/tmondev/220536094345)
  - 자바스크립트의 프로토타입에 대하여 쉬운 예제와 구성도로 설명하여 이해하기 쉬움
  - underscore.js 활용
    - underscore.js 라이브러리에 대한 설명과 간단한 코드를 통하여 어떻게 사용하면 되는지 설명 함
      - [1](http://blog.seoh.xyz/2012/10/09/getting-cozy-with-underscore-js/)
      - [2](http://tazz009.tistory.com/928)
      - [3](https://slipp.net/wiki/plugins/servlet/mobile#content/view/19530696)

<hr>
<br>

# AngularJS
- [리팩토링 요소(Angularjs를 이용한 프론트앤드 단에서 서비스와 컨트롤러 분리)](http://webframeworks.kr/tutorials/angularjs/dependency_injection_with_angularjs/)
- [Angularjs에서의 서비스 및 의존관계 주입 설명](http://programmingsummaries.tistory.com/125)
- [AngularJS에 관련한 링크들](http://w3devlabs.net/wp/?p=15)
- [AngularJS 기본 개념, 기본 구조](http://www.nextree.co.kr/p3241/)
  - 여기서 선정한 5가지 기본 개념을 주제로 AngularJS 설명(Scope, Model, View, Controller, Directives)
  - 추가해서 Modules, Service 설명
- [AngularJS Scope 개념, 구조 설명](http://blog.naver.com/jjoommnn/130182960996)
  - controller와 view 가 필요한 model, handler등을 갖고있음
  - tree 구조를 갖고 있음
  - HTML의 DOM 트리와 scope의 트리가 중간중간 연결되어있음
  - controller 나 view가 scope트리를 검색할 때, 검색이 상위 scope로 계속해서 진행하게됨(찾을때 까지) -> JavaScript의 prototype을 이용
  - watch list: 바인딩을 위해 존재/ event listener list: AngularJS 내부에서 사용되는 이벤트 리스트
- [AngularJS Model, View, Controller에 대한 기본 개념 및 실행 과정 설명](http://mobicon.tistory.com/270)
- [AngularJS Directives 정의 부분](http://www.nextree.co.kr/p4850/)
- [AngularJS Directives compile과 link를 나눈 이유](http://mobicon.tistory.com/271)
- [AngularJS Module](http://programmingsummaries.tistory.com/118)
  - Main 함수가 없기 때문에, module을 main 함수 처럼 사용
  - 4부분(Service, Directive, Filter, Application)으로 나누기를 권장하지만 이는 테스트의 용이함을 위해서 일 뿐, 필수는 아님
  - 설정, 실행 두 블럭으로 나뉘어지며, 실행 블럭이 실제 main 함수 처럼 사용됨
  - 종속을 통해서 다른 모듈들을 나열 할 수 있고, 선행 모듈이 필요한 경우, 선행 모듈은 요청 모듈보다 먼저 실행 됨
  - 모듈은 VM에 로드 되기까지 아무것도 하지 않기 때문에, 이를 통해서 로딩의 병렬화가 가능하다.
- [AngularJS Service](http://mobicon.tistory.com/329)
  - Constant, Value, Factory, Service, Provider
    - Factory를 가장 일반적으로 사용

<hr>
<br>

# 기타
## 문서
- [OOP 원리](http://www.nextree.co.kr/p6960/)
- [OOP 특징](http://krvision.tistory.com/entry/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%6%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8DObject-Oriented-Programming)
- [코딩 스타일](http://kkangeva.tistory.com/39)
- [코드 샘플](http://www.javapractices.com/home/HomeAction.do)
- [반복주기1을 진행하면서 문제 해결 정리, 글쓰는 개발자 Jbee](http://asfirstalways.tistory.com/292)
- [반복주기1의 원격서버를 Docker를 이용해서 해결, Inki Hwang](https://fisache.github.io/Install-Docker/)
- [개발관련 정리 사이트(추천도서 등)](http://asfirstalways.tistory.com/293)
