# Convention

## CSS
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

## Javascript
- === 사용하기
- singleQuote 사용하기
- 네이밍은 constCase
- 변경되지 않는 값은 const
- 변경되는 값은 let
- 함수는 arrow function ( \_ => {} )
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
6. (기타 init에서만 쓰이는 함수들)
7. init 선언
8. window.onload = init();