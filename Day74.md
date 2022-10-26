# 20221026 TIL

# 동기와 비동기

## 동기(Synchronous)

> 동기

- 모든 일을 순서대로 하나씩 처리 하는 것
- 순서대로 처리한다 == 이전 작업이 끝나면 다음 작업 시작
- 작성했던 Python 코드가 모두 동기시

```py
print('첫 번째 작업')
for i in range(10):
  print('두 번째 작업')
  print(i)
print('세 번째 작업')
```

- 요청과 응답을 동기식으로 처리한다면?

  - 요청을 보내고 응답이 올때까지 기다렸다가 다음 로직을 처리

## 비동기

> 비동기(Asynchronous)

- 작업을 시작한 후 결과를 기다리지 않고 다음 작업을 처리하는 것(병렬적 수행)
- 시간이 필요한 작업들은 요청을 보낸 뒤 응답이 빨리 오는 작업부터 처리
- ex. gmail 메일 전송 시 메일 목록 화면으로 전환되지만 메일을 보내는 작업은 병렬적으로 뒤에서 처리

> 비동기를 사용하는 이유

- 사용자 경험

  - 아주 큰 데이터를 불러온 뒤 실행되는 앱이 있을 때 동기로 처리한다면 사용자들은 마치 앱이 멈춘 것과 같은 경험을 겪게 됨
  - 즉 동기식 처리는 특정 로직이 실행되는 동안 다른 로직 실행을 차단하기 때문에 마치 프로그램이 응답하지 않는 듯한 사용자 경험을 만들게 됨
  - 비동기로 처리한다면 먼저 처리되는 부분부터 보여줄 수 있으므로, 사용자 경험에 긍정적인 효과를 볼 수 있음

# JavaScript의 비동기 처리

> Single Thread 언어, JavaScript

- 여러 작업을 동시에 처리하면 안되나?
- JavaScript는 한 번에 하나의 일만 수행할 수 있는 Single Thread 언어. 동시에 여러 작업을 처리할 수 없다.
- Thread란?

  - 작업을 처리할 때 실제로 작업을 수행하는 주체, multi-thread라면 업무를 수행할 수 있는 주체가 여러 개라는 의미

- 즉, JavaScript는 하나의 작업을 요청한 순서대로 처리할 수 밖에 없다. 근데 어떻게 비동기 처리를 할까?

> JavaScript Runtime

- JavaScript자체는 Single Thread이므로 비동기 처리를 할 수 있도록 도와주는 환경이 필요함
- 특정 언어가 동작할 수 있는 환경을 "런타임(runtime)"이라고 함
- JavaScript에서 비동기와 관련한 작업은 브라우저 또는 Node 환경에서 처리
- 브라우저 환경에서 비동기 동작 구분

1. JavaScript Engine의 Call Stack
2. Web API
3. Task Queue
4. Event Loop

> 비동기 처리 동작 방식

- 브라우저 환경에서의 JavaScript 의 비동기 처리

1. 모든 작업은 Call Stack(LIFO)으로 들어간 후 처리된다.
2. 오래 걸리는 작업이 Call Stack으로 들어오면 Web API로 보내 별도로 처리하도록 한다.
3. Web API에서 처리가 끝난 작업들은 곧바로 Call Stack으로 들어가지 못하고 Task Queue(FIFO)에 순서대로 들어간다.
4. Event Loop가 Call Stack이 비어 있는 것을 계속 체크하고 Call Stack이 빈다면 Task Queue에서 가장 오래된(앞에 있는) 작업을 Call Stack으로 보낸다.

> 비동기 처리 동작 방식

1. Call Stack

- 요청이 들어올 때마다 순차적으로 처리하는 Stack(LIFO)
- 기본적인 JavaScript의 Single Thread 작업 처리

2. Web API

- JavaScript 엔진이 아닌 브라우저에서 제공하는 runtime 환경으로 시간이 소요되는 작업을 처리(setTimeout, DOM Event, AJAX 요청 등)

3. Task Queue

- 비동기 처리된 Callback 함수가 대기하는 Queue(FIFO)

4. Event Loop

- Call Stack과 Task Queue를 지속적으로 모니터링
- Call Stack이 비어 있는지 확인 후 비어 있다면 Task Queue에서 대기 중인 오래된 작업을 Call Stack으로 Push

> 그림으로 보는 비동기 처리

- 현재 3초라고 가정하였지만, Call Stack의 처리가 3초 이상이 걸릴경우 더 걸릴수도 있다. 따라서 최소 시간을 보장하는 것.

