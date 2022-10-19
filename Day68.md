# 20221019 TIL

## JavaScript 시작하기

## JavaScript를 배워야 하는 이유

> Web 기술의 기반이 되는 언어

- HTML 문서의 콘텐츠를 동적으로 변경할 수 있는 언어
- Web 공간에서 채팅, 게임 등 다양한 동작을 할 수 있게 된 기반

> 다양한 분야로 확장이 가능한 언어

- JavaScript는 Web을 위해 탄생한 언어로, 초기에는 언어의 특성 상 많은 개발자에게 환영받지 못함
- 하지만 버전이 올라가면서 하나의 단단한 언어로 자리매김
- Web조작을 넘어서 프로그래밍, 모바일 서비스, 컴퓨터 응용프로그래밍, 블록체인, 게임 등 다양한 분야에서 활용이 가능한 언어가 됨
- 다양한 직군에서 찾음

## JavaScript의 역사

- Web Browser와 깊은 연관관계

> 웹 브라우저의 역할

- URL을 통해 Web(WWW)을 탐색
- HTML, CSS, JavaScript를 이해한 뒤 해석해서 사용자에게 화면으로 보여줌

> 웹 브라우저와 스크립트 언어

- 웹 브라우저에 탑재해서 웹 페이지를 동적으로 바꿔줄 Script 언어 필요

  - Script 언어란 소스코드를 기계어로 바꿔주는 컴파일러 없이 바로 실행 가능한 언어.
  - 속도가 느림

- Netscape에서 10일의 개발 기간을 통해 Script 언어인 Mocha 개발
- 이후 LiveScript로 이름 변경 후 브라우저에 LiveScript를 해석해주는 Engine 내장
- JAVA의 명성에 기대고자 JavaScript로 이름 변경

> 정리

- 웹 브라우저는 JavaScript를 해석하는 엔진을 가지고 있음
- 현재 JavaScript는 자리를 잡았고, 개발에서 큰 축 담당
- 더이상 jQuery 등 라이브러리를 사용할 필요 없음(모든 웹 브라우저가 표준안을 따르기 때문)
- 특히 Chrome V8의 경우 JavaScript를 번역하는 속도가 매우 빠름

  - 물건이다. 다른 개발에서도 사용해보자
  - node.js, react.js, electron 등 내부엔진으로 사용
  - 그 결과, back-end, mobile, desktop app등 모두 JavaScript로 개발

## JavaScript 실행하기

> 개요

1. Web Browser로 실행하기
2. Node.js로 실행하기

> Web Browser로 실행하기

- Web Browser에는 JavaScript를 해석할 수 있는 엔진이 있어 실행할 수 있음
- HTML 파일에 직접 JavaScript 작성 후 웹 브라우저로 파일 열기
- .js 확장자를 가진 파일에 JavaScript를 작성하고 해당 파일을 HTML에 포함 가능
- 웹 브라우저의 console 에서 바로 JavaScript를 입력해도 된다.(엔진이 있기 때문)
- 특별하게 웹 브라우저에서 바로 실행할 수 있는 JavaScript 문법들을 Vanilla JavaScript라고 부름

  - 순수한 JavaScript라는 의미
  - 모든 아이스크림의 순정은 Vanilla 라는 어원

> Node.js로 실행하기

- 웹 브라우저를 이용하지 않고 JavaScript를 실행할 수 있음(엔진이 있기 때문)
- Node.js 설치 문서 참조

---

# JavaScript 기초 문법

## 코드 작성법

> 세미콜론(semicolon)

- 자바스크립트는 세미콜론을 선택적으로 사용 가능
- 세미콜론이 없으면 ASI에 의해 자동으로 세미콜론 삽입

  - ASI(Automatic Semicolon Insertion, 자동세미콜론 규칙)

- 본 수업에서는 세미콜론 X

> 들여쓰기와 코드블럭

- python은 4칸, JavaScript는 2칸 들여쓰기
- 블럭은 if, for, 함수에서 중괄호{} 내부를 말함

  - 파이썬은 들여쓰기를 이용해서 코드 블럭 ㄱ부ㅜㄴ
  - JavaScript는 중괄호{}를 사용해 코드 블럭 구분

> 코드 스타일 가이드

- 코드 스타일의 핵심은 합의된 원칙과 일관성
- 코드의 품질에 직결되는 중요한 요소

  - 코드의 가독성, 유지보수 또는 팀원과의 커뮤니케이션 등 개발 과정 전체에 영향

- Python에도 PEP8 이라는 코드 스타일 가이드가 있었듯, JavaScript에도 있음
- 여러 회사마다 여러 스타일 가이드가 존재하나, 수업에서는 Airbnb Style Guide 를 기반

> 다양한 JavaScript 코드 스타일 가이드

- Airbnb
- Google
- standard

> 주석

