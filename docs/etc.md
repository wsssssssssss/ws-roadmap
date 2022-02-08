##### Table of Contents

- [id를 classList처럼 제어하기](#id를-classlist처럼-제어하기)
- [let const 차이](#let-const-차이)
- [화살표 함수 일반 함수 차이](#화살표-함수-일반-함수-차이)

---

# id를 classList처럼 제어하기

결론부터 말하자면 id는 하나만 가질수 있기 때문에 굳이 classList 처럼 제어할 필요 없이 그냥 함수를 만들거나 필요한 곳마다 비교하면 된다.

먼저 classList의 method들을 알아보자

classList method

- contains: 클래스가 있는지 확인한다.
- add: 클래스를 추가한다. (이미 있다면 무시)
- remove: 클래스를 제거한다.
- toggle: 클래스를 toggle한다.
- replace: 이미 존재하는 클래스를 새로운 클래스로 교체한다.

## 구현 (function)

### contains

```js
containsId = (ele, tgId) => ele.id === tgId;
```

### add

```js
addId = (ele, tgId) => (ele.id = tgId);
```

### remove

```js
removeId = (ele, tgId) => {
  if (ele.id === tgId) {
    ele.removeAttribute("id");
  }
};
```

### toggle

```js
toggleId = (ele, tgId) => {
  if (ele.id === tgId) {
    removeid(ele, tgId);
  } else {
    addId(ele, tgId);
  }
};
```

### replace

```js
repalceId = (ele, oldId, newId) => {
  removeId(ele, oldId);
  addId(ele, newId);
};
```

## 구현 (prototype)

### contains

```js
Element.prototype.containsId = function (tgId) {
  return this.id === tgId;
};

document.body.containsId("testId");
```

### add

```js
Element.prototype.addId = function (tgId) {
  this.id = tgId;
};

document.body.addId("testId");
```

### remove

```js
Element.prototype.removeId = function (tgId) {
  if (this.id === tgId) {
    this.removeAttribute("id");
  }
};

document.body.removeId("testId");
```

### toggle

```js
Element.prototype.toggleId = function (tgId) {
  if (this.id === tgId) {
    this.removeId(tgId);
  } else {
    this.addId(tgId);
  }
};

document.body.toggleId("testId");
```

### replace

```js
Element.prototype.replaceId = function (oldId, newId) {
  if (this.containsId(oldId)) {
    this.removeId(oldId);
    this.addId(newId);
  }
};

document.body.replaceId("testId");
```

# let const 차이

const: 변경 불가능한 변수
let: 변경 가능한 변수

# 화살표 함수 일반 함수 차이

기능대회 기준) this 유무 + 더 빨리 칠 수 있다. 클래스를 쓰지 않는다면 this 유무도 사실상 거진 상관 없다.
(화살표 함수 이벤트 핸들러의 경우 this로 Element를 가져오지 못한다.)
[관련 아티클](https://dmitripavlutin.com/when-not-to-use-arrow-functions-in-javascript/)
