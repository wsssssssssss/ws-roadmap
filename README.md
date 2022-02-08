# ws-roadmap [WIP]

Step by step guide to becoming a modern 기능이

##### Table of Contents

- [문서 모음](#docs)
- [기능이 로드맵](#ws-roadmap)
- [팁](#tip)
- [문제 풀이 순서](#problem-roadmap)

<br />

<a name="docs"/>

## 문서 모음

- [배열 method 정리](/docs/Array.md)
- [프로미스](/docs/Promise.md)
- [기타](/docs/etc.md)
  - [id를 classList처럼 제어하기](/docs/etc.md#id를-classlist처럼-제어하기)
  - [let const 차이](/docs/etc.md#let-const-차이)

---

<a name="ws-roadmap"/>

## 기능이 로드맵

(로드맵 이미지 추가 예정)

---

## Tip

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

1. const var 선언
2. let var 선언
3. 기타 나머지 function 선언
4. eventListenr function 선언
5. eve function 선언
6. (기타 init에서만 쓰이느 함수들)
7. init 선언
8. window.onload = init();

---

<a name="problem-roadmap"/>

## 문제 풀이 순서 (추천)

### 1. [css-control-element](https://github.com/wsssssssssss/css-control-element)

기능대회에서 사용되는 기본적인 label, input, css animation 등을 알아본다.

### 2. [js-ttt](https://github.com/wsssssssssss/js-ttt)

틱택토 미니 게임을 만들어보며 [Canvas API](https://developer.mozilla.org/ko/docs/Web/API/Canvas_API), [MouseEvent](https://developer.mozilla.org/ko/docs/Web/API/MouseEvent), [requestAnimationFrame](https://developer.mozilla.org/ko/docs/Web/API/Window/requestAnimationFrame)를 알아본다.

### 3. [css-ttt](https://github.com/wsssssssssss/css-ttt)

[js-ttt](https://github.com/wsssssssssss/js-ttt)의 틱택토 구현을 참고해 css만을 이용해 틱택토를 만들어 본다.

### 4. [js-trello](https://github.com/wsssssssssss/js-trello)

trello 미니 앱을 만들어보며 데이터 관리, dom 핸들링, [indexedDB](https://developer.mozilla.org/ko/docs/Web/API/IndexedDB_API)를 알아본다.

### 5. [js-lotto](https://github.com/wsssssssssss/js-lotto)

미니 로또 앱을 만들어 보며 Canvas API를 통한 이미지 관리, [FileSystemAccess API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API)를 알아본다.
