# group - list

## dl

dl은 name-value group을 구성하는 연관 목록(설명 목록)을 나타낸다.
terms-definition, metadata topics-value, question-answers 또는 name-value의 다른 그룹이다.

dl안에 dd가 여러개 올수 있는데 아래 예와 같다.

```html
<dl>
  <dt>Authors</dt>
  <dd>John</dd>
  <dd>Luke</dd>
  <dt>Editor</dt>
  <dd>Frank</dd>
</dl>
```

## menu

menu는 하나의 컨텐츠를 구성하는 툴바를 나타낸다.

```html
<menu>
  <li>
    <button onclick="copy()"><img src="copy.svg" alt="Copy" /></button>
  </li>
  <li>
    <button onclick="cut()"><img src="cut.svg" alt="Cut" /></button>
  </li>
  <li>
    <button onclick="paste()"><img src="paste.svg" alt="Paste" /></button>
  </li>
</menu>
```

### 자료 출처

- https://html.spec.whatwg.org/multipage/grouping-content.html#the-dl-element
- https://html.spec.whatwg.org/multipage/grouping-content.html#the-menu-element
