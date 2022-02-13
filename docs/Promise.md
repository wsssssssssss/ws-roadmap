# Promise

Promise를 알려면 그 전에 동기(synchronous) 비동기(asynchronous)에 대해서 알아야 한다. <br />

해당 개념을 간단하게 설명하자면 아래와 같다. 단순히 자바스크립트 언어 보다는 컴퓨터 공학에 더 관련되어 있기 때문에 아래와 같이 심플하게만 하고 넘어간다.
- 동기: 단어의 뜻은 동시에 진행된다는 뜻.
  - 동기의 뜻만 보면 코드를 동시에 실행하는거라고 착각할 수 있다.
  코드가 동시에 실행되는게 아니라 코드의 실행과 종료가 동시(동시라 하기엔 모호하지만)에 일어나는 즉, 현재 실행한 코드가 실행 시간이 얼마나 걸리든 기다렸다가 실행이 완료되면 다음 코드를 실행한다. 그렇기 때문에 코드의 실행이 순서대로 차례차례 일어나는게 보장된다.
- 비동기: 단어의 뜻은 동시에 일어나지 않는다는 뜻.
  - 비동기는 동기와 반대이다. 코드의 종료를 기다리지 않고 다음 코드로 넘어간다.

<img src="https://media.vlpt.us/images/hwang-eunji/post/5485ec1e-140b-457e-aa53-f8d7dc15f2d8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-03-31%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%202.29.45.png" width="600" />

동기 비동기에 대해 학교 수업으로 간단한 예시를 들어보자면,<br />
수업은 현재 교시가 끝나면 다음 교시로 넘어가게 되어 있다. 각 교시별로 시간이 겹치지 않게 정해두었기 때문에 앞의 교시가 끝나기 전까지는 다음 교시를 시작하지 않는다. 8시 20분에 시작하는 1교시가 40분 걸린다면 2교시는 9시(쉬는시간 미포함)에 시작한다.<br />
만약 디지텍 고등학교가 학습 속도 향상을 목표로 각 교시별 시작 시간을 겹치게 했다 가정해보자. 그렇다면 1교시를 진행하면서 2교시도 진행할 수 있고, 3교시를 진행하면서 4,5,6교시를 동시에 진행할수도 있다. 앞의 교시가 끝나든 말든 다음 교시가 언제든 시작할 수 있게 되는 것이다.<br />
위 예시에서 전자의 경우는 수업이 끝나기 전까지는 다음 수업이 시작되지 않기 때문에 동기적이라 할 수 있고, 후자의 경우에는 수업들이 서로 끝나건 말건 상관없이 시작하기 때문에 비동기적이라 할 수 있다.<br />

마아아아안약에 느낌이 안온다면 급식실에 줄이 한줄이면 동기, 여러 줄이면 비동기라고 일단 생각하자. <br />

자바스크립트의 경우는 동기적으로 실행된다. 기본적으로 하나의 쓰레드를 사용하고, 코드를 콜스택에 넣어서 실행한 뒤 해당 작업을 콜스택에서 제거하고 다음 코드로 넘어가고의 반복이기 때문에 현재 작업이 완료되기 전까지는 다른 작업을 하지 않는다.<br />

아래의 이미지를 사용하는 코드를 봐보자.
```js
document.body.onclick = function () {
  console.log('body 클릭');
}

const img = new Image();
img.src = src;
document.body.append(img); // 이미지가 로딩되면 body에 추가하기
...
console.log('나머지 기타 코드들');
```

이미지의 src를 설정하면 이미지 데이터를 가져와야 하기 때문에 로딩에 시간이 걸린다. 만약 해당 부분이 loading까지 동기적으로 처리된다면 javascript의 쓰레드는 이미지가 로딩될때까지 다른 작업을 처리할 수 없다. 로드가 끝나기 전까지 body에 이미지도 추가가 안되고, 콘솔도 안찍히고, body를 클릭해도 이벤트리스너의 실행이 되지 않는다. 말그대로 앱이 멈춰버리는거다.

```md
// 실행 순서
1. 이미지 생성 및 src 세팅
2. (이미지 로드 기다리기...)
3. body에 이미지 추가
4. 다음 코드들 실행
```

자바스크립트는 이런 상황을 위해서 내부적으로 비동기 처리(이미지 로딩)와 callback 방식을 채택하고 로드를 기다리지 않는다.

```js
document.body.onclick = function () {
  console.log('body 클릭');
}

const img = new Image();
img.onload = function () {
  document.body.append(img);
}
img.src = src;

console.log('src', src);
console.log('나는 다른 코드들');
```

