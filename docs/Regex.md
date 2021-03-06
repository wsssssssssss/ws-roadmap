# 정규 표현식

특정 문자에 대응하는 일정한 패턴. 이라고 짧게 말할 수 있겠다. <br />
정규 표현식은 접근하기는 어렵지만 알면 꽤 쉽다할 수 있다. (간단한 경우에만. 무슨 이상한 패턴으로 들어가기 시작하면 머리가 부서지려 한다.) <br />
Javascript에서는 RegExp 생성자로 생성하거나 /표현식값/ 이런식으로 / 사이에 값을 넣어서 만들 수 있다. (이런걸 **리터럴**이라 한다.) <br />

## 자세한 설명
정규표현식의 패턴으로는 모든 텍스트값은 다 들어갈 수 있다. 일부 문자들은 특별한 의미를 가지고 있는데 고건 다다음에 알아보고 일단 예시를 보면서 이해해보자. <br />

```js
cosnt firstRegex = /abc/;
// 위처럼 regex를 선언하면 abc에 대응하는 정규 표현식이 만들어진다. 자바스크립트 정규표현식 메소드는 아래를 참고하자.
// https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp#%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4_%EB%A9%94%EC%84%9C%EB%93%9C
// RegExp.prototype.test라는 메소드가 있는데 이 메소드는 파라미터로 받은 값이 정규표현식에 만족하는지 판별한다.

firstRegex.test('abc'); // true (abc는 알맞은 값이므로 true를 return한다.)
firstRegex.test('abcdefg'); // true (정규표현식에 알맞는 값이 존재하므로 true를 return한다.)
firstRegex.test('ABC'); // false (대문자로 되어 있기 떄문에 패턴에 알맞지 않는다.)
```

위 코드에서 볼 수 있듯이 패턴을 만들고 패턴을 이용해 값 판별을 주로 하고 이 외에도 문자열 검색, 변경 등등등 여러가지를 할 수 있다. <br />
위 예제만 보면 되게 단순한 녀석이지만 정규표현식의 특수문자들을 사용하는 순간부터 난이도가 올라간다. <br /> <br />

단순히 한가지 케이스에 대응해야 한다면 상관 없지만 만약에 abbc, abbbc, abbbbbc, abbbb.....(무수히 많은 b)...bbc, abc 이렇게 b가 여러번 들어가는 경우를 위한 패턴을 만들어야 한다면 모든 케이스의 패턴을 만들어야 할거다. 이처럼 유동적인 케이스에 대응하기 위해 정규 표현식은 특수문자들을 가지고 있다. <br />

