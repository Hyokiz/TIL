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