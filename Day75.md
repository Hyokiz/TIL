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

```