# layouts

## Flow content

document의 body와 application에서 쓰이는 대부분의 요소(elements)들은 flow content로써 분류 된다.
(거의 대부분이 쓰이므로 한번 보는 걸 추천 [Flow content](https://html.spec.whatwg.org/multipage/dom.html#flow-content))

## Sectioning content

Headings 와 Footers의 범위를 정의 하는 컨텐트 이다.
각각의 Sectioning content 요소는 haeding과 하나의 outline을 가질 수 있다.

- article
- aside
- nav
- section

### outline?

Sectioning content 요소 또는 Sectioning root 요소(ex. body, fieldset, figure, td ...[참고](https://html.spec.whatwg.org/multipage/sections.html#sectioning-root)) 는 하나 또는 그이상 section들을 껴넣을 수 있다. 하나의 outline이 생성된 요소는 outline owner라고 말 할 수 있다.

```html
<body>
  <hgroup id="document-title">
    <h1>HTML</h1>
    <h2>Living Standard — Last Updated 12 August 2016</h2>
  </hgroup>
  <p>Some intro to the document.</p>
  <h2>Table of contents</h2>
  <ol id="toc">
    ...
  </ol>
  <h2>First section</h2>
  <p>Some intro to the first section.</p>
</body>
```

- 첫 번째 outline은 body 태그
  - hgroup 태그 안에 h1과 h2 아래 p 태그까지 outline으려 연결 된다.
    (비록 렌더된 view에서 그리 보이지 않더라도)
  - 그 다음 \<h2>Table of contents\</h2> 와 아래 \<ol>과 연결된다.
  - \<h2>First section\</h2> 요소와 아래 \<p>요소와 연결 된다.

자세한 내용은 [outline](https://html.spec.whatwg.org/multipage/sections.html#outline)을 참고하자!

### article

### section

### aside

### nav