- 한 줄 주석(//), 여러 줄 주석(/\* \*/)

## 변수와 식별자

> 식별자 정의와 특징

- 식별자는 변수를 구분할 수 있는 변수명
- 식별자는 반드시 문자, 달러($) 또는 밑줄로 시작
- 대소문자 구분, 클래스 명 이외에 소문자로 시작
- 예약어 사용 불가

  - for, if, function 등

> 식별자 정의와 특징

- 카멜 케이스(calmelCase, lower-camel-case)

  - 변수, 객체, 함수에 사용

- 파스칼 케이스(PascalCase, upper-camel-case)

  - 클래스, 생성자에 사용

- 대문자 스네이크 케이스(SNAKE_CASE)

  - 상수(constants)에 사용
  - 상수 : 개발자의 의도와 상관없이 변경될 가능성이 없는 값

> 변수 선언 키워드

- Python과 다르게 JavaScript는 변수를 선언하는 키워드가 정해져 있음

1. let

   - 블록 스코프 지역 변수 선언(추가로 동시에 값 초기화)

2. const

   - 블록 스코프 읽기 전용 상수를 선언(추가로 동시에 값 초기화)

3. var

   - 변수를 선언(추가로 동시에 값 초기화)

> 선언, 할당, 초기화

- 선언(Declaration)

  - 변수를 생성하는 행위 또는 시점

- 할당(Assignment)

  - 선언된 변수에 값을 저장하는 행위 또는 시점

- 초기화(Initialization)

  - 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점

> 블록 스코프

- if, for, 함수 등의 중괄호 내부를 가리킴
- 블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가

> 변수 선언 키워드 - let

- let

  - 재할당 가능 & 재선언 불가능

    ```js
    let number = 10; // 1. 선언 및 초기값 할당
    number = 20; // 2. 재할당

    let number = 10;
    let number = 20; // 2. 재선언 불가능
    ```

- 블록 스코프를 갖는 지역 변수를 선언, 선언과 동시에 원하는 값으로 초기화 가능

> 변수 선원 키워드 - const

- const

  - 재할당 불가능 & 재선언 불가능

    ```js
    const number = 10; // 1. 선언 및 초기값 할당
    number = 10; // 2. 재할당 불가능

    const number = 10;
    const number = 20; // 2. 재선언 불가능
    ```

  - 선언 시 반드시 초기값을 설정해야 함, 이후 값 변경 불가능
  - let과 동일하게 블록 스코프

> 변수 선언 키워드 - var

- var

  - 재할당 가능 & 재선언 가능
  - ES6 이전에 변수 선언 시 사용되던 키워드
  - 호이스팅 되는 특성으로 인해 예기치 못한 문제 발생 가능

    - 따라서 ES6 이후로는 var 대신 const, let 사용 권장

  - 함수 스코프(function scope) 를 가짐

  - 변수 선언 시 var, const, let 키워드 중 하나를 사용하지 않으면 자동으로 var로 선언됨

> 함수 스코프(function scope)

- 함수의 중괄호 내부를 가리킴
- 함수 스코프를 가지는 변수는 함수 바깥에서 접근 불가능

> 호이스팅(hoisting)(끌어 올리다)

- 변수를 선언 이전에 참조할 수 있는 현상
- var로 선언된 변수는 선언 이전에 참조할 수 있으며, 이러한 현상을 호이스팅이라 함
- 변수 선언 이전의 위치에서 접근 시 undefined를 반환

```js
console.log(name); // undefined => 선언 이전에 참조

var name = "홍길동"; // 선언
```

```js
// 위 코드를 암묵적으로 아래와 같이 이해함
var name; // undefined로 초기화
console.log(name);

var name = "홍길동";
```

- 즉, JavaScript에서 변수들은 실제 실행 시에 코드의 최상단으로 끌어 올려지게 되며(hoisted) 이러한 이유 때문에 var 로 선언된 변수는 선언 시에 undefined로 값이 초기화되는 과정이 동시에 일어남
- 반면 let, const는 호이스팅이 일어나면 에러를 발생시킴

```js
console.log(username); // undefined
var username = "홍길동";

console.log(email); // Uncaught ReferenceError
let email = "gildong@gmail.com";

console.log(age); // Uncaught ReferenceError
const age = 50;
```

- 이것은 코드의 논리적인 흐름을 깨뜨리는 행위이며 이것을 방지하기 위해 let, const 추가

  - var는 사용하지 않아도 됨

- 다만, 아직까지 많은 기존의 JavaScript 코드는 ES6 이전의 문법으로 작성되어 있으므로 호이스팅에 대한 이해 필요

> 변수 선원 키워드 정리

- let : 재선언 X, 재할당 O, 블록스코프
- const : 재선언 X, 재할당 X, 블록스코프
- var : 재선언 O, 재할당 O, 함수스코프, 사용X

- 어디에 변수를 쓰고 상수를 쓸지 결정하는 것은 프로그래머의 몫
- Airbnb 스타일 가이드에서는 기본적으로 const

  - 재할당 해야 하는 경우만 let

## 데이터 타입

> 데이터 타입

- JavaScript의 모든 값은 특정한 데이터 타입
- 크게 원시 타입(Primitive type)과 참조 타입(Reference type)으로 분류됨

> Number

- 정수 또는 실수형 숫자를 표현하는 자료형

```js
const a = 13;
const b = -5;
const c = 3.14; // float - 숫자표현
const d = 2.998e8; // 2.998 * 10^8 = 299,800,000
const e = Infinity;
const f = -Infinity;
const g = NaN; // Not a Number
```

- NaN

  - Not-A-Number(숫자가 아님)
  - Number.isNaN()의 경우 주어진 값의 유형이 Number이고 값이 NaN이면 true, 아니면 false

    ```js
    Number.isNaN(NaN); // true
    Number.isNaN(0 / 0); // true
    ```

- NaN을 반환하는 경우

1. 숫자로서 읽을 수 없음(parseInt('어쩌구'), Number(undefined))
2. 결과가 허수
3. 피연산자가 NaN (7 \*\* NaN)
4. 정의할 수 없는 계산식(0 \* Infinity)
5. 문자열을 포함하면서 덧셈이 아닌 계산식('가' / 3)

> String

- 문자열을 표현
- 작은따옴표, 큰따옴표 모두 가능
- 곱셈, 나눗셈, 뺄셈은 안되지만 덧셈을 통해 문자열 합치기 가능

- Quote를 사용하면 선언 시 줄바꿈이 안됨
- 대신 escape sequence를 사용할 수 있기 때문에 \n 사용

```js
// Bad
const word = "안녕
하세요" // error

// Good
const word1 = "안녕 \n하세요"
console.log(word1)
```

- Template Literal을 사용하면 줄바꿈이 되며, 문자열 사이에 변수도 삽입도 가능
- 단, escape sequence 사용 불가능 == python 의 f-string

```js
const word2 = '안녕
들 하세요'
console.log(word2)

const age = 10
const message = '홍길동은 ${age}세입니다.'
console.log(message)
```

> Template literals(템플릿 리터럴)

- 내장된 표현식을 허용하는 문자열 작성 방식
- ES6+ 부터 지원
- Backtick('')을 이용하며, 여러 줄에 걸쳐 문자열 정의, JavaScript의 변수를 문자열 안에 바로 연결할 수 있는 이점
- 표현식을 넣을 수 있는데, 이는 $와 중괄호($ {expression})로 표기

```js
const age = 10;
const message = "홍길동은 ${age}세 입니다.";
```

> Empty Value

- 값이 존재하지 않음을 표현, JavaScript에서는 null과 undefined가 존재
- 동일한 역할을 하는 이 두개의 키워드가 존재하는 이유는 단순 JavaScript의 설계 실수
- 큰 차이를 두지 말고 interchangeable하게 사용할 수 있도록 권장

> null

- null 값을 나타내는 특별한 키워드
- 변수의 값이 없음을 의도적으로 표현

```js
let lastName = null;
console.log(lastName); // null - 의도적으로 값이 없음
```

> undefined

- 값이 정의되어 있지 않음
- 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당

```js
let firstName; // 선언만 하고 할당하지 않음
console.log(firstName); // undefined
```

> null과 undefined

- 차이점은 typeof 연산자를 통해 확인했을 때 나타남

```js
typeof null; // 'object'
typeof undefined; // 'undefined'
```

- null 이 원시 타입임에도 불구하고 object로 출력되는 이유는 JavaScript 설계 당시 버그를 지금까지 해결하지 못한 것
- 쉽게 해결할 수 없는 이유는 이미 null 타입에 의존성을 띄고 있는 많은 프로그램들이 망가질 수 있기 때문(하위 호환 유지)

> Boolean

- true, false
- 참과 거짓
- 조건문 또는 반복문에서 사용

  - 조건문 또는 반복문에서 boolean 이 아닌 데이터 타입은 자동 형변환 규칙에 따라 true 또는 false 로 변환됨

> ToBoolean Conversions(자동 형변환)

- undefined : 항상 거짓
- null : 항상 거짓
- Number : false = 0, -0, NaN // True : 나머지 모든 경우
- String : false = 빈 문자열 // True : 나머지 모든 경우
- Object : 항상 참

## 연산자

> 할당 연산자

- 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자
- 다양한 연산에 대한 단축 연산자 지원
- Increment 및 Decrement 연산자

  - Increment(++) : 피연산자의 값 1 증가
  - Decrement(--) : 피연산자의 값 1 감소
  - += 또는 -= 와 같이 더 분명한 표현으로 적을 것을 권장

```js
let c = 0;

c += 10;
console.log(c); // 10 - c에 10을 더한다

c -= 3;
console.log(c); // 7 - c에 3을 뺀다

c *= 10;
console.log(c); // 70 - c에 10을 곱한다

c++;
console.log(c); // 71 - c에 1을 더한다(증감식)

c--;
console.log(c); // 70 - c에 1을 뺀다(증감식)
```

> 비교 연산자

- 피연산자들(숫자, 문자, Boolean 등)을 비교하교 결과값을 boolean으로 반환
- 문자열은 유니코드 값을 사용하며 표준 사전 순서를 기반으로 비교

  - ex. 알파벳끼리 비교

    - 알파벳 순서상 후순위가 더 크다
    - 소문자가 대문자보다 크다

```js
3 > 2; // true
3 < 2; // false

"A" < "B"; // true
"Z" < "a"; // true
"가" < "나"; // true
```

> 동등 연산자(==)

- 두 연산자가 같은 값으로 평가되는지 비교 후 boolean 값 반환
- 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
- 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별
- 특별한 경우를 제외하고 사용하지 않음

```js
const a = 1;
const b = "1";

console.log(a == b); // true
console.log(a == true); // true

// 자동 형변환 예시
console.log(8 * null); // 0, null은 0
console.log("5" - 1); // 4
console.log("5" + 1); // '51'
console.log("five" * 2); // NaN
```

> 일치 연산자(===)

- 두 피연산자의 값과 타입이 모두 같은 경우 true
- 같은 객체를 가리키거나, 같은 타입이면서 같은 값인지 비교
- 엄격한 비교가 이루어지며 암묵적 타입 변환이 발생하지 않음

  - 엄격한 비교 : 두 비교 대상의 타입과 값 모두 같은지 비교

```js
const a = 1;
const b = "1";

console.log(a === b); // false
consolg.log(a === Number(b)); // true
```

> 논리 연산자

- 세 가지 논리 연산자로 구성

  - and 연산은 '&&'
  - or 연산은 '||'
  - not 연산은 '!'

- 단축 평가 지원

  - ex. false && true => false
  - ex. true || false => true

```js
true && false; // false
true && true; // true

false || true; // true
false || false; // false

!true; // false

1 && 0; // 0
0 && 1; // 0
4 && 7; // 7

1 || 0; // 1
0 || 1; // 1
4 || 7; // 4
```

> 삼항 연산자(Ternary Operator)

- 3개의 피연산자를 사용하여 조건에 따라 값을 반환하는 연산자
- 가장 앞의 조건식이 참이면 : 앞의 값이 반환되며, 그 반대일 경우 : 뒤의 값이 반환
- 삼항 연산자의 결과 값이기 때문에 변수에 할당 가능

```js
true ? 1 : 2; // 1
false ? 1 : 2; // 2

const result = Math.PI > 4 ? "Yep" : "Nope";
console.log(result); // Nope
```

## 조건문

> 조건문의 종류와 특징

- if statement

  - 조건 표현식의 결과값을 boolean 타입으로 변환 후 참/거짓 판단

- switch statement

  - 조건 표현식의 결과값이 어느 값(case)에 해당하는지 판별
  - 주로 특정 변수의 값에 따라 조건을 분기할 때 활용

    - 조건이 많아질 경우 if문보다 가독성이 나을 수 있음

> if statement

- if, else if, else

  - 조건은 소괄호(condition)안에 작성
  - 실행할 코드는 중괄호{}안에 작성
  - 블록 스코프 생성

```js
const name = "manager";

if (name === "admin") {
  console.log("관리자님 환영합니다.");
} else if (name === "manager") {
  console.log("매니저님 환영합니다.");
} else {
  console.log("${name}님 환영합니다.");
}
```

> switch statement

- 표현식(expression)의 결과값을 이용한 조건문
- 표현식의 결과값과 case문의 오른쪽 값을 비교
- break 및 default 문은 [선택적]으로 사용 가능
- break 문이 없는 경우 break 문을 만나거나 default 문을 실행할 때까지 다음 조건문 실행
- 블록 스코프 생성

```js
switch(expression) {
  case 'first value': {
    // do something
    [break]
  }
  case 'second value': {
    // do something
    [break]
  }
  [default : {
    // do something
  }]
}
```

> switch statement

- 이 경우 모든 console이 출력 (Fall-through)

```js
const name = "홍길동";

switch (name) {
  case "홍길동": {
    console.log("홍길동님 환영합니다.");
  }
  case "manager": {
    console.log("매니저님 환영합니다.");
  }
  default: {
    console.log("${name}님 환영합니다.");
  }
}
```

- break를 작성하면 의도한대로 동작

```js
const name = "홍길동";

switch (name) {
  case "홍길동": {
    console.log("홍길동님 환영합니다.");
    break;
  }
  case "manager": {
    console.log("매니저님 환영합니다.");
    break;
  }
  default: {
    console.log("${name}님 환영합니다.");
  }
}
```

> if / switch

- 조건이 많은 경우 switch 문을 통해 가독성 향상을 기대할 수 있음
- 일반적으로 중첩 else if 문은 유지보수하기 힘들다.

```js
const numOne = 5;
const numTwo = 10;
let operator = "+";

if (operator === "+") {
  console.log(numOne + numTwo);
} else if (operator === "-") {
  console.log(numOne - numTwo);
} else if (operator === "*") {
  console.log(numOne * numTwo);
} else if (operator === "/") {
  console.log(numOne / numTwo);
} else {
  console.log("유효하지 않은 연산자입니다.");
}
```

```js
const numOne = 5;
const numTwo = 10;
let operator = "+";

switch (operator) {
  case "+": {
    console.log(numOne + numTwo);
    break;
  }
  case "-": {
    console.log(numOne - numTwo);
    break;
  }
  case "*": {
    console.log(numOne * numTwo);
    break;
  }
  case "/": {
    console.log(numOne / numTwo);
    break;
  }
  default: {
    console.log("유효하지 않은 연산자입니다.");
  }
}
```

## 반복문

> 반복문 종류

- while
- for
- for...in
- for...of

> while

- 조건문이 참이김나 하면 문장을 계속해서 수행

```js
while (조건문) {
  // do something
}
```

- 예시

```js
let i = 0;

while (i < 6) {
  console.log(i);
  i += 1;
}

// 0, 1, 2, 3, 4, 5
```

> for

- 특정한 조건이 거짓으로 판별될 때까지 반복

```js
for ([초기문]; [조건문]; [증감문]) {
  // do something
}
```

- 예시

```js
for (let i = 0; i < 6; i++) {
  console.log(i);
}

// 0, 1, 2, 3, 4, 5
```

> for 동작 예시

```js
for (let i = 0; i < 6; i++) {
  console.log(i); // 0, 1, 2, 3, 4, 5
}
```

```js
// 1. 반복문 진입 및 변수 i 선언
for (let i = 0;)
```

```js
// 2. 조건문 평가 후 코드 블럭 실행
for (i < 6){
  console.log(i) // 0
}
```

```js
// 3. 코드 블록 실행 이후 i 값 증가
for (i ++)
```

> for ... in

- 객체(object)의 속성을 순회할 때 사용
- 배열도 순회 가능하나, 인덱스 순으로 순회한다는 보장이 없으므로 권장하지 않음

```js
for (variable in object) {
  statements;
}
```

- 예시

```js
const fruits = { a: "apple", b: "banana" };

for (const key in fruits) {
  console.log(key); // a, b
  console.log(fruits[key]); // apple, banana
}
```

> for ... of

- 반복 가능한 객체를 순회할 때 사용
- 반복 가능한(iterable) 객체의 종류 : Array, Set, String 등

```js
for (variable of object) {
  statements;
}
```

- 예시

```js
const numbers = [0, 1, 2, 3];

for (const number of numbers) {
  console.log(number); // 0, 1, 2, 3
}
```

> for ... in 과 for ... of 차이

- for ... in 은 속성 이름을 통해 반복
- for ... of 는 속성 값을 통해 반복

```js
const arr = [3, 5, 7];

for (const i in arr) {
  console.log(i); // 0 1 2
}
// 이것은 인덱스가 아님.
// 배열은 내부적으로 object이다.
// {0: 3, 1: 5, 2: 7} 이렇게 되어있다.

for (const i of arr) {
  console.log(i); // 3 5 7
}
```

- 다른 예

```js
// array

const fruits = ["딸기", "바나나", "메론"];

for (let fruit in fruits) {
  console.log(fruit); // 0, 1, 2
}

// object
const capitals = {
  Korea: "서울",
  France: "파리",
  USA: "워싱턴 D.C.",
};

for (let capital in capitals) {
  console.log(capital); // Korea, France, USA
}
```

```js
// array
const fruits = ["딸기", "바나나", "메론"];

for (let fruit of fruits) {
  console.log(fruit); // 딸기, 바나나, 메론
}

// object
const capitals = {
  Korea: "서울",
  France: "파리",
  USA: "워싱턴 D.C.",
};

for (let capital of capitals) {
  console.log(capital);
  // Uncaught TypeError: capitals is not iterable
}
```

> for ... in, for ... of 와 const

- 일반적인 for 문 for (let i = 0; i < arr.length; i++) {...}의 경우에는 최초 정의한 i를 재할당 하면서 사용하기 때문에 const 를 사용하면 에러 발생
- 다만 for ... in, for ... of 의 경우에는 재할당이 아니라, 매 반복 시 해당 변수를 새로 정의하여 사용하므로 에러가 발생하지 않음

> 조건문과 반복문 정리

- 키워드 // 종류 // 연관 키워드 // 스코프
- if // 조건문 // - // 블록 스코프
- switch // 조건문 // case, break, default // 블록 스코프
- while // 반복문 // break, continue // 블록 스코프
- for // 반복문 // break, continue // 블록 스코프
- for ... in // 반복문 // 객체 순회 // 블록 스코프
- for ... of // 반복문 // iterable 순회 // 블록 스코프

# 함수

> 개요

- 참조 타입 중 하나인 function 타입
- JavaScript에서 함수를 정의하는 방법은 주로 2가지

  - 함수 선언식(function declaration)
  - 함수 표현식(function expression)

## 함수의 정의

> 함수 선언식(Function declaration)

- 일반적인 프로그래밍 언어의 함수 정의 방식

```js
function 함수명() {
  // do something
}
```

- 예시

```js
function add(num1, num2) {
  return num1 + num2;
}

console.log(add(2, 7));
add(2, 7);
// 값을 확인하려면 console.log를 사용해야 값이 출력됨
```

> 함수 표현식(Function expression)

- 표현식 내에서 함수를 정의하는 방식
- 함수 표현식은 함수의 이름을 생략한 익명 함수로 정의 가능

```js
변수키워드 함수명 = function () {
  // do something
}
```

- 예시

```js
const sub = function (num1, num2) {
  return num1 - num2;
};

sub(7, 2); // 5
console.log(sub(7, 2));
```

- 함수 이름을 명시하는 것도 가능
- 다만 이 경우 함수 이름은 호출에 사용 되지 못하고 디버깅 용도로 사용

```js
const mySub = function namedSub(num1, num2) {
  return num1 - num2;
};

mySub(1, 2); // -1
namedSub(1, 2); // ReferenceError : namedSub is not defined
```

> 기본 인자(Default arguments)

- 인자 작성 시 '=' 문자 뒤 기본 인자 선언 가능

```js
const greeting = function (name = "Anonymous") {
  return "Hi ${name}";
};

greeting(); // Hi Anonymous
```

> 매개 변수와 인자의 개수 불일치 허용

- 매개 변수보다 인자의 개수가 많을 경우

```js
const noArgs = function () {
  return 0;
};

noArgs(1, 2, 3); // 0

const twoArgs = function (arg1, arg2) {
  return [arg1, arg2];
};

twoArgs(1, 2, 3); // [1, 2]
```

- 매개 변수보다 인자의 개수가 적을 경우

```js
const threeArgs = function (arg1, arg2, arg3) {
  return [arg1, arg2, arg3];
};

threeArgs(); // [undefined, undefined, undefined]
threeArgs(1); // [1, undefined, undefined]
threeArgs(1, 2); // [1, 2, undefined]
```

> Spread syntax(...)

- 전개 구문
- 전개 구문을 사용하면 배열이나 문자열과 같이 반복 가능한 객체를 배열의 경우는 요소, 함수의 경우는 인자로 확장할 수 있음

1. 배열과의 사용

```js
let parts = ["shoulders", "knees"];
let lyrics = ["head", ...parts, "and", "toes"];
// ['head', 'shoulders', 'knees', 'and', 'toes']
```

2. 함수와의 사용 (Rest parameters)

- 정해지지 않은 수의 매개변수를 배열로 받을 수 있음

```js
function func(a, b, ...theArgs) {
  //
}

const restOpr = function (arg1, arg2, ...restArgs) {
  return [arg1, arg2, restArgs];
};

restArgs(1, 2, 3, 4, 5); // [1, 2, [3, 4, 5]]
restArgs(1, 2); // [1, 2, []]
```

## 선언식과 표현식

> 함수의 타입

- 선언식 함수와 표현식 함수 모두 타입은 function으로 동일

```js
// 함수 표현식
const add = function (args) {};

// 함수 선언식
function sub(args) {}

console.log(typeof add); // function
console.log(typeof sub); // function
```

> 호이스팅 - 선언식

- 함수 선언식으로 정의한 함수는 var로 정의한 변수처럼 호이스팅 발생
- 즉 함수 호출 이후에 선언해도 동작

```js
add(2, 7); // 9

function add(num1, num2) {
  return num1 + num2;
}
```

> 호이스팅 - 표현식

- 반면 함수 표현식으로 선언한 함수는 함수 정의 전에 호출 시 에러 발생
- 함수 표현식으로 정의된 함수는 변수로 평가되어 변수의 scope 규칙을 따름

```js
sub(7, 2); // Uncaught ReferenceError: Cannot access 'sub' before initialization

const sub = function (num1, num2) {
  return num1 - num2;
};
```

> 선언식과 표현식 정리

- 선언식 : 익명함수 불가능, 호이스팅 있음
- 표현식 : 익명함수 가능, 호이스팅 없음, Airbnb Style Guide 권장 방식

## Arrow Function

> 화살표 함수(Arrow Function)

- 함수를 비교적 간결하게 정의할 수 있는 문법
- function 키워드와 중괄호를 이용한 구문을 짧게 사용하기 위해 탄생

  1. function 키워드 생략 가능
  2. 함수의 매개변수가 하나뿐이라면 '()'도 생략 가능
  3. 함수의 내용이 한 줄이라면 '{}'와 'return'도 생략 가능

- 화살표 함수는 항상 익명 함수

  - == 함수 표현식에서만 사용 가능

```js
const arrow1 = function (name) {
  return "hello, ${name}";
};

// 1. function 키워드 삭제
const arrow2 = (name) => {
  return "hello, ${name}";
};

// 2. 인자가 1개일 경우에만 () 생략 가능
const arrow3 = (name) => {
  return "hello, ${name}";
};

// 3. 함수 바디가 return을 포함한 표현식 1개일 경우에 { } & return 삭제 가능
const arrow4 = (name) => "hello, ${name}";
```

- 명확성과 일관성을 위해 항상 인자 주위에는 괄호('()')를 포함하는 것을 권장

> 화살표 함수 응용

```js
// 1. 인자가 없다면? () or _로 표시가능
let noArgs = () => "No args";
noArgs = (_) => "No args";

// 2-1. object 를 return 한다면
let returnObject = () => {
  return { key: "value" };
}; // return 을 명시적으로 적어준다.

// 2-2. return 을 적지 않으려면 괄호를 붙여야 한다.
returnObject = () => ({ key: "value" });
```

> 즉시 실행 함수(IIFE, Immediately Invoked Function Expression)

- 선언과 동시에 실행되는 함수
- 함수의 선언 끝에 '()'를 추가하여 선언되자 마자 실행하는 형태
- '()'에 값을 넣어 인자로 넘겨줄 수 있음
- 즉시 실행 함수는 선언과 동시에 실행되기 때문에 같은 함수를 다시 호출할 수 없음
- 이러한 특징을 살려 초기화 부분에 많이 사용
- 일회성 함수이므로 익명함수로 사용하는 것이 일반적

```js
(function (num) {
  return num ** 3;
})(2); // 8
```

```js
(num) => {
  return num ** 3;
};
```

```js
((num) => num ** 3)(2); // 8
```

# Array와 Object

> 개요

- JavaScript의 데이터 타입 중 참조 타입(reference)에 해당 하는 타입은 array와 object이며, 객체라고 말함
- 객체는 속성들의 모음(collection)

  - 객체 안쪽의 속성들은 메모리에 할당 되어있고 해당 객체는 메모리의 시작 주소 값을 가리키고 있는 형태

## 배열(Array)

> 배열(Array)

- 키와 속성들을 담고 있는 참조 타입의 객체(object)
- 순서를 보장
- 주로 대괄호, 0을 포함한 양의 정수 인덱스로 접근 가능
- 배열의 길이는 array.length 형태로 접근 가능

```js
const numbers = [1, 2, 3, 4, 5];

console.log(numbers[0]); // 1
console.log(numbers[-1]); // undefined
console.log(numbers.length); // 5
```

```js
const numbers = [1, 2, 3, 4, 5];

console.log(numbers[numbers.length - 1]); // 5
console.log(numbers[numbers.length - 2]); // 4
console.log(numbers[numbers.length - 3]); // 3
console.log(numbers[numbers.length - 4]); // 2
console.log(numbers[numbers.length - 5]); // 1
```

## 배열 메서드 기초

> 배열 메서드 기초

- reverse : 원본 배열의 요소들의 순서를 반대로 정렬
- push & pop : 가장 뒤에 요소를 추가 또는 제거
- unshift & shift : 가장 뒤에 요소를 추가 또는 제거
- includes : 배열에 특정 값이 존재하는지 판별 후 참/거짓 반환
- indexOf : 배열에 특정 값이 존재하는지 판별 후 인덱스 반환 // 요소가 없을 경우 -1 반환
- join : 배열의 모든 요소를 구분자를 이용하여 연결 // 구분자 생략 시 쉼표 기준

> 배열 메서드 기초

- array.reverse()

  - 원본 배열 요소들의 순서를 반대로 정렬

```js
const numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]
```

- array.push()

  - 배열의 가장 뒤에 요소 추가

- array.pop()

  - 배열의 마지막 요소 제거

```js
const numbers = [1, 2, 3, 4, 5];

numbers.push(100);
console.log(numbers); // [1, 2, 3, 4, 5, 100]

numbers.pop();
console.log(numbers); // [1, 2, 3, 4, 5]
```

- array.includes(value)

  - 배열에 특정 값이 존재하는지 판별 후 참 또는 거짓 반환

```js
const numbers = [1, 2, 3, 4, 5];

console.log(numbers.includes(1)); // true
console.log(numbers.includes(100)); // false
```

- array.indexOf(value)

  - 배열에 특정 값이 존재하는지 확인 후 가장 첫번째로 찾은 요소의 인덱스 반환
  - 해당 값이 없을 때 -1 반환

```js
const numbers = [1, 2, 3, 4, 5];
let result;

result = numbers.indexOf(3); // 2
console.log(result);

result = numbers.indexOf(100); // -1
console.log(result);
```

- array.join([seperator])

  - 배열의 모든 요소를 연결하여 반환
  - seperator(구분자)는 선택적으로 지정 가능, 생략 시 쉼표가 기본 값

```js
const numbers = [1, 2, 3, 4, 5];
let result;

result = numbers.join(); // 1,2,3,4,5
console.log(result);

result = numbers.join(""); // 12345
console.log(result);

result = numbers.join(" "); // 1 2 3 4 5
console.log(result);

result = numbers.join("-"); // 1-2-3-4-5
console.log(result);
```

## 배열 메서드 심화

> Array Helper Methods

- 배열을 순회하며 특정 로직을 수행하는 메서드
- 메서드 호출 시 인자로 callback 함수를 받는 것이 특징

  - callback 함수 : 어떤 함수의 내부에서 실행될 목적으로 인자로 넘겨받는함수

- forEach : 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행 // 반환 값 없음
- map : 콜백 함수의 반환 값을 요소로 하는 새로운 배열 반환
- filter : 콜백 함수의 반환 값이 참인 요소들만 모아서 새로울 배열 반환
- reduce : 콜백 함수의 반환 값들을 하나의 값(acc)에 누적 후 반환
- find : 콜백 함수의 반환 값이 참이면 해당 요소를 반환
- some : 배열의 요소 중 하나라도 판별 함수를 통과하면 참을 반환
- every : 배열의 모든 요소가 판별 함수를 통과하면 참을 반환

> Array Helper Methods - forEach

- array.forEach(callback(element[, index[, array]]))
- 인자로 주어지는 함수(콜백 함수)를 배열의 각 요소에 대해 한 번씩 실행

  - 콜백 함수는 3가지 매개변수로 구성

  1. element: 배열의 요소
  2. index: 배열 요소의 인덱스
  3. array: 배열 자체

- 반환 값 없음

```js
// 1. 일단 사용해보기

const colors = ["red", "blue", "green"];

printFunc = function (color) {
  console.log(color);
};
colors.forEach(printFunc);

// red
// blue
// green
```

```js
// 2. 함수 정의를 인자로 넣어보기

colors.forEach(function (color)) {
  console.log(color)
})
```

```js
// 3. 화살표 함수 적용하기
colors.forEach((color) => console.log(color));
```

> Array Helper Methods - map

- array.map(callback(element[, index[, array]]))
- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
- 콜백 함수의 반환 값을 요소로 하는 새로운 배열 반환
- 기존 배열 전체를 다른 형태로 바꿀 때 유용

```js
// 1. 일단 사용해보기

const numbers = [1, 2, 3];

// 함수 정의 (표현식)

const doubleFunc = function (number) {
  return number * 2;
};

// 함수를 다른 함수의 인자로 넣기(콜백 함수)

const doubleNumbers = numbers.map(doubleFunc);
console.log(doubleNumbers); // [2, 4, 6]
```

```js
// 2. 함수 정의를 인자로 넣어보기

const doubleNumbers = numbers.map(function (number) {
  return number * 2;
});
console.log(doubleNumbers); // [2, 4, 6]
```

```js
// 3. 화살표 함수 적용하기

const doubleNumbers = numbers.map((number) => number * 2);
console.log(doubleNumbers); // [2, 4, 6]
```

> Array Helper Methods - filter

- array.filter(callback(element[, index[, array]]))
- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
- 콜백 함수의 반환 값이 참인 요소들만 모아서 새로운 배열 반환
- 기존 배열의 요소들을 필터링할 때 유용

```js
// 1. 일단 사용해보기

const products = [
  { name: "cucumber", type: "vegetable" },
  { name: "banana", type: "fruit" },
  { name: "carrot", type: "vegetable" },
  { name: "apple", type: "fruit" },
];

// 함수 정의하고
const fruitFilter = function (product) {
  return product.type === "fruit";
};

// 콜백으로 넘기고
const fruits = products.filter(fruitFilter);

console.log(fruits);
// [ { name: 'banana', type: 'fruit' }, { name: 'apple', type: 'fruit' } ]
```

```js
// 2. 함수 정의를 인자로 넣어보기

const fruits = products.filter(function (product) {
  return product.type === "fruit";
});
```

```js
// 3. 화살표 함수 적용하기

const fruits = products.filter((product) => product.type === 'fruit)
```

> Array Helper Methods - reduce

- array.reduce(callback(acc, element, [index[, array]])[, initialValue])
- 인자로 주어지는 함수(콜백 함수)를 각 요소에 대해 한 번씩 실행해서, 하나의 결과 값을 반환
- 즉, 배열을 하나의 값으로 계산하는 동작이 필요할 때 사용(총합, 평균 등)
- map, filter 등 여러 배열 메서드 동작을 대부분 대체할 수 있음

- reduce 메서드의 주요 매개 변수

  - acc

    - 이전 callback 함수의 반환 값이 누적되는 변수

  - initialValue(optional)

    - 최초 callback 함수 호출 시 acc에 할당되는 값, default 값은 배열의 첫 번째 값

- reduce의 첫 번째 매개변수인 콜백함수의 첫 번째 매개변수('acc')는 누적된 값(전 단계까지의 결과)
- reduce의 두 번째 매개변수인 'initialValue'는 누적될 값의 초기값, 지정하지 않을 시 첫 번째 요소의 값
- 빈 배열의 경우 initialValue를 제공하지 않으면 에러 발생

```js
// 이제부터는 바로 콜백 함수를 정의해보자

const tests = [90, 90, 80, 77];

// 총합
const sum = tests.reduce(function (total, x) {
  return total + x;
}, 0); // 여기서 0 생략 가능

// 화살표 함수
const sum = tests.reduce((total, x) => total + x, 0);

// 평균
const sum = tests.reduce((total, x) => total + x, 0) / tests.length;
```

- reduce 동작 방식

```js
const numbers = [1, 2, 3];

const result = numbers.reduce((acc, num) => {
  return acc + num;
}, 0);

// 0 + 1
// 1 + 2
// 3 + 3
// 결과 6
```

> Array Helper Methods - find

- array.find(callback(element[, index[, array]]))
- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
- 콜백 함수의 반환 값이 참이면, 조건을 만족하는 첫 번째 요소를 반환
- 찾는 값이 배열에 없으면 undefined 반환

```js
const avengers = [
  { name: "Tony Stark", age: 45 },
  { name: "Steve Rogers", age: 32 },
  { name: "Thor", age: 40 },
];

const avenger = avengers.find(function (avenger) {
  return avenger.name === "Tony Stark";
});

// refactoring
const avenger = avengers.find((avenger) => avenger.name === "Tony Stark");
```

> Array Helper Methods - some

- array.some(callback(element[, index[, array]]))
- 배열의 요소 중 하나라도 주어진 판별 함수를 통과하면 참을 반환
- 모든 요소가 통과하지 못하면 거짓 반환
- 빈 배열은 항상 false 반환

```js
const arr = [1, 2, 3, 4, 5];

const result = arr.some((elem) => elem % 2 === 0); // true
```

> Array Helper Methods - every

- array.every(callback(element[, index[, array]]))
- 배열의 모든 요소가 주어진 판별 함수를 통과하면 참을 반환
- 하나의 요소라도 통과하지 못하면 거짓 반환
- 빈 배열은 항상 true

```js
const arr = [1, 2, 3, 4, 5];

const result2 = arr.every((elem) => elem % 2 === 0); // false
```

> 배열 순회 비교

```js
const chars = ["A", "B", "C", "D"];

// for loop
for (let idx = 0; idx < chars.length; idx++) {
  console.log(idx, chars[idx]);
}

// for ... of
for (const char of chars) {
  console.log(char);
}

// forEach

chars.forEach((char, idx) => {
  console.log(idx, char);
});

chars.forEach((char) => {
  console.log(char);
});
```

- for loop

  - 모든 브라우저 환경 지원
  - 인덱스를 활용하여 배열의 요소 접근
  - break, continue 사용 가능

- for ... of

  - 일부 오래된 브라우저 환경에서는 지원 X (단점이라고 볼 수 없음)
  - 인덱스 없이 배열의 요소에 바로 접근 가능
  - break, continue 사용 가능

- forEach

  - 대부분 브라우저에서 지원
  - break, continue 사용 불가능
  - Airbnb Style Guide 권장 방식

# 객체(Object)

> 개요

- 객체는 속성(property)의 집합이며, 중괄호 내부에 key와 value의 쌍으로 표현
- key 는 문자열 타입만 가능

  - key 이름에 띄어쓰기 등의 구분자가 있으면 따옴표로 묶어서 표현

- value 는 모든 타입(함수 포함) 가능
- 객체 요소 접근은 점(.) 또는 대괄호([])로 가능

  - key 이름에 띄어쓰기 같은 구분자가 있으면 대괄호 접근만 가능

> 객체(Object) 예시

```js
const me = {
  name: "jack",
  phoneNumber: "01012345678",
  "samsung products": {
    buds: "Galaxy Buds pro",
    galaxy: "Galaxy s99",
  },
};

console.log(me.name)
console.log(me.phoneNumber)
console.log(me.['samsung products'])
console.log(me.['samsung products'].buds)
```

# 객체 관련 문법

> 객체 관련 ES6 문법 익히기

- ES6에 새로 도입된 문법들로 객체 생성 및 조작에 유용하게 사용 가능

1. 속성명 축약
2. 메서드명 축약
3. 계산된 속성명 사용하기
4. 구조 분해 할당
5. 객체 전개 구문(Spread Operator)

> 1. 속성명 축약

- 객체를 정의할 때 key와 할당하는 변수의 이름이 같으면 예시와 같이 축약 가능

```js
var books = ["Learning JavaScript", "Learning Python"];
var magazines = ["Vogue", "Science"];

// ES5
var bookShop = {
  books: books,
  magazines: magazines,
};
console.log(bookShop);

/*
{
  books: ['Learning JavaScript', 'Learning Python'],
  magazines : ['Vogue', 'Science']
}
*/
```

```js
const books = ["Learning JavaScript", "Learning Python"];
const magazines = ["Vogue", "Science"];

// ES6+
const bookShop = {
  books,
  megaines,
};
console.log(bookShop);

/*
{
  books: ['Learning JavaScript', 'Learning Python'],
  magazines : ['Vogue', 'Science']
}
*/
```

> 2. 메서드명 축약

- 메서드 선언 시 function 키워드 생략 가능

```js
// ES5
var obj = {
  greeting: function () {
    console.log("Hi!");
  },
};

obj.greeting(); // Hi!
```

```js
// ES6+
const obj = {
  greeting() {
    console.log("Hi!");
  },
};

obj.greeting(); // Hi!
```

> 3. 계산된 속성(computed property name)

- 객체를 정의할 때 key의 이름을 표현식을 이용하여 동적으로 생성 가능

```js
const key = "country";
const value = ["한국", "미국", "일본", "중국"];

const myObj = {
  [key]: value,
};

console.log(myObj); // { country: [ '한국', '미국', '일본', '중국' ] }
console.log(myObj.country); // [ '한국', '미국', '일본', '중국' ]
```

> 4. 구조 분해 할당(destructing assignment)

- 배열 또는 객체를 분해하여 속성을 변수에 쉽게 할당할 수 있는 문법

- 구조 분해 할당을 하지 못할 때

```js
const userInformation = {
  name: "ssafy kim",
  userId: "ssafyStudent1234",
  phoneNumber: "010-1234-1234",
  email: "ssafy@ssafy.com",
};

const name = userInformation.name;
const userId = userInformation.userId;
const phoneNumber = userInformation.phoneNumber;
const email = userInformation.email;
```

- 구조 분해 할당 후

```js
const userInformation = {
  name: "ssafy kim",
  userId: "ssafyStudent1234",
  phoneNumber: "010-1234-1234",
  email: "ssafy@ssafy.com",
};

const { name } = userInformation;
const { userId } = userInformation;
const { phoneNumber } = userInformation;
const { email } = userInformation;

// 여러개도 가능
const { name, userId } = userInformation;
```

> 5. Spread syntax (...)

- 배열과 마찬가지로 전개구문을 사용해 객체 내부에서 객체 전개 가능
- 얕은 복사에 활용 가능

```js
const obj = { b: 2, c: 3, d: 4 };
const newObj = { a: 1, ...obj, e: 5 };

console.log(newObj); // {a: 1, b: 2, c: 3, d: 4, e: 5}
```

> JavaScriptON(JavaScript Object Notation)

- Key-Value 형태로 이루어진 자료 표기법
- JavaScript의 Object와 유사한 구조를 가지고 있지만 Object는 그 자체로 타입이고, JavaScriptON은 형식이 있는 문자열
- 즉, JavaScriptON을 Object로 사용하기 위해서는 변환 작업이 필요

```js
const JavaScriptObject = {
  coffee: "Americano",
  iceCream: "Cookie and cream",
};
```

```js
// Object -> JavaScriptON

const objToJavaScripton = JSON.stringify(JavaScriptObject);

console.log(objToJavaScripton); // {'coffee':'Americano','iceCream':'Cookie and cream'}
console.log(typeof objToJavaScripton); // string

// JavaScriptON -> Object

const JsonToObj = JSON.parse(objToJavaScripton);

console.log(JsonToObj); // { coffee: 'Americano', iceCream: 'Cookie and cream'}
console.log(typeof JsonToObj); // object
```

> 배열은 객체다

- 키와 속성들을 담고 있는 참조 타입의 객체(object)
- 배열은 인덱스를 키고 갖으며 length 프로퍼티를 갖는 특수한 객체

```js
Object.getOwnPropertyDescriptors([1, 2, 3]);

/*
{
  '0': { value: 1, writable: true, enumerable: true, configurable: true},
  '1': { value: 2, writable: true, enumerable: true, configurable: true},
  '2': { value: 3, writable: true, enumerable: true, configurable: true},
  length: : { value: 3, writable: true, enumerable: false, configurable: false},
}
*/
```

# 마무리

- JavaScript 기초 문법

  - 세미콜론
  - 들여쓰기와 코드 블럭
  - 스타일가이드
  - 변수와 식별자
  - 타입과 연산자

    - 원시 자료형

  - 조건문
  - 반복문

- 함수

  - 선언식과 표현식
  - 화살표 함수

- Array와 Object

  - 배열

    - Array Helper Method

  - 객체

    - ES6+ 객체 문법
