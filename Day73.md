# 20221025 TIL

## DOM

- Tree 구조로 이루어져 있는 문서
- 장고의 경우 새로고침을 해야 바뀐다.
- javascript의 경우 DOM의 api 속성을 바꿀 수 있다.

> DOM API

- DOM을 조작할 수 있는 메뉴판이다.

## THIS 

- window는 전역 객체이다.
- 객체는 key, value로 이루어져 있다.

```js
const func = function () {
  console.log(this)
}

const obj = {
  method : func,
}

func() // window
obj.method() // {method: f}
obj['method']() // {method: f}
```

> this

1. 전역에서는 window를 가리킨다.
2. 함수에서는 다음과 같다.

   - 함수로 호출할때는 window를 가리킨다.
   - 메서드로 호출할 때는 앞 객체를 가리킨다.

> 심화

```js
const obj = {
  methodA: function () {
    console.log(this)
  },
  innerObj: {
    methodB : function () {
      console.log(this)
    }
  }
}

obj.methodA() // {innerObj: {_}, methodA: f}
obj.innerObj.methodB() // {methodB: f}
```

```js
const obj1 = {
  outer: function () {
    console.log(this) // obj1 {outer: f}

    const innerFunc = function () {
      console.log(this) // window
    }
    innerFunc()

    const obj2 = {
      innermethod: innerFunc,
    }
    obj2.innerMethod() // obj2 {innerMethod: f}
  }
}

obj1.outer()
```

- ES6 이후로

3. bind를 통한 명시

```js
const test = {
  a: 1,
}

const obj1 = {
  outer: function () {
    console.log(this)
  }

  const innerFunc = function () {
    console.log(this)
  }.bind(test)
  innerFunc() // this -> test
}

obj1.outer() // this -> obj1
```

4. 화살표 함수

- 상위의 this를 자동적으로 가리키게 됨
- 호출 기준이 아닌 선언 기준

```js
const obj1 = {
  outer: function () {
    console.log(this)
  }
  const innerFunc = () => {
    console.log(this)
  }
  innerFunc() // this -> obj1
}

obj1.outer() // this -> obj1
```

> 예제

```js
const test = {
  a: "hello",
  b: "world",
}

const obj1 = {
  outer: function() {
    console.log(this) // test -> bind(test) 가 걸려있기 때문에 test
  }

  const innerFunc = () => {
    console.log(this) // test -> 상위의 this를 가리키고 있는데 상위가 test를 가리키고 있으므로 똑같이 test 
  innerFunc() 
  }.bind(test)
}

obj1.outer()
```

5. 콜백함수에서의 this는 각각 다름

- 콜백함수 : 제어권을 넘길 때 쓰는 함수
- 일반적으로 콜백 함수도 함수 호출이므로 this는 전역 객체
- addEventListener에서 콜백 함수 안의 this는 이벤트가 발생하는 html 요소
- 콜백 함수를 제어하는 함수에서 this를 명시적으로 지정 가능한 것도 있음 (ex. Array Helper Method)

```js
const func = function () {
  console.log("hello!")
}
func() // hello!

setTimeout(func, 5000) // 시간 지연
```

## 정리

> this 가 가리키는 것

- 함수로 호출하면 전역 객체, 메서드로 호출하면 .(dot)앞의 객체
- 화살표 함수에서는 스코프 체인 상 가장 가까운 상위의 this
- bind로 this를 명시적으로 지정 가능
- 혹은 변수에 임의로 객체를 할당하여 this 키워드 대신 해당 변수를 사용하여 명시 지정 가능
- 콜백 함수에서의 this 는 다름

  - 일반적으로 콜백 함수도 함수 호출이므로 this는 전역 객체
  - addEventListener에서 콜백 함수 안의 this 는 이벤트가 발생하는 html 요소
  - 콜백 함수를 제어하는 함수에서 this를 명시적으로 지정 가능한 것도 있음(ex. Array Helper Method)