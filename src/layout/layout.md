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

article 요소는 문서에서 완료된 또는 독립적인 요소를 나타낸다. 독립적으로 나눌수 있거나 재사용할 수 있는 요소를 나타낸다.
컨텐츠의 독립적인 요소라고 생각 하면 된다. article 요소는 그 자체로 의미가 있어야 하며, 사이트의 나머지 부분과 독립적으로 배포할 수 있어야 한다.

article 요소들이 중첩되었을 때는 안에 있는 article 요소들이 바깥 article의 컨텐츠와 관련이 있는 article을 나타낸다.

저작자 정보와 관련있는 article 요소( 예를 들어 \<address>\ 같은)에는 article 요소를 중첩해서 적용 하지 않는다.
[마크업 확인](https://html.spec.whatwg.org/multipage/sections.html#the-article-element)

```html
<article>
  <header>
    <h1>...</h1>
    <p></p>
    <link rel="stylesheet" href="" />
  </header>
  <p>...</p>
  <footer></footer>
</article>
```

**블로그 포스트**
각각 코멘트 정보를 제공하는 \<footer\> 사용
푸터 요소는 해당 섹션의 시작부분에서 나타날 수 있다.
헤더 또한 잘 못된 것이 아니다.

```html
<article itemscope itemtype="http://schema.org/BlogPosting">
  <header>
    <h1 itemprop="headline">...</h1>
    <p>
      <time itemprop="datePublished" datetime="2009-10-09">3 days ago</time>
    </p>
    <link itemprop="url" href="?comments=0" />
  </header>
  <p></p>
  <section>
    <h1>...</h1>
    <article
      itemprop="comment"
      itemscope
      itemtype="http://schema.org/UserComments"
      id="c1"
    >
      <link itemprop="url" href="#c1" />
      <footer>
        <p>
          Posted by:
          <span
            itemprop="creator"
            itemscope
            itemtype="http://schema.org/Person"
          >
            <span itemprop="name">George Washington</span>
          </span>
        </p>
        <p>
          <time itemprop="commentTime" datetime="2009-10-10"
            >15 minutes ago</time
          >
        </p>
      </footer>
      <p>Yeah! Especially when talking about your lobbyist friends!</p>
    </article>
    <article
      itemprop="comment"
      itemscope
      itemtype="http://schema.org/UserComments"
      id="c2"
    >
      <link itemprop="url" href="#c2" />
      <footer>
        <p>
          Posted by:
          <span
            itemprop="creator"
            itemscope
            itemtype="http://schema.org/Person"
          >
            <span itemprop="name">George Hammond</span>
          </span>
        </p>
        <p>
          <time itemprop="commentTime" datetime="2009-10-10"
            >5 minutes ago</time
          >
        </p>
      </footer>
      <p>Hey, you have the same first name as me.</p>
    </article>
  </section>
</article>
```

### section

\<section\>은 문서 또는 어플리케이션의 일반적인 섹션을 나타낸다.
여기서는 일반적으로 제목이 있는 주제별 콘텐츠 그룹이다.

\<section\>은 일반적인 컨테이너 요소가 아니다. 스타일링 목적으로 필요하거나 스크립트가 용이하게 하기 위할때는 \<div\>를 사용하는 것이 좋다.
일반적으로 \<section\>은 문서 outline에서 요소 컨텐츠들이 명시적으로 나욜 되어 있다면 사용하는 것이 좋다.

아래의 예에서 섹션을 사용한다는 것은 작성자가 특정 섹션이 최상위 층, 두 번째 층, 세 번째 층등에 있는지 염두할 필요 없이 \<h1\>을 쓸 수 있는 것을 의미한다.

```html
<article>
  <hgroup>
    <h1>Apples</h1>
    <h2>Tasty, delicious fruit!</h2>
  </hgroup>
  <p>The apple is the pomaceous fruit of the apple tree.</p>
  <section>
    <h1>Red Delicious</h1>
    <p>
      These bright red apples are the most common found in many supermarkets.
    </p>
  </section>
  <section>
    <h1>Granny Smith</h1>
    <p>These juicy, green apples make a great filling for apple pies.</p>
  </section>
</article>
```

### aside

\<aside\> 해당 컨텐츠에서 분리될 수 있고 관련된 컨텐츠와 별개로 간주될 수 있는 페이지의 섹션을 나타낸다.

### nav

\<nav\>요소는 페이지에서 다른 페이지로 가는 링크이거나 페이지내 다른 부분을 나타낸다. 이때 내부의 링크는 문서내 모든 링크가 아니라 컨텐츠 상에 주요 섹션(block)을 의미한다.

렌더링 초기에서 생략될 네비게이션 정보로 부터 이점을 얻을 수 있는 유저 또는 즉시 필요할 네이게이션 정보로 부터 이득을 얻을 사용자를 대상으로 하는 User agents(스크린리더 같은)는 처음에 요구하는데로 스킵할지 제공할지 결정할 방법으로 \<nav\>를 쓸 수 있다.

아래 예시는 두개의 \<nav\>가 있는데 첫 번째는 주요 navigation이고 또 하나는 패이지 내 컨텐츠를 나타낸다.

```html
<body>
  <h1>The Wiki Center Of Exampland</h1>
  <nav>
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/events">Current Events</a></li>
      ...more...
    </ul>
  </nav>
  <article>
    <header>
      <h1>Demos in Exampland</h1>
      <p>Written by A. N. Other.</p>
    </header>
    <nav>
      <ul>
        <li><a href="#public">Public demonstrations</a></li>
        <li><a href="#destroy">Demolitions</a></li>
        ...more...
      </ul>
    </nav>
    <div>
      <section id="public">
        <h1>Public demonstrations</h1>
        <p>...more...</p>
      </section>
      <section id="destroy">
        <h1>Demolitions</h1>
        <p>...more...</p>
      </section>
      ...more...
    </div>
    <footer>
      <p>
        <a href="?edit">Edit</a> | <a href="?delete">Delete</a> |
        <a href="?Rename">Rename</a>
      </p>
    </footer>
  </article>
  <footer>
    <p><small>© copyright 1998 Exampland Emperor</small></p>
  </footer>
</body>
```

#### 참고

- https://html.spec.whatwg.org/multipage/sections.html
- https://www.w3schools.com/tags/tag_article.asp
