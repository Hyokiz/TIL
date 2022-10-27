# 20221027 TIL

# 어제 복습

- 동기

  - 직렬적

- 비동기

  - 병렬적

- browser에는 DOM API가 없다..

```js
// 동기, 비동기, 실행 컨텍스트 종합

// 시간 지연 함수 -> 중요하지 않음

function sleep(sec) {
  const delayUntil = Date.now() + sec
  while (Date.now() < delayUntil) {}
}

for (let i = 1; i <= 10; i++) {
  console.log(`${i}번째 반복`)
  sleep(1000)
}

setTimeout(function () {
  console.log("5초 뒤 실행!!")
}, 5000)

// 이 코드의 결과는?
// "10번째 반복" 문구 이후로 5초가 흐른 다음 "5초 뒤 실행!!"이 나온다.
// 동시에 들어가지 않는다.

function sleep(sec) {
  const delayUntil = Date.now() + sec
  while (Date.now() < delayUntil) {}
}

setTimeout(function () {
  console.log("5초 뒤 실행!!")
}, 5000)

for (let i = 1; i <= 10; i++) {
  console.log(`${i}번째 반복`)
  sleep(1000)
}

// 이 코드의 결과는?
// "10번째 반복" 문구 이후로 "5초 뒤 실행!!"이 바로 나온다.
```

- XMLHttpRequest() : XMLHttpRequest (XHR) 객체는 서버와 상호작용할 때 사용합니다. XHR을 사용하면 페이지의 새로고침 없이도 URL에서 데이터를 가져올 수 있습니다.

## 콜백 함수

- 앞선 데이터를 받아오지 않고 전역함수에서 실행시켜버릴 경우 데이터가 없다.
- 따라서 앞의 데이터를 받아와서 그 다음을 실행하려다보니 콜백 지옥 발생
- 해결하기 위해 Promise가 나왔다.

## Promise

```js
// const get = function (url) {
//   return new Promise(function (resolve, reject) {
//     const xhr = new XMLHttpResponse()
//     xhr.open("GET", url)
//     xhr.send()

//     xhr.onload = () => {
//       if (xhr.status === 200) {
//         resolve.
//       }
//     }
//   })
// }

// 후속 처리(then, catch)를 통해 지옥 탈출
get (`${url}/posts/1`)
  .then((response) => {
    const userId = response.userId
    return userId
  })
  .then((userId) => {
    return get(`${url}/users/${userId}`)
  })
  .then((response) => {
    console.log(response)
  })
  .catch((error) => {
    console.log(error)
  })
```

```js

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    img {
      width: 500px;
      height: 500px;
      border: 1px solid black;
    }
  </style>
</head>

<body>
  <div>
    <img id="cat">
    <img id="dog">
  </div>

  <button>CAT & DOG</button>

  <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
  <script>
    const button = document.querySelector('button')

    // 두 개 이상의 요청을 비동기로 받기 (매번 순서가 달라짐 -> 먼저 오는 걸 먼저 띄워주기 때문)
    button.addEventListener('click', function (event) {
      // 1. 고양이 사진 가져오기
      axios({
        url: 'https://api.thecatapi.com/v1/images/search',
        method: 'get',
      })
        .then((response) => {
          // console.log(response.data)
          const catImgTag = document.querySelector('#cat')
          catImgTag.src = response.data[0].url
        })
        .catch((error) => {
          console.log(error)
        })

      // 2. 강아지 사진 가져오기
      axios({
        url: 'https://dog.ceo/api/breeds/image/random',
        method: 'get',
      })
        .then((response) => {
          // console.log(response.data)
          const dogImgTag = document.querySelector('#dog')
          dogImgTag.src = response.data.message
        })
        .catch((error) => {
          console.log(error)
        })
    })
  </script>
</body>

</html>
```

## AJAX

> 수업 정리

- 비동기
- DOM Tree를 조작 할 수 있는 언어 -> JavaScript

- 부분을 바꾸기 위해서

  - JS요청 -> XMLHttpRequest -> Promise -> Axios(비동기요청)

- 여기서 부분만 바꾸는 것이 AJAX이다.

--- 

# AJAX

> AJAX란?

- 비동기 통신을 이용하면 화면 전체를 새로고침 하지 않아도 서버로 요청을 보내고, 데이터를 받아 화면의 일부분만 업데이트 가능
- 이러한 비동기 통신 웹 개발 기술을 Asynchronous Javascript And XML(AJAX)라고 함
- AJAX의 특징

  1. 페이지 새로고침 없이 서버에 요청
  2. 서버로부터 응답(데이터)를 받아 작업을 수행

- 이러한 비동기 웹 통신을 위한 라이브러리 중 하나가 Axios

## 비동기(Async) 적용하기

> data-* attributes

- 사용자 지정 데이터 특성을 만들어 임의의 데이터를 HTML과 DOM 사이에서 교환할 수 있는 방법
- 사용 예시

```html
<div data-my-id="my-data"></div>
<script>
  const myId = event.target.dataset.myId
</script>
```

- 예를 들어 data-test-value 라는 이름의 특성을 지정했다면 JavaScript에서는 element.dataset.testValue로 접근할 수 있음

- 속성명 작성 시 주의사항

  - 대소문자 여부에 상관없이 xml로 시작하면 안됨
  - 세미콜론을 포함해서는 안됨
  - 대문자를 포함해서는 안됨

> XHR

- XMLHttpRequest
- AJAX 요청을 생성하는 JavaScript API
- XHR의 메서드로 브라우저와 서버 간 네트워크 요청을 전송할 수 있음
- Axios는 손쉽게 XHR을 보내고 응답 결과를 Promise 객체로 반환해주는 라이브러리

> 팔로워 & 팔로잉 수 비동기 적용

- 해당 요소를 선택할 수 있도록 span 태그와 id 속성 작성

> 좋아요(like)

- 좋아요 비동기 적용은 "팔로우와 동일한 흐름 + forEach() & querySelectorAll()"

  - index 페이지 각 게시글에 좋아요 버튼이 있기 때문

## 마무리

> 왜 비동기(Asynchronous) 방식이 필요할까

- human-centered design with UX

  - 인간 중심으로 설계된 사용자 경험
  - 실제 Ajax라는 용어를 처음 논문에서 사용한 사람이 강조

- 동기와 비동기
- JavaScript의 비동기 처리

  - Call Stack, Web API, Task Queue, Event Loop

- Axios 라이브러리

  - then & catch

- Async Callback과 Promise
- AJAX

