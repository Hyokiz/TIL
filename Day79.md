# 20221106 TIL

# JavaScript 기초 문법

## 코드 작성법

> 세미콜론

- 자바스크립트는 세미콜론을 선택적으로 사용 가능
- 세미콜론이 없으면 ASI에 의해 자동으로 세미콜론이 삽입됨

  - ASI(Automatic Semicolon Insertion, 자동 세미콜론 삽입 규칙)

> 들여쓰기와 코드 블럭

- JavaScript는 2칸
- 블럭(block)은 중괄호 내부

> 주석

- 한줄 주석(//), 여러줄 주석(/* */)

# 변수와 식별자

> 식별자 정의와 특징

- 식별자(identifier)는 변수를 구분할 수 있는 변수명
- 식별자는 반드시 문자, 달러($) 또는 밑줄(_)로 시작
- 대소문자 구분, 클래스 명 외에는 모두 소문자

> 식별자 정의와 특징

- 카멜 케이스(camelCase)

  - 변수, 객체, 함수

- 파스칼 케이스(PascalCase)

  - 클래스, 생성자

- 대문자 스네이크 케이스(SNAKE_CASE)

  - 상수(constants)에 사용
  - 상수 : 변경될 가능성이 없는 값

> 변수 선언 키워드

1. let

   - 블록 스코프 지역 변수 선언(값 초기화)

2. const

   - 블록 스코프 읽기 전용 상수 선성(값 초기화)

3. var

   - 변수 선언(값 초기화)

> 선언, 할당, 초기화

- 선언(Declaration)

  - 변수를 생성하는 행위 또는 시점

- 할당(Assignment)

  - 선언된 변수에 값을 저장하는 행위 또는 시점

- 초기화(Initialization)

  - 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점

> 블록 스코프(block scope)

- if, for, 함수 등의 중괄호 내부
- 블록 바깥에서 접근 불가능

> 변수 선언 키워드 - let

- let 

  - 재할당 가능, 재선언 불가능
  - 블록 스코프를 갖는 지역 변수 선언

- const

  - 재할당 불가능, 재선언 불가능
  - 선언시 반드시 초기값을 설정해야 하며 이후 값 변경 불가능
  - 블록 스코프를 가짐

- var

  - 재할당 가능, 재선언 가능
  - 호이스팅 특성으로 인해 예기치 못한 문제 발생 가능
  - 함수 스코프를 가짐

> 함수 스코프

- 함수의 중괄호 내부
- 함수 스코프를 가지는 변수는 함수 바깥에서 접근 불가능

> 호이스팅

- 변수를 선언 이전에 참조할 수 있는 현상
- var로 선언된 변수는 선언 이전에 참조할 수 있음
- 변수 선언 이전의 위치에서 접근 시 undefined를 반환
- 이러한 이유 때문에 var로 선언된 변수는 선언 시 undefined로 값이 초기화
- let, const는 호이스팅이 일어나면 에러 발생

> 변수 선언 키워드 정리

- let : 재선언 X, 재할당 O, 블록스코프, ES6부터
- const : 재선언 X, 재할당 X, 블록 스코프, ES6부터
- var : 재선언 O, 재할당 O, 함수 스코프, 사용X

- Airbnb 스타일 가이드에서는 기본적으로 const 사용 권장

  - 재할당 해야하는 경우만 let

# 데이터 타입

> 데이터 타입

- 원시 타입, 참조 타입으로 분류됨

> Number 

- 정수 또는 실수형 숫자를 표현하는 자료형

- NaN

  - Not-A-Number(숫자가 아님)
  - Number.isNaN()의 경우 주어진 값의 유형이 Number이고 값이 NaN이면 true, 아니면 false

- NaN을 반환하는 경우

1. 숫자로서 읽을 수 없음
2. 결과가 허수인 수학 계산식
3. 피연산자가 NaN
4. 정의할 수 없는 계산식
5. 문자열을 포함하면서 덧셈이 아닌 계산식

> String

- 문자열을 표현하는 자료형
- 작은 따옴표 또는 큰 따옴표
- 덧셈을 통해 문자열을 붙일 수 있음
- Quote를 사용하면 선언 시 줄 바꿈이 안됨("", '')
- \n을 사용해야 함
- Template Literal(``) 사용 시 줄바꿈이 되며, 변수 삽입 가능하나, escape sequence를 사용할 수 없다.

> Template literals(템플릿 리터럴)

- 내장된 표현식을 허용하는 문자열 작성 방식
- Backtick(``)을 이용, 여러 줄에 걸쳐 문자열 정의 가능
- 표현식을 넣을 수 있음, 이는 $와 중괄호로 표기

> Empty Value

- null과 undefined가 존재
- 동일한 역할을 하는 이는 JavaScript의 실수

> null

- null 값을 나타내는 특별한 키워드
- 변수 값이 없음을 의도적으로 표현

> undefined

- 값이 정의되어 있지 않음
- 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당됨

> null 과 undefined

- 대표적인 차이는 typeof 를 통해 확인 가능

  - null 은 object 타입
  - undefined는 undefined

- unll이 원시 타입임에도 불구하고 object로 출력된느 이유는 javascript 설계 당시 버그를 아직 해결하지 못한 것
- 쉽게 해결하지 못한 이유는 이미 null 타입에 의존성을 띄고 있는 많은 프로그램들이 망가질 수 있기 때문

> Boolean

- true 와 false
- 참과 거짓을 표현
- 조건문 및 반복문에서 유용하게 사용

  - boolean이 아닌 데이터 타입은 자동 형변환 규칙으로 인해 true 또는 false로 변환됨

# 연산자

> 할당 연산자

- 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자

> 비교 연산자

- 피연산자들(숫자, 문자, Boolean 등)을 비교하고 결과값을 boolean으로 반환
- 문자열은 유니코드 값을 사용하며 표준 사전 순서를 기반으로 비교

  - ex. 알파벳끼리 비교

    - 순서상 후순위가 더 크다.
    - 소문자가 대문자보다 더 크다.

> 동등 연산자(==)

- 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 반환
- 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
- 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별
- 예상치 못한 결과가 발생할 수 있으므로 특별한 경우를 제외하고 사용하지 않음

> 일치 연산자(===)

- 두 피연산자의 값과 타입이 모두 같은 경우 true를 반환
- 같은 객체를 가리키거나, 같은 타입이면서 같은 값인지를 비교
- 엄격한 비교가 이루어지며 암묵적 타입 변환이 발생하지 않음

  - 엄격한 비교 : 두 비교 대상의 타입과 값 모두 같은지 비교

> 논리 연산자

- 세 가지

  - and 연산은 &&
  - or 연산은 ||
  - not 연산은 !

- 단축 평가 지원

  - false && true => false
  - true || false => true

> 삼항 연산자(Ternary Operator)

- 3개의 피연산자를 활용하여 조건에 따라 값을 반환하는 연산자

# 조건문

> 조건문의 종류와 특징

- if statement

  - 조건 표현식의 결과값을 boolean 타입으로 변환 후 참/거짓을 판단

- switch statement

  - 조건 표현식의 결과값이 어느 값(case)에 해당하는 지 판별
  - 주로 특정 변수의 값에 따라 조건을 분기할 때 활용

> it statement

- if, else, if, else

  - 조건은 소괄호(condition)안에 작성
  - 실행할 코드는 중괄호 안에
  - 블록 스코프 생성

> switch statement

- 표현식의 결과값을 이용한 조건문
- 결과값과 case문의 오른쪽 값을 비교
- break, default 문은 선택적으로
- 블록 스코프 생성

> if / switch

- 조건이 많은 경우 switch 문을 통해 가독성 향상
- 일반적으로 중첩 else if 문은 유지보수하기 힘듦

# 반복문

> while

- 참이면 계속해서 수행

> for

- 특정한 조건이 거짓으로 판별될 때까지 반복

> for ... in 

- 객체(object)의 속성을 순회할 때 사용
- 배열도 순회 가능

> for ... of

- 반복 가능한 객체를 순회할 때 사용
- 반복 가능한(iterable) 객체의 종류 : Array, Set, String

> for ... in과 for ... of 차이

- for ... in은 속성 이름을 통해 반복
- for ... of는 속성 값을 통해 반복

> for ... in, for ... of 와 const

- for 문

  - for (let i = 0; i < arr.length; i++) 의 경우 최초 i를 재할당 하면서 사용하기 때문에 const를 사용하면 에러 발생

- for ... in, for ... of

  - 재할당이 아니고 매 반복 시 해당 변수를 새로 정의하여 사용하므로 에러 발생 X

# 함수

> 개요

- 참조 타입 중 하나로써 function 타입에 속함
- JavaScript에서 함수를 정의하는 방법은 주로 2가지

  - 함수 선언식
  - 함수 표현식

## 함수의 정의

> 함수 선언식

- 일반적인 프로그래밍 언어의 함수 정의 방식

```js
function 함수명() {
    // do sth
}
```

> 함수 표현식

- 표현식 내에서 함수를 정의하는 방식
- 함수 표현식은 함수의 이름을 생략한 익명 함수로 정의 가능

```js
변수 키워드 함수명 = function () {
    //do sth
}
```

- 함수 이름을 명시하는 것도 가능
- 디버깅을 위해 사용하는 것

```js
const mySub = function namedSub(num1, num2) {
    return num1 - num2
}

mySub(1, 2) // -1
namedSub(1, 2) // ReferenceError : namedSub is not defined
```

> 기본 인자(Default arguments)

- 인자 작성 시 "=" 문자 뒤 기본 인자 선언 가능

```js
const greeting = function (name = 'Anonymous') {
    return `Hi ${name}`
}

greeting() // Hi Anonymous
```

> 매개변수와 인자의 개수 불일치 허용

- 매개변수보다 인자의 개수가 많을 경우

```js
const noArgs = function () {
    return 0
}

noArgs(1, 2, 3) // 0
```

- 매개변수보다 인자의 개수가 적을 경우

```js
const threeArgs = function (arg1, arg2, arg3) {
    return [arg1, arg2, arg3]
}

threeArgs() // [undefined, undefined, undefined]
threeArgs(1) // [1, undefined, undefined]
threeArgs(1, 2) // [1, 2, undefined]
```

> Spread syntax(...)

- 전개 구문
- 배열이나 문자열과 같이 반복 가능한 객체를 배열의 경우는 요소, 함수의 경우는 인자로 확장할 수 있음

1. 배열과의 사용

```js
let parts = ['shoulders', 'knees']
let lyrics = ['head', ...parts, 'and', 'toes']
// ['head', 'shoulders', 'knees', 'and', 'toes']
```

2. 함수와의 사용(Rest parameters)

- 정해지지 않은 수의 매개변수를 배열로 받을 수 있음

```js
const restOpr = function (arg1, arg2, ...restArgs) {
    return [arg1, arg2, restArgs]
}

restArgs(1, 2, 3, 4, 5) // [1, 2, [3, 4, 5]]
rsetArgs(1, 2) // [1, 2, []]
```

# 선언식과 표현식

> 함수의 타입

- 선언식 함수와 표현식 함수 모두 타입은 function으로 동일

```js
// 함수 표현식
const add = function (args) {}

// 함수 선언식
funtion sub(args) {}

console.log(typeof add) // function
console.log(typeof sub) // function
```

> 호이스팅 - 선언식

- 함수 선언식으로 정의한 함수는 var로 정의한 변수처럼 호이스팅이 발생
- 함수 호출 이후에 선언해도 동작

```js
add(2, 7) // 9

function add (num1, num2) {
    return num1 + num2
}
```

> 호이스팅 - 표현식

- 반면 함수 표현식으로 선언한 함수는 함수 정의 전에 호출 시 에러 발생
- 함수 표현식으로 정의된 함수는 변수로 평가되어 변수의 scope 규칙을 따름

# Arrow Function

> 화살표 함수(Arrow Function)

- 함수를 비교적 간결하게 정의할 수 있는 문법
- function 키워드와 중괄호를 이용한 구문을 짧게 사용하기 위해 탄생

  1. function 키워드 생략 가능
  2. 함수의 매개변수가 하나 뿐이라면 매개변수의 () 생략 가능
  3. 함수의 내용이 한 줄이라면 {}와 return 도 생략 가능

- 화살표 함수는 항상 익명 함수

  - ===함수 표현식에서만 사용 가능

> 화살표 함수 예시

```js
const arrow1 = function (name) {
    return `hello, ${name}`
}

// 1. function 키워드 삭제
const arrow2 = (name) => { return `hello, ${name}` }

// 2. 인자가 1개일 경우에만 () 생략 가능
const arrow3 = name => { return `hello, ${name}` }

// 3. 함수 바디가 return 을 포함한 표현식 1개일 경우에 {} & return 삭제 가능
const arrow4 = name => `hello, ${name}`
```

> 화살표 함수 응용

```js
// 1. 인자가 없다면? () or _로 표시 가능
let noArgs = () => 'No args'
noArgs = _ => 'No args'

// 2-1. object를 return 한다면
let returnObject = () => { return { key: 'value'} } // return을 명시적으로 적어준다.

// 2-2. return 을 적지 않으려면 괄호를 붙여야 함
returnObject = () => ({ key: 'value' })
```

> 즉시 실행 함수(IIFE, Immediately Invoked Function Expression)

- 선언과 동시에 실행되는 함수
- 함수의 선언 끝에 ()를 추가하여 선언되자마자 실행하는 형태
- ()에 값을 넣어 인자로 넘겨줄 수 있음
- 선언과 동시에 실행되기 때문에 같은 함수를 다시 호출할 수 없음
- 익명 함수로 사용하는 것이 일반적

```js
(function (num) { return num ** 3 })(2) // 8
(num => num ** 3)(2) // 8 
```

# Array 와 Object

> 개요

- JavaScript의 데이터 타입 중 참조 타입(reference)에 해당 하는 타입은 Array와 Object이며, 객체라고도 말함
- 객체는 속성들의 모음(collection)

# 배열(Array)

> 배열

- 키와 속성들을 담고 있는 참조 타입의 객체
- 순서를 보장
- 주로 대괄호로 생성, 0을 포함한 양의 정수 인덱스로 특정 값에 접근 가능
- 배열의 길이는 array.length 형태로 접근 가능

  - 마지막 요소는 -1로 접근

## 배열 메서드 기초

- array.reverse()

  - 반대로 정렬

- array.includes(value)

  - 배열에 특정 값(value)이 존재하는지 판별 후 true or false 반환

- array.indexOf(value)

  - 배열에 특정 값이 존재하는지 확인 후 가장 첫 번째로 찾은 요소의 인덱스 반환
  - 없을 경우 -1

- array.join([separator])

  - 배열의 모든 요소를 연결하여 반환
  - separator(구분자)는 선택적으로 지정 가능하며, 생략 시 쉼표를 기본값으로 사용

## 배열 메서드 심화

> Array Helper Methods

- 배열을 순회하며 특정 로직을 수행하는 메더스
- 메서드 호출 시 인자로 callback 함수를 받는 것이 특징

  - callback 함수 : 어떤 함수의 내부에서 실행될 목적으로 인자로 넘겨받는 함수

> forEach

- 인자로 주어지는 함수(콜백 함수)를 배열의 각 요소에 대해 한 번씩 실행

  - 콜백함수 는 3가지 매개변수로 구성

  1. element : 배열의 요소
  2. index : 배열 요소의 인덱스
  3. array : 배열 자체

- 반환 값 없음

> map

- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
- 콜백 함수의 반환 값을 요소로 하는 새로운 배열 반환
- 기존 배열 전체를 다른 형태로 바꿀 때 유용

  - forEach + return

> filter

- 콜백 함수의 반환 값이 true인 요소들만 모아서 새로운 배열 반환
- 기존 배열의 요소들을 필터링

> reduce

- 하나의 결과 값을 반환
- 배열을 하나의 값으로 계산하는 동작이 필요할 때(총합, 평균)
- map, filter등 여러 배열 메서드 동작을 대부분 대체할 수 있음
- 주요 매개 변수

  - acc

    - 이전 callback 함수의 반환 값이 누적되는 변수

  - initialValue

    - 최초 callback 함수 호출 시 acc에 할당되는 값, default 값은 배열의 첫 번째 값

> find

- 콜백 함수의 반환 값이 true이면, 조건을 만족하는 첫 번째 요소 반환
- 찾는 값이 없으면 undefined

> some

- 하나라도 통과하면 true
- 모든 요소가 통과하지 못하면 false
- 빈 배열은 항상 false

> every

- 모든 요소가 통과하면 true
- 하나라도 통과하지 못하면 false
- 빈 배열을 true

# 객체(Object)

> 개요

- 객체는 속성의 집합, 중괄호 내부에 key와 value의 쌍으로 표현

- key

  - 문자열 타입만
  - key 이름에 띄어쓰기 등의 구분자가 있으면 따옴표로 묶어서 표현

- value

  - 모든 타입 가능

- 객체 요소 접근

  - 점 또는 대괄호
  - key 이름에 띄어쓰기 같은 구분자가 있으면 대괄호 접근만 가능

# 객체 관련 문법

> ES6 문법 익히기

1. 속성명 축약
2. 메서드명축약
3. 계산된 속성명 사용
4. 구조 분해 할당
5. 객체 전개 구문

> 1. 속성명 축약

- 객체를 정의할 때 key와 할당하는 변수의 이름이 같으면 축약 가능

> 2. 메서드명 축약

- 메서드 선언 시 function 키워드 생략 가능

> 3. 계산된 속성

- 객체를 정의할 때 key의 이름을 표현식을 이용하여 동적으로 생성 가능

> 4. 구조 분해 할당

- 배열 또는 객체를 분해하여 속성을 변수에 쉽게 할당할 수 있는 문법

> 5. Spread syntax(...)

- 배열과 마찬가지로 전개구문을 사용해 객체 내부에서 객체 전개 가능
- 얕은 복사

> JSON

- Key-Value 형태로 이루어진 자료 표기법
- JSON을 Object로 사용하기 위해서는 변환 작업 필요

> JSON 변환

- JSON.stringfy(sth) 로 Object -> JSON 변환
- JSON.parse(sth) 로 JSON -> Object 변환

> 배열은 객체다

- 배열은 키와 속성들을 담고 있는 객체

