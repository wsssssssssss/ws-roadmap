# ws-roadmap

Step by step guide to becoming a modern 기능이

##### Table of Contents

- [문서 모음](#docs)
- [팁](#tip)
- [문제 풀이 순서](#problem-roadmap)

<br />

<a name="docs"/>

## 문서 모음

- [배열 method 정리](/docs/Array.md)
- [클린 코드](/docs/CleanCode.md)
- [프로미스](/docs/Promise.md)
- [정규표현식](/docs/Regex.md)
- [MVC](/docs/MVC.md)
- [기타](/docs/etc.md)
  - [id를 classList처럼 제어하기](/docs/etc.md#id를-classlist처럼-제어하기)
  - [let const 차이](/docs/etc.md#let-const-차이)

---

## Tip

### 기능대회
**딱 한달만 평상시에 2배로 해보자. 보상은 달달할거다**

1. 플러그인은 최대한 활용하기
2. php template 무조건 외워서 5분 안에 완성하기
3. A모듈, B모듈 시간에 문제 빨리 풀고 남은 시간에 다음 모듈 구현하기
4. 수정된 부분, 중요한 부분은 펜으로 표시해두기
5. 종료 20분 전쯤에 문제 다시 천천히 읽으면서 구현한거랑 일치하는지 확인하기
6. 제출파일들 동작 및 파일명 10분 전에 최종 확인

#### 미리 구현할때 우선 순위 (미리 구현한거 코드는 그냥 바탕화면에 두면 됨)
1. php template 구현
2. B모듈 주요 기능 구현
3. C모듈 주요 기능 구현
4. DB 설계

#### 목표로 해야할 문제 풀이 시간
__A: 1시간__ <br />
__B: 30분__ <br />
__C: 30분__ <br />

#### 평가전
다같이 실제 대회처럼 시간 재면서 문제 풀이를 한다. 모듈별로 채점도 실제로 해본다.

#### 기능대회 준비

##### 3학년 기준
_(문제 나온 날)_ <br />
바로 문제 구현을 한다. __구현에 허점이 있어도 좋으니 최대한 빠르게 마무리한다. (당일에 무리해서 마무리할 필요는 없다)__ <br />
구현이 완료되면 __ws 슬랙 채널__ 에 공유한다. <br />

_(문제 완성 후)_ <br />
채점 하면서 터진 부분 + 코드를 최대한 개선해서 개선본을 완성한다. <br />
코드 개선에 대해서는 2학년 3학년 가릴거 없이 좋은 부분이 있다면 그걸 차용해서 최종 개선본을 통합해서 완성한다. <br />
서로서로 코드를 쉐어해서 어떻게 구현했나 같이 보는게 좋다. 코드 리뷰를 한다던가 하는 식으로 진행해도 좋다.

_(최종 개선본 완성 후)_ <br />
1일 1구현을 목표로 구현한다. 만약 하루안에 다 구현하지 못했다면 다음날에 이어서 작업하면 되니 괜찮다. <br />
1일 1구현이 된다면 A모듈 디자인 작업을 겸한다. 지금까지 모아둔 디자인들을 참고해서 제작하고 디자인은 하나만 만들지 말고 2개 정도 만들어 두는게 좋다. <br />
1일 1구현이 여유롭게 되면 타이머로 시간을 측정하면서 구현을 하고 시간 단축을 최대한 한다. <br />
1일 1구현 되면 1일 2구현 그거 되면 1일 3구현... 이렇게 점점 횟수를 늘리면 좋다. <br />
부족한 모듈이 있다면 해당 모듈은 구현 횟수를 늘린다. <br />

_(대회 2~3일 전)_ <br />
잠깐 만약 문제가 수정이 된다면 어떻게 수정할지를 한번쯤 상상해보고 어떻게 구현하면 좋을지를 생각해본다.

_(대회 전날, 당일)_ <br />
긴장하지 말고 편한 마음으로 한다. 실수만 안하면 메달은 확정이다.

##### 2학년 기준
_(문제 나온 당일)_ <br />
바로 문제 정리를 한다. 정리는 문제 나온 __당일에 무조건 마무리한다.__
문제가 정리되면 __ws 슬랙 채널__ 에 원본 문제와 함께 공유한다. (정리라 함은 repositoriy 과제들처럼 - 기능1, - 기능2 이렇게 정리하는거) <br />

_(문제 정리 완료 후)_ <br />
문제 정리 후에는 3학년이 과제 완성본을 만들기 전까지는 디자인들을 찾아서 __디자인-공유 슬랙 채널__ 에 올린다. 디자인은 최대한 긁어 모으는게 좋다. <br />
- 꿀팁: web design tempalte, flat design template 비슷한 키워드로 검색하면 꽤 괜찮은게 나온다. 사이트는 pinterest, dribbble, behance가 좋다.

_(3학년이 문제 완성 후)_ <br />
3학년 문제를 터트린다는 생각으로 채점한다. 최대한 많이 터트릴수록 좋다. (url 수정을 통해서 터지는건 상관없다. 실제 대회 과제 채점시에 url은 건들지 않는다)
완성본 코드 구조를 보고 따라치면서 구현을 익히고, 익혔으면 혼자 구현해본다. <br />
혼자 구현 완료 했으면 3학년 개선본이 나왔다면 그거랑 비교하면서 더 좋은 부분이 있으면 공유하고, 부족한 부분이 있으면 보완한다. 안나왔다면 나올때까지 기다리면서 부족한 부분(php?)을 공부한다. <br />

_(부족한 부분 공부 완료, 최종본 나온 후)_ <br />
하루에 한번 과제를 구현한다. __구현하다 막히면 바로 최종본을 참고한다. 참고해도 상관없으니 구현을 목표로 하자__ <br />
__1일 1구현은 계속 반복한다.__ 대회 3일전 혹은 5일전쯤 되면 참고 안해도 구현할 수 있을것이다. <br />
구현은 계속 하면서 중간중간 디자인 작업을 들어간다. 지금까지 모아둔 디자인 들을 참고해서 제작한다. 선배들과 디자인이 안겹치는게 좋다.

### Js 팁
- singleQuote 사용하기
- 네이밍은 constCase
- 변경되지 않는 값은 const
- 변경되는 값은 let
- 함수는 arrow function ( \_ => {} )
- === 사용하기
- 함수 파라미터는 3개 이하로 쓰기
- 삼항연산자를 많이 쓰자 (함수의 로직 같이 흐름이 있는 부분은 if 문을, 값의 선언 같은 부분은 삼항연산자)
- 이벤트리스너 함수 네이밍은 handle* or on* [ ex) handleBtnClick, onBtnClick ]
- 증가하는 값을 조건에 넣을땐 값이 어떤 값보다 작을때 말고 클때로 조건을 걸자 (흐름을 맞추자. 커지는 값은 무엇보다 클때로 비교하는게 이해가 더 쉬워진다)
- 전역값은 파라미터에 넘기지 말고 바로 접근해서 사용하자
- 2가지 경우의 수만 있는 값은 boolean을 사용하는게 편하다

### 코드 작성 순서

순서는 이렇게 써뒀지만 코드의 흐름을 맞춰서 위에서 부터 아래로 작성하면 됨

#### Javascript
1. const var 선언
2. let var 선언
3. 기타 나머지 function 선언
4. eventListenr function 선언
5. eve function 선언
6. (기타 init에서만 쓰이는 함수들)
7. init 선언
8. window.onload = init();

#### CSS
1. 특정 아이템들의 고유 속성들
    - list styling, table styling
2. item 요소에서 부모의 속성을 override 할 수 있는 속성들
    - (align-self, justify-self, ...)
3. position
    - position, top, right, bottom, left
4. display
    - display
    - display에 의한 요소들 (flex 관련 속성, grid 관련 속성, ...)
5. size
    - width, height 관련 요소
6. margin
7. padding
8. border
9. outline
10. box-shadow
11. background
12. font
    - font-size, color, line-height
13. etc
    - z-index, box-sizing, cursor, 등등

Ex
```css
body {
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  min-width: 500px;
  height: 100vh;
  margin: 0 auto;
  padding: 35px 25px;
  border: 1px solid #ddd;
  border-radius: 15px;
  font-size: 24px;
}
```

---

<a name="problem-roadmap"/>

## 문제 풀이 순서 (추천)

### 1. [css-control-element](https://github.com/wsssssssssss/css-control-element)

기능대회에서 사용되는 기본적인 label, input, css animation 등을 알아본다.

### 2. [css-animation](https://github.com/wsssssssssss/css-animation)

css animation을 보다 디테일하게 알아본다.

### 3. [js-ttt](https://github.com/wsssssssssss/js-ttt)

틱택토 미니 게임을 만들어보며 [Canvas API](https://developer.mozilla.org/ko/docs/Web/API/Canvas_API), [MouseEvent](https://developer.mozilla.org/ko/docs/Web/API/MouseEvent), [requestAnimationFrame](https://developer.mozilla.org/ko/docs/Web/API/Window/requestAnimationFrame)를 알아본다.

### 4. [css-ttt](https://github.com/wsssssssssss/css-ttt)

[js-ttt](https://github.com/wsssssssssss/js-ttt)의 틱택토 구현을 참고해 css만을 이용해 틱택토를 만들어 본다.

### 5. [js-drawing-tool](https://github.com/wsssssssssss/js-drawing-tool)

drawing tool을 javascript로 구현하며 Canvas API에 대해 더 구체적으로 알아본다.

### 6. [php-wordle](https://github.com/wsssssssssss/php-wordle)

wordle을 구현하며 clipboard api, http request, polling, 기타 js 테크닉 및 php를 알아본다.

### 7. [js-trello](https://github.com/wsssssssssss/js-trello)

trello 미니 앱을 만들어보며 데이터 관리, dom 핸들링, [indexedDB](https://developer.mozilla.org/ko/docs/Web/API/IndexedDB_API)를 알아본다.

### 8. [php-trello](https://github.com/wsssssssssss/php-trello)

js-trello 작업을 기반으로 ajax, polling, php PDO, mysql database를 알아본다.

### 9. [js-chatting](https://github.com/wsssssssssss/js-chatting)

slack의 채팅 기능을 일부 구현하며 File Upload, Emoji, indexedDB를 알아본다.

### 10. [php-slack](https://github.com/wsssssssssss/php-slack)

js-chatting을 기반으로 slack을 구현하며 ajax, polling, php PDO, mysql database를 알아본다.

### 11. [js-lotto](https://github.com/wsssssssssss/js-lotto)

미니 로또 앱을 만들어 보며 Canvas API를 통한 이미지 관리, [FileSystemAccess API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API)를 알아본다.
