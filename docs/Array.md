# Array 문서

자세한 부분은 각각의 mdn 문서를 참고한다.

## 용어

- 아이템: 배열의 값
- 파라미터: 함수로 넘기는 값
- 콜백 함수: 파라미터로 넘겨지고 실행되는 함수 (파라미터는 보통 (element, index, array))
- 콜백 함수 통과: 콜백 함수의 실행 값이 true가 나오는지 여부

##### Table of Contents

- [length](#Array.prototype.length)
- [concat](#Array.prototype.concat)
- [every](#Array.prototype.every)
- [fill](#Array.prototype.fill)
- [filter](#Array.prototype.filter)
- [find](#Array.prototype.find)
- [flat](#Array.prototype.flat)
- [forEach](#Array.prototype.forEach)
- [includes](#Array.prototype.includes)
- [join](#Array.prototype.join)
- [map](#Array.prototype.map)
- [reduce](#Array.prototype.reduce)
- [reverse](#Array.prototype.reverse)
- [slice](#Array.prototype.slice)
- [some](#Array.prototype.some)
- [sort](#Array.prototype.sort)
- [some](#Array.prototype.some)

---

<a name="Array.prototype.length"/>

## Array.prototype.length

배열의 아이템 수를 나타낸다.

```js
const arr = [1, 2, 3];

arr.length; // 3

arr.length = 5; // arr = [1, 2, 3, empty, empty]; (empty = 해당 index에 아이템이 아예 없다는 뜻. 순회를 도는 함수들도 empty는 아이템이 없기 때문에 건너뜀)

arr.length = 1; // arr = [1];
```

<a name="Array.prototype.concat"/>

## Array.prototype.concat

배열과 파라미터 값을 합쳐서 새 배열을 반환한다. <br />
파라미터가 없으면 기존 배열을 복사한 새 배열을 반환한다.

```js
// Syntax: concat(value1, value2, value3, ...valueN);
const arr = [1, 2, 3];

arr.concat([4, 5, 6]); // [1, 2, 3, 4, 5, 6]
arr.concat([4, 5, 6], [7, 8, 9]); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
arr.concat(4); // [1, 2, 3, 4]
arr.concat(4, [5, 6]); // [1, 2, 3, 4, 5, 6]

console.log(arr); // [1, 2, 3]
```

<a name="Array.prototype.every"/>

## Array.prototype.every

배열의 모든 아이템이 콜백함수를 통과하면 true를 아니면 false를 반환한다.

```js
// Syntax: every((element, index, array) => {});
const arr = [1, 2, 3];

arr.every((num) => num > 0); // true
arr.every((num) => num > 1); // false (1이 false)
arr.every((num) => num < 3); // false (3이 false)
```

<a name="Array.prototype.fill"/>

## Array.prototype.fill

배열을 시작 index에서 부터 끝 index - 1 까지 특정 값 하나로 채운다. <br />
변경된 기존 배열을 반환한다.

```js
// Syntax: fill(value, start, end);
const arr = [1, 2, 3, 4];

arr.fill(1); // arr = [1, 1, 1, 1];
arr.fill(0, 2); // arr = [1, 1, 0, 0];
arr.fill(99, 1, 2); // arr = [1, 99, 0, 0];
```

<a name="Array.prototype.filter"/>

## Array.prototype.filter

배열의 아이템중 콜백 함수를 통과하는 아이템들만 모아 새로운 배열을 반환한다.

```js
// Syntax: filter((element, index, array) => {});
const arr = [1, 2, 3, 4];

arr.filter((v) => v === 2); // [2]
arr.filter((v) => v < 2); // [1]
arr.filter((v) => v % 2); // [1, 3]
```

<a name="Array.prototype.find"/>

## Array.prototype.find

배열의 아이템중 콜백 함수를 통과하는 첫 번째 아이템을 반환한다. 없으면 undefined를 반환.

```js
// Syntax: find((element, index, array) => {})

const arr = [{ a: 1 }, { a: 2 }, { a: 3 }];

arr.find((ele) => ele.a === 3); // { a: 3 }
arr.find((ele, idx) => idx === 0); // { a: 1 }
```

<a name="Array.prototype.flat"/>

## Array.prototype.flat

다중차원의 배열을 파라미터로 받은 depth 값 만큼 평탄화 시킨다. <br />
depth의 기본값은 1이다.

```js
// Syntax: flat(depth);

const arr = [1, 2, 3, [4, 5, [6, 7, [8, 9]]]];

arr.flat(); // [1,2,3,4,5,[6,7,[8,9]]];
arr.flat(2); // [1,2,3,4,5,6,7,[8,9]];
arr.flat(Infinity); // [1,2,3,4,5,6,7,8,9];
```

<a name="Array.prototype.forEach"/>

## Array.prototype.forEach

배열의 모든 요소를 가지고 콜백 함수로 실행한다. <br />
undefined를 리턴하기 때문에 method chaining의 중간에 사용할 수 없다.

```js
// Syntax: forEach((element, index, array) => {});

const arr = [1, 2, 3, 4];

arr.forEach((ele) => {
  console.log(ele);
}); // 1 2 3 4

let cnt = 0;
arr.forEach((ele) => {
  cnt++;
});
console.llog(cnt); // 4
```

<a name="Array.prototype.includes"/>

## Array.prototype.includes

배열이 특정 아이템을 포함하고 있는지를 체크한다. <br />
두번째 인자로 받는 값은 체크를 시작할 위치이다. (optional)

```js
// Syntax: includes(value, fromIndex)

const arr = [1, 2, 3, 4, "hi"];

arr.includes(1); // true
arr.includes(4); // true
arr.includes(false); // false
arr.includes("hi"); // true
arr.includes("HI"); // false

// index 1부터 찾기 시작하기 때문에 false가 나온다.
arr.includes(1, 1); // false
```

<a name="Array.prototype.join"/>

## Array.prototype.join

배열의 아이템들을 연결해 문자열로 만든다.

```js
const arr = [1, 2, 3, 4];

arr.join(); // 1,2,3,4
[].join(); // ''
[].join(","); // ''
```

<a name="Array.prototype.map"/>

## Array.prototype.map

배열의 모든 요소들의 콜백 함수 반환값을 배열로 반한한다.

```js
// Syntax: map((element, index, array) => {});

const arr = [1, 2, 3, 4];

arr.map((ele) => ele + 1); // [2,3,4,5]
arr.map((ele) => "Hi"); // ['Hi','Hi','Hi','Hi']
arr.map((ele, idx) => idx); // [0,1,2,3]
```

<a name="Array.prototype.reduce"/>

## Array.prototype.reduce

배열의 모든 요소를 가지고 리듀서 함수를 실행하고 결과값을 반환한다. <br />
빈 배열에서 초기값 없이 reduce를 호출하면 오류가 발생한다.

```js
// Syntax: reduce((accumulator, element, index, array) => {}, initialValue);
// accumulator: 저장된 리듀서 함수의 결과값
// initialValue: 리듀서 함수를 처음 실행할때 accumulator의 값. 제공하지 않으면 배열의 첫 아이템을 accumulator 값으로 사용한다.

const arr = [1, 2, 3, 4];

arr.reduce((acc, ele) => acc + ele, 0); // 10 (1 + 2 + 3 + 4)
arr.reduce((acc, ele, idx) => {
  acc[`key${idx}`] = ele;

  return acc;
}, {}); // { key0: 1, key1: 2, key2: 3, key3: 4 }
```

<a name="Array.prototype.reverse"/>

## Array.prototype.reverse

배열의 순서를 반전한다. <br />
원본 배열을 변형시키니 유의해야 한다.

```js
const arr = [1, 2, 3, 4];

arr.reverse(); // [4,3,2,1];

console.log(arr); // [4,3,2,1];
```

<a name="Array.prototype.slice"/>

## Array.prototype.slice

배열의 시작 index에서 부터 끝 index - 1 까지를 복사한 배열을 반환한다. <br />
start가 없으면 0부터 시작한다. <br />
end가 없으면 끝까지 (arr.length) 복사한다.

```js
// Syntax: slice(start, end);

const arr = [1, 2, 3, 4];

arr.slice(); // [1,2,3,4];
arr.slice(1); // [2,3,4]
arr.slice(2, 3); // [3]
```

<a name="Array.prototype.some"/>

## Array.prototype.some

every가 모든 아이템이 콜백함수를 통과하는지 체크하는 거라면 some은 하나의 요소라도 통과하는지 체크한다.

```js
// Syntax: some((element, index, array) => {});
const arr = [1, 2, 3];

arr.some((num) => num > 0); // true
arr.some((num) => num > 1); // true
arr.some((num) => num < 3); // true
arr.some((num) => num === 4); // false
```

<a name="Array.prototype.sort"/>

## Array.prototype.sort

배열을 비교 함수의 return 값에 따라 정렬한 후 배열을 반환한다. 정렬 함수가 없을 경우 unicode순으로 정렬한다. <br />
return 값이 0보다 작은 경우 a를 b보다 앞으로 정렬한다. <br />
return 값이 0을 반환하면 변경하지 않고 넘어간다. <br />
return 값이 0보다 큰 경우 b를 a보다 앞으로 정렬한다.
기존 배열이 변경되니 주의해야 한다.

```js
// Syntax: sort((a, b) => {})
/*
  숫자 오름차순 정렬
  function (a, b) {
    if (a < b) {
      return -1;
    }

    if (a > b) {
      return 1;
    }

    return 0;
  }
  function (a, b) {
    return a - b;
  }
*/

const arr = [3, 2, 1];

arr.sort((a, b) => a - b); // [1,2,3]

console.log(arr); // [1,2,3]
```

<a name="Array.prototype.some"/>

## Array.prototype.some

배열의 아이템을 삭제, 변경, 추가하고 배열을 변경한다. <br />
반환값은 삭제된 배열이다. <br />
deleteCount 값이 없으면 배열의 끝까지 삭제 한다.

```js
// Syntax: splice(start, deleteCount, item1, item2, item3, item4, ... itemN);

let arr = [1, 2, 3, 4];

arr.splice(2); // [3,4];
console.log(arr); // [1,2]

arr = [1, 2, 3, 4];
arr.splice(0, 2); // [1,2]
console.log(arr); // [3,4]

arr = [1, 2, 3, 4];
arr.splice(2, 1, "add item", "add item2"); // [3]
console.log(arr); // [1,2,'add item', 'add item2', 4];
```