- 3초라는 것은 Web API에서 3초 후에 Task Queue로 보낸다는 것

- setTimeout을 0으로 한다고 해도 똑같다.

## JavaScript의 비동기 처리 정리

- JavaScript는 한 번에 하나의 작업을 수행하는 Single Thread 언어로 동기적 처리를 하지만, 브라우저 환경에서는 Web API에서 처리된 작업이 지속적으로 Task Queu를 거쳐 Event Loop에 의해 Call Stack에 들어와 순차적으로 실행됨으로써 비동기 작업이 가능한 환경이 된다.

---

# Axios 라이브러리

> Axios

- JavaScript의 HTTP 웹 통신을 위한 라이브러리
- 확장 가능하나 인터페이스와 쉽게 사용할 수 있는 비동기 통신 기능을 제공
- node 환경은 npm을 이용해서 설치 후 사용할 수 있고, browser 환경은 CDN을 이용해서 사용할 수 있음

## Axios 기본 구조

> Axios 사용해보기

- get, post 등 여러 method 사용 가능
- then을 이용해서 성공하면 수행할 로직을 형성
- catch를 이용해서 실패하면 수행할 로직을 작성

> 고양이 사진 가져오기

- The Cat API

  - 이미지를 요청해서 가져오는 작업을 비동기로 처리

- response 구조

  - 랜덤으로 들어가 있다.

> 고양이 사진 가져오기(Python)

- Python 으로 요청해보기(동기)

```py
import requests

print('고양이는 야옹')

cat_image_search_url = "https://~"
response = requests.get(cat_image_search_url)

if response.status_code == 200:
  print(response.json())
else:
  print('실패했다옹')

print('야옹야옹')
```

> 고양이 사진 가져오기(JavaScript)

- Axios로 요청해보기(비동기)

```html
<script>
  console.log("고양이는 야옹");
  const catImageSearchURL = "https";

  axios
    .get(catImageSearchURL)
    .then((response) => {
      console.log(response.data);
    })
    .catch((error) => {
      console.log("실패했다옹");
    });
  console.log("야옹야옹");
</script>
```

> 결과 비교

- 동기식 코드(Python)은 위에서부터 순서대로 처리가 되기 때문에 첫번째 print가 출력되고 이미지를 가져오는 처리를 기다렸다가 다음 print가 출력되는 반면
- 비동기식 코드(JavaScript)는 바로 처리가 가능한 작업(console.log)은 바로 처리하고, 오래 걸리는 작업인 이미지를 요청하고 가져오는 일은 요청을 보내 놓고 기다리지 않고 다음 코드로 진행 후 완료가 된 시점에 결과 출력이 진행됨

> 고양이 사진 가져오기(완성하기)

- 작업 Flow

1. 버튼을 누르면
2. 고양이 이미지를 요청하고
3. 요청이 처리되어 응답이 오면
4. 처리한 response 에 있는 url을 img 태그에 넣어 보여주기

> 고양이 사진 가져오기(실행결과)

- 버튼을 누르면 console.log가 먼저 출력되고 이미지 요청을 보낸다.
- 버튼을 여러 번 누르면 먼저 로딩되는 이미지부터 나오는 것을 볼 수 있다.

## 정리

- axios 는 비동기로 데이터 통신을 가능하게 하는 라이브러리
- 같은 방식으로 우리가 배운 Django REST API로 요청을 보내서 데이터를 받아온 후 처리할 수 있음

---

# Callback 과 Promise

> 비동기 처리의 단점

- 작업이 완료되는 순서에 따라 처리한다는 것
- 개발자의 입장에서는 코드의 실행 순서가 불명확하다는 단점이 있음. 이와 같은 단점을 실행 결과를 예상하면서 코드를 작성할 수 없게 함.
- 콜백 함수를 사용하자!

## 콜백함수(Callback Function)

> 콜백 함수란?

- 특별한 함수가 아님. 다른 함수의 인자로 전달되는 함수
- 비동기에만 사용되는 함수가 아니며 동기, 비동기 상관 없이 사용 가능
- 시간이 걸리는 비동기 작업이 완료된 후 실행할 작업을 명시하는 데 사용되는 콜백 함수를 비동기 콜백(asynchronous callback)이라 부름

> 콜백 함수를 사용하는 이유