이미지에 src를 세팅하면 이미지 로딩을 기다리지 않고 src만 세팅하고 작업을 완료한다. 그 후 이미지 로딩이 완료됐을때 callback을 실행하는 방식으로 앱이 멈추는걸 막는 것이다.
위 방식은 이미지 로딩이 되는 와중에도 console도 찍히고 이벤트리스너도 정상적으로 잘 실행된다.
```md
// 실행 순서
1. 이미지 생성 및 src 세팅
2. (이미지 로드를 기다리지 않음)
3. 다음 코드들 실행
4. (이미지 로딩이 완료 됐을때)
5. callback 실행 (body에 이미지 추가)
```

대표적인 비동기 처리로는 setTimeout, setInterval, load eventListener들이 있다.

Promise는 이런 비동기 처리를 조금 더 쉽게 사용하게 하려고 만들어진 비동기 작업의 성공, 실패를 나타내는 객체이다.
기존에는 콜백을 비동기 함수 파라미터로 넘기는 방식이라면, 프로미스는 콜백을 Promise에 추가적으로 붙이는 방식이다.
Promise는 3가지 상태를 가지는데 pending, fulfilled, rejected이다. (settled라는 것도 있는데 pending을 벗어난 상황(fulfilled, rejected)을 말한다)
- pending: 초기 상태
- fulfilled: 비동기 처리가 완료됐다는 뜻
- rejected: 비동기 처리가 실패했다는 뜻

Promise는 resolve, reject를 파라미터로 받는 실행 함수를 받은뒤 실행한다.
```js
new Promise((resolve, reject) => {
  setTimeout(() => {
    if (isOk) {
      resolve(1);
    } else {
      reject('some error');
    }
  }, 300);
});
```
callback은 Promise.then() 혹은 Promise.catch(), Promise.finally() 메소드를 통해 추가할 수 있다. 해당 메소드들 모두 Promise를 return 한다.

- then: 프로미스가 성공하면 onFulfilled 콜백을 실행하고, 실패하면 onRejected 콜백을 실행한다.
  - Syntax: Promise.then(onFulfilled, onRejected)
  - Return: 콜백의 결과 값을 Promise 값으로 return 한다.

- catch: 프로미스가 실패한 경우에만 onRejected 콜백을 실행한다.
  - Syntax: Promise.catch(onRejected)
  - Return: 콜백의 결과 값을 Promise 값으로 return 한다.

- finally: 프로미스가 settled되면 onFinally 콜백을 실행한다. try catch의 finally를 생각하면 된다.
  - Syntax: Promise.catch(onFinally)
  - Return: Promise의 값을 return 한다.


```js
promise
.then((num) => {
  console.log('success')!

  return num * 2;
})
.then((num) => {
  console.log('2가 곱해진 num', num);
})
.catch(err => {
  console.error(err);
});
```

Promise의 주요 특징은 then()을 여러번 사용해 콜백을 여러개 추가 할 수 있다는 점이다. 해당 특성을 이용한 프로미스 체이닝은 Promise의 주요 장점이다.

## 실제 예제

### 이미지 가져와서 캔버스에 그리기

```js
const loadImage = (src) => new Promise((res, rej) => {
  const img = new Image();

  img.onload = () => res(img);
  img.onerror = () => rej(img);

  img.src = src;
});

loadImage('/img.png')
.then((img) => {
  ctx.drawImage(img, 0, 0);
})
```

### http request

```js
const res = fetch('/api/400'); // fetch api는 Promise를 return 한다.

res
.then((res) => res.json())
.then(json => {
  console.log('response', json);
});

```

## Async, Await
단순히 Promise를 쉽게 사용한다고 생각해도 무방하다. async await도 사실 Promise에 then callback을 붙이는 것과 거진 동일하게 작동한다.

```js
const getItem = () => new Promise(res => {
  setTimeout(() => {
    res(1);
  }, 300);
})

// Async ver
async function app() {
  console.log('start');

  const item = await getItem();

  console.log(item);
  console.log('end');
}

app();

// Promise ver
function app() {
  console.log('start');

  getItem()
  .then((item) => {
    console.log(item);
    console.log('end');
  });
}

app();
```

위 코드로 볼 수 있듯이 getItem의 Promise response를 then 콜백 방식 대신 await 키워드를 통해 값으로 바로 받아올 수 있기 때문에 개발이 편해지고 가독성이 증가한다.
reject는 try catch를 사용해서 받아올 수 있다.
```js
async function app() {
  let item = null;
  try {
    item = await getItem();
  } catch (e) { // reject
    item = 'failed';
  }

  console.log(item);
}
```