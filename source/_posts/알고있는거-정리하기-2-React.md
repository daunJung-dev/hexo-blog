---
title: 알고있는거 정리하기(2) React
tags:
---

## 목차

---

[1. Learning For React](#learning_for_react)
[2. What is React?](#what_is_react?)

---

## Learnig For React

### Javascript

리액트를 배우기 위해서는 선행되어야 할 것으로는 `javascript`, `html`,`css` 등등 여러가지가 있겠지만, 단연 javascript는 그 중 핵심이라고 할 수 있다. 리액트 자체가 자바스크립트로 만들어진 라이브러리인만큼 자바스크립트가 어떤 언어인지 잘 아는 것 외에 리액트를 빠르고 깊게 이해하는 방법은 없다고 해도 무방하다.

`javascript`는 스크립트에 대한 [MDN][mdn_link] 소개를 따르면,

> JavaScript(JS)는 가벼운 인터프리터 또는 JIT 컴파일 프로그래밍 언어로, 일급 함수를 지원합니다. 웹 페이지의 스크립트 언어로서 제일 유명하지만 Node.js, Apache CouchDB, Adobe Acrobat처럼 많은 비 브라우저 환경에서도 사용하고 있습니다. JavaScript는 프로토타입 기반의 동적 다중 패러다임 스크립트 언어로, 객체지향형, 명령형, 선언형(함수형 프로그래밍 등) 스타일을 지원합니다. 자세한 내용은 JavaScript에 대하여를 참고하세요.
> 이 문서는 JavaScript 언어 자체만 다루며 웹 페이지를 비롯한 다른 사용 환경에 대해서는 다루지 않습니다. 웹 페이지의 특정 API에 대하여 알고 싶다면 웹 API와 DOM을 참고하시기 바랍니다.
> JavaScript의 표준은 ECMAScript입니다. 2012년 기준 최신 브라우저는 모두 ECMAScript 5.1을 온전히 지원합니다. 이전 브라우저의 경우는 최소한 ECMAScript 3까지는 지원합니다. 2015년 6월 17일 ECMA International에서는 공식명 ECMAScript 2015 로 불리는 ECMAScript의 6번째 주 버전을 발표했습니다(보통 ECMAScript 6 혹은 ES6으로 불립니다). 그 이후 ECMAScript 표준의 출시 주기는 1년입니다. 이 문서는 최신 초안(현재 ECMAScript 2020)에 기반을 둡니다.
> JavaScript를 Java 프로그래밍 언어와 혼동해서는 안 됩니다. "Java"와 "JavaScript" 두 가지 모두 Oracle이 미국 및 기타 국가에 등록한 상표입니다. 하지만, 두 언어는 문법 체계와 사용 방법이 전혀 다릅니다.
> 안내서 및 자습서와 함께 JavaScript 프로그램을 짜는 법을 알아보세요.

javascript가 어떤 기능들을 제공하는지, 그리고 흔히 할 수 있는 오해로 `java`와 `javascript`를 혼동하지 말라는 친절한 안내까지 말하는 것을 볼 수 있다.

하지만 둘 다 배워본 바로 두 언어 모두 개념상 통하는 부분들이 상당히 많고, 파이썬을 비롯한 C#, c++ 등의 현대 프로그래밍 언어는 상당한 개념들을 공유하고 있기 때문에, 어떤 언어든 하나를 제대로 익히기만 하면 다른 언어도 금방익힌다는 많은 개발자들의 조언이 꽤나 합리적이란 생각이 든다. 쨋든, `javascript`를 잘 이해하는 사람이 React를 잘 한다!

`javascript`개발자를 찾는 구인 공고를 보면 꼭 보이는 말이 있다.

> ES6 및 최신 javascript 문법에 익숙한 자

`왜 최신 문법에 익숙한 사람을 찾을까?`에 대한 고민을 가졌던 적이 있다. 실무를 하면서 그에 대한 나름의 답을 내려보자면, [ECMA][ecma_wiki_link]를 통해 매년 자바스크립트의 새로운 문법이 개발자들에게 소개되고, 이것은 웹 개발의 표준으로 작동하기 때문에, 최신 자바스크립트 문법을 사용할줄 모른다면, 지금 쓰이는 라이브러리들을 활용할 수 없는 능력을 지녔다는 것으로 생각될 수 있다. 따라서 `최신 스펙에 대한 이해 == 시대에 맞는 개발자`라는 공식이 되는 것이다.

심지어 React의 공식문서에서는 이렇게 말한다.

> JavaScript의 최신 버전인 ES6의 몇 가지 기능을 사용한다는 사실에 주목해주세요. 자습서에서는 화살표 함수, 클래스, let, const를 사용합니다. Babel REPL을 사용하여 ES6 코드가 어떻게 컴파일되는지 확인할 수 있습니다.

적어도, ES6는 이해해야 React를 배울 준비가 됐다고 할 수 있다.

## DOM

`React`는 [DOM][dom_wiki_link]을 javascript를 이용해 DOM을 동적으로 렌더링하는 라이브러리다. 따라서, `DOM`이 무엇인지 알아야 하는게 선행되어야 한다

DOM에 대한 자세한 설명은 링크를 통해 확인해보면 좋다. 내용을 요약한 부분을 인용하자면 이렇다.

> DOM은 HTML 문서에 대한 인터페이스입니다. 첫째로 뷰 포트에 무엇을 렌더링 할지 결정하기 위해 사용되며,
> 둘째로는 페이지의 콘텐츠 및 구조, 그리고 스타일이 자바스크립트 프로그램에 의해 수정되기 위해 사용됩니다.
> DOM은 원본 HTML 문서 형태와 비슷하지만 몇 가지 차이점이 있습니다.
>
> - 항상 유효한 HTML 형식입니다.
> - 자바스크립트에 수정될 수 있는 동적 모델이어야 합니다.
> - 가상 요소를 포함하지 않습니다. (Ex. ::after)
> - 보이지 않는 요소를 포함합니다. (Ex. display: none)

자, 이제 그럼 DOM을 동적으로 생성해주는 강력한 라이브러리 `React`에 대해서 알아보자.

## What is React?

> React는 사용자 인터페이스를 구축하기 위한 선언적이고 효율적이며 유연한 JavaScript 라이브러리입니다. “컴포넌트”라고 불리는 작고 고립된 코드의 파편을 이용하여 복잡한 UI를 구성하도록 돕습니다.

[공식문서][react_doc_link]의 설명이다. 리액트는 컴포넌트라는 작은 파편(마치 html 코드 조각)들을 떼어내서 조립하는 것 마냥 화면을 쉽게 구성하고 또한 재사용하기도 쉽게끔 해주는 javascript 라이브러리다. JSP와 같이 Static한 html 파일을 서버에서 생성하여 사용자에게 제공하던 기존의 웹 개발 프레임을 완전히 달라지게 했다고 할 수 있다. 동적으로 화면이 구성되게 하며, 사용자의 액션에 따라 server로부터 새로운 정보를 불러들이기도 하고, 상호작용 할 수 있게끔 하는 것이다.

React 내부 api 들에 대한 설명들도 블로그에 남기면 좋겠지만, 같은 걸 두벌 남기는 꼴밖에 되지 않을 것이다. Javascript ES6까지 끝냈고, html, css의 기본에 대해서 공부를 했다면, 공식문서의 자습서를 통해 바로 리액트를 시작해보는걸 추천한다. CRA(create-react-app)을 통해서 5분도 되지 않아 작은 웹페이지 개발을 할 수 있을 것이다.

## 마무리

알고있는 것에 대해 천천히 다쓰기에는 javascript, react, 등등 너무 양이 많을것 같다... 일단은 지금 쓰고 있는 것들에 대한 정리를 먼저 시작해야겠다.
최근 실제 프로젝트에 처음 사용해보았던 `recoil`에 대한 후기를 적어보고, 더 나은 사용방법이 있었는지 한번 회고해봐야겠다. 오늘은 여기까지! 굿밤!

[mdn_link]: "https://developer.mozilla.org/ko/docs/Web/JavaScript"
[ecma_wiki_link]: "https://ko.wikipedia.org/wiki/ECMA%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8"
[dom_wiki_link]: "https://wit.nts-corp.com/2019/02/14/5522"
[react_doc_link]: "https:reactjs.org/tutorial/tutorial.html"
