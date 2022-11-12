# 20221111 TIL

# CSS

- labeling이 중요하다.

> 선택자(Selector)

- Universal = *
- type = Tag
- ID = #id
- Class = .class
- state = :
- Attribute = []

- 기본 문법

```css
selector {
  property: value;
}

* {
  color: green;
}

li {
  color: blue;
}

#special {
  color: pink;
}

.red {
  width: 100px;
  height: 100px;
  background: yellow;
}

button:hover {
  color: red;
  background: beige;
}

a[href="naver"] {
  color: purple;
}

li#special {
  color: pink;
}
```

- div box를 봤을 때

```css
.red {
  width: 100px;
  height: 100px;
  padding: 20px 20px 20px 20px;
  margin: 20px;
  border: 2px dashed red;
  /* border-width: 2px;
  border-style: solid;
  bordor-color: pink; */
}
```

- 가능한 속성값 확인 : css reference

- 게임을 통한 selector 쓰는 연습 : https://flukeout.github.io