- 명시적인 호출이 아닌 특정 조건 또는 행동에 의해 호출되도록 작성할 수 있음
- 요청이 들어오면, 이벤트가 발생하면, 데이터를 받아오면 등의 조건으로 이후 로직을 제어할 수 있음
- 비동기 처리를 순차적으로 동작할 수 있게 함
- 비동기 처리를 위해서는 콜백 함수의 형태가 반드시 필요

> 콜백 지옥(Callback Hell)

- 콜백 함수는 연쇄적으로 발생하는 비동기 작업을 순차적으로 동작할 수 있게 함
- 보통 어떤 기능의 실행 결과를 받아서 다른 기능을 수행하기 위해 많이 사용하는데, 이 과정을 작성하다 보면 비슷한 패턴이 계속 발생하게 됨

- A를 처리해서 결과가 나오면, 첫 번째 callback 함수를 실행하고
- 첫 번째 callback 함수가 종료되면 두 번째... 세 번쨰...

- 비동기 처리를 위한 콜백을 작성할 때 마주하는 문제를 Callback Hell(콜백 지옥)이라 하며, 그때의 코드 작성 형태가 마치 피라미드와 같다고 해서 Pyramid of doom(파멸의 피라미드) 라고도 부름

> 정리

- 콜백 함수는 비동기 작업을 순차적으로 실행할 수 있게 하는 반드시 필요한 로직
- 비동기 코드를 작성하다 보면 콜백 함수로 이한 콜백 지옥(Callback Hell)은 반드시 나타나는 문제

  - 코드의 가독성을 해치고
  - 유지 보수가 어려워짐

---

# Callback 과 Promise

## 프로미스(Promise)

> 프로미스(Promise)

- Callback Hell 문제를 해결하기 위해 등장한 비동기 처리를 위한 객체
- 작업이 끝나면 실행 시켜줄게 라는 약속(promise)
- 비동기 작업의 완료 또는 실패를 나타내는 객체
- Promise 기반의 클라이언트가 바로 이전에 사용한 Axis 라이브러리

  - 성공에 대한 약속 then()
  - 실패에 대한 약속 catch()

> 프로미스(Promise)

- then(callback)

  - 요청한 작업이 성공하면 callback 실행
  - callback은 이전 작업의 성공 결과를 인자로 전달 받음

- catch(callback)

  - then()이 하나라도 실패하면 callback 실행
  - callback은 이전 작업의 실패 객체를 인자로 전달 받음

- then과 catch 모두 항상 promise 객체를 반환. 즉 계속해서 chaining을 할 수 있음

- axios로 처리한 비동기 로직이 항상 promise 객체를 반환. 그래서 then을 계속 이어 나가면서 작성할 수 있던 것

```js
// 기존의 콜백 함수 작성 방식

work1(functin () {
  // 첫번째
  work2(result1, function (result2) {
    // 두번째
    work3(result2, function (result3) {
      console.log('최종 :' + result3)
    })
  })
})

// promise 방시

work1()
  .then((result1) => {
    //work2
    return result2
  })
  .then((result2) => {
    //work3
    return result3
  })
  .catch((error) => {
    // error handling
  })
```

- promise 방식은 비동기 처리를 마치 우리가 일반적으로 위에서 아래로 적는 방식처럼 코드를 작성할 수 있음

> Promise가 보장하는 것(vs 비동기 콜백)

- 비동기 콜백 작성 스타일과 달리 Promise 가 보장하는 특징

1. callback 함수는 JavaScript의 Event Loop가 현재 실행 중인 Call Stack을 완료하기 이전에는 절대 호출되지 않음

- Promise callback 함수는 Event Queue에 배치되는 엄격한 순서로 호출됨

2. 비동기 작업이 성공하거나 실패한 뒤에 .then() 메서드를 이용하여 추가한 경우에도 1번과 똑같이 동작

3. .then()을 여러 번 사용하여 여러 개의 callback 함수를 추가할 수 있음(Chaining)

- 각각의 callback은 주어진 순서대로 하나하나 실행하게 됨
- Chaning은 Promise의 가장 뛰어난 장점

> 주의사항

- return을 넘겨주지 않으면 다음then이 실행되지 않는다.
- 앞의 return값을 다음 then의 인자로 사용하는 게 편하다.
- 이런 식으로도 사용 가능

```js
btn.addEventListner("click", function () {
  axios({
    method: "post",
    url: catImageSearchURL,
  })
    .then()
    .then()
    .catch();
});
```

- 요청 config 기억하기

---

# AJAX
