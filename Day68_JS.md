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