| 특수문자  | 설명 |
| ------------- | ------------- |
| ^  | 문장의 시작에 대응한다. <br /> 만약 [] 내부의 첫글자로 쓰이면 괄호 내부의 문자가 아닌 문자들에 대응한다. (이 부분은 아래에서 추가로 설명)   |
| $  | 문장의 마지막에 대응한다.  |
| *  | {0,}와 같은 의미로 앞의 표현이 0번 이상 반복된다는 뜻이다. <br /> 예를 들어 /ab*c/ 의 경우에는 <ul><li>ac 처럼 b가 0개 있으면 만족한다.</li><li>abbbbbc 처럼 b가 5개 있으면 만족한다.</li><li>ab의 경우 b가 있지만 c가 없으므로 만족하지 않는다.</li></ul> |
| +  | {1,}와 같은 의미로 앞의 표현이 1번 이상 반복된다는 뜻이다. <br /> 예를 들어 /ab+c/ 의 경우에는 <ul><li>ac 처럼 b가 0개 있으면 만족하지 않는다</li><li>abc 처럼 b가 1개 있으면 만족한다.</li><li>abbbbbc 처럼 b가 5개 있으면 만족한다</li></ul> |
| ?  | {0,1}와 같은 의미로 앞의 표현이 0번 또는 1번 반복된다는 뜻이다. <br /> 예를 들어 /ab?c/ 의 경우에는 <ul><li>ac 처럼 b가 0개 있으면 만족한다.</li><li>abc 처럼 b가 1개 있으면 만족한다.</li><li>abbbbbc 처럼 b가 5개 있으면 만족하지 않는다</li></ul> |
| .  | 모든 문자(줄바꿈을 제외한)를 뜻한다. <br /> 예를 들어 /.+/ 의 경우에는 아무 문자나 1개 이상 있으면 만족한다는 뜻이다.  |
| \  | 뒤에서 나올 특수문자들을 문자 그대로 해석하도록 한다. <br /> /\\*/ 의 경우 특수문자 \*이 아니라 "\*"에 대응하게 된다. |
| \|  | \|의 앞뒤에 있는 표현중 하나에 대해서 만족한다는 뜻이다. <br /> 예를 들어 /a\|b/ 의 경우에는 <ul><li>a: 만족</li><li>b: 만족</li><li>c: 불만족</li></ul> |
| {n}  | 앞의 표현이 n번 반복된다는 뜻이다. n은 양의 정수(+)여야 한다. <br /> 예를 들어 /a{2}/ 의 경우에는 <ul><li>a: 불만족</li><li>aa: 만족</li><li>aac: 만족</li></ul> |
| {n,m}  | 앞의 표현이 n번 ~ m번 반복된다는 뜻이다. m은 n보다 크거나 같아야 한다. m이 없다면 m은 무한대값으로 자동 설정된다 (최소 n번만 있으면 대응한다는 뜻). <br /> 예를 들어 /a{2,3}/ 의 경우에는 <ul><li>a: 불만족</li><li>aa: 만족</li><li>aac: 만족</li><li>aaa: 만족</li><li>aaaac: 만족</li></ul> <br /> /a{2,}/ 의 경우에는 <ul><li>a: 불만족</li><li>aa: 만족</li><li>aac: 만족</li><li>aaa: 만족</li><li>aaaac: 만족</li></ul> <br /> 위 두가지 예시에서 중요한 점은 {2,3}은 "aa" 혹은 "aaa"만 대응이 되지만 {2,}는 "aa", "aaa", "aaaaaaa" 상관없이 전부 대응이 된다는 점이다. <br /> "aaaaaaaaaa"라는 문자열이 있을때 /a{2,3}/은 "\`aaa\`aaaaaaa" 백틱 부분이 대응이 돼서 test를 통과한다. 하지만 /a{2,}/의 경우 "\`aaaaaaaaaa\`" 문자열 전체가 대응이 돼서 통과한다. |
| [xyz]  | 문자의 집합(Character set)이다. 괄호 내의 문자들에 대응된다. <br /> 괄호 내에서는 특수문자들이 괄호 밖에서와 달리 일반 문자가 되기 때문에 이스케이프(\\) 시킬 필요가 없다. \\를 붙이면 다시 특수문자처럼 동작한다. <br /> 하이픈을 이용한 문자의 범위 지정도 할 수 있다. <ul><li>/[a-d]/: [abcd]와 동일하게 동작한다.</li><li>/[0-9]/: [0123456789]와 동일하게 동작한다.</li><li>/[0-9.]+/: [0123456789.]와 동일하게 동작한다. <br /> <ul><li>"123.": 만족</li><li>"...": 만족</li><li>"1234567890": 만족</li></ul></li></ul> |
| [^xyz]  | 위 "^" 설명에서 설명한 부정 문자 집합이다. 괄호 내부에 없는 어떤 문자에나 대응한다. <br /> 문자 집합과 동일하게 하이픈으로 범위를 지정할 수 있다. <br /> 예를 들어 /[^abc]/의 경우에는 <br /> <ul><li>abcd: d가 만족한다.</li><li>abc: 불만족한다.</li><li>aaa: 불만족</li></ul> |
| (xyz)  | 캡쳐링 그룹이라 불리는 이 패턴은 괄호 내의 값에 대응하고 그 값을 저장한다. <br /> 저장된 값은 정규식 내에서는 \n으로 사용이 가능하다. n 값은 캡쳐링 그룹이 몇번째 인지를  뜻한다. 추후에 replace 부분에서는 \index 대신 $index를 사용한다. $&의 경우는 문자열 전체를 가르킨다. <br /> 예를 들어 /(a)\1\1/ 의 경우에는 <ul><li>aa 처럼 a가 2개 있으면 만족하지 않는다.</li><li>aaabcasd 처럼 a가 3개 연속으로 있으면 만족한다.</li></ul>  예를 들어 /(abc)\1\1/ 의 경우에는 <ul><li>abc 처럼 "abc"가 1개 있으면 만족하지 않는다.</li><li>abcabcabc 처럼 "abc"가 3개 연속으로 있으면 만족한다.</li></ul> |
| (?:x)  | 비캡쳐링 그룹이라 불리는 이 패턴은 캡쳐링 그룹과 동일하지만 값을 저장하지 않는다. 캡쳐링 그룹과 저장 유무를 제외하고는 동일하게 동작한다. <br /> 캡쳐링 그룹 대신 비캡쳐링 그룹을 사용하면 약간의 성능 향상을 얻을 수 있다. |
| a(?=b)  | "a"뒤에 b가 있을때에만 "a"에 대응한다. <br /> 예를 들어 /(web)(?=skills)/ 의 경우에는 <ul><li>webskills 처럼 web뒤에 skills가 있으면 web이 대응하게 된다.</li><li>skillswebb 처럼 web뒤에 skills가 없으면 만족하지 않는다.</li></ul> |
| a(?!b)  | "a"뒤에 b가 없을때에만 "a" 에 대응한다. a(?=b)와 반대로 동작한다 생각하면 된다. |
| \w | (word) [a-zA-Z0-9_]와 동일하다. |
| \W | \w의 반대 값으로 [^a-zA-Z0-9_]와 동일하다. |
| \s | (space) space, tab, enter등 공백에 대응한다. |
| \S | \s의 반대 값으로 공백 문자가 아닌 모든 문자에 대응한다. |
| \d | 숫자에 대응한다. [0-9]와 동일하다. |

## 플래그를 사용한 검색
/[a-z]/ 뒤에 플래그를 추가하면 좀 더 쉽게 검색을 할 수 있다. g, i 외에도 m, s, u, y가 있지만 딱히 쓸일이 없으므로 스킵한다.

| 특수문자  | 설명 |
| ------------- | ------------- |
| g | 전체 검색이라는 뜻으로 한번만 대응하지 않고 전체에 대응하게 된다. /abc/g 처럼 g가 붙으면 "abcabcabc"의 모든 "abc"에 대응하게 된다. |
| i | 검색할때 대소문자 구분을 안한다는 뜻. /a/i 라면 aA 상관없이 대응한다. |

## 예제

- /[a-zA-Z0-9]+/: 문자열에 대소문자 영어, 숫자만 있다면 전체 문자열에 대응한다.
- /^([\w\.-]+)@([\w-]+\.)+[a-z]{2,4}$/: Id 부분은 \w,마침표,하이픈만 허용된다. 도메인 네임 부분은 \w와 -로 이루어져 있고, 최상위 도메인은 영문 2~4글자가 된다.
