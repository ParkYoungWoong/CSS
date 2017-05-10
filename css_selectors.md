# CSS Selectors

## 기본 선택자들 (Basic Selectors)

### 전체 (Universal Selector)

모든 요소 선택

```
*
```

```css
* { color: red; }
div > * { color: blue; }
```

### 태그 (Type Selector)

태그명이 `E`인 요소를 선택

```
E
```

```css
div { color: red; }
```

```html
<h1>1</h1>
<div>2</div> <!--RED-->
<p>3</p>
<span>4</span>

```

### 클래스 (Class Selector)

HTML class 속성 값이 `E`인 요소를 선택

```
.E
```

```css
.hello { color: red; }
```

```html
<div class="hello">HELLO</div> <!--RED-->
<div>WORLD</div>
```

### 아이디 (ID Selector)

HTML id 속성 값이 `E`인 요소를 선택

```
#E
```

```css
#hello { color: red; }
```

```html
<div id="hello">HELLO</div> <!--RED-->
<div class="world">WORLD</div>
```

## 복합 선택자들 (Combinators)

### 일치

`E`와 `F`를 동시에 만족하는 요소를 선택

```
EF
```

```css
span.hello { color: red; }
```

```html
<div class="hello">HELLO</div>
<span class="hello">HELLO</span> <!--RED-->
```

### 자식 (Child Combinator)

`E`의 자식 `F`를 선택

```
E > F
```

```css
.parent > .child { color: red; }
.list > li { color: blue; }
```

```html
<div class="parent">
    <div class="child"></div> <!--RED-->
</div>

<ul class="list">
  <li>1</li> <!--BLUE-->
  <li>2</li> <!--BLUE-->
  <li>3</li> <!--BLUE-->
</ul>
```

### 후손(하위) (Descendant Combinator)

`E`의 후손(하위요소) `F`를 선택

```
E F
```

```css
.parents .red { color: red; }
.list li { color: blue; }
```

```html
<div class="parents">
  <h1>HELLO</h1>
  <p>
    Welcome to
    <span class="red">hello</span> <!--RED-->
    world!
  </p>
</div>

<ul class="list">
  <li>1 <!--BLUE-->
    <ul>
      <li>2</li> <!--BLUE-->
      <li>3</li> <!--BLUE-->
    </ul>
  </li>
  <li>4</li> <!--BLUE-->
</ul>
```

### 인접 형제 (Adjacent Sibling Combinator)

`E`의 다음 형제요소 `F` 하나만 선택

```
E + F
```

```css
.hello + li { color: red; }
```

```html
<ul>
  <li>1</li>
  <li class="hello">2</li>
  <li>3</li> <!--RED-->
  <li>4</li>
  <li>5</li>
</ul>
```

### 일반 형제 (General Sibling Combinator)

`E`의 다음 형제요소 `F` 모두 선택

```
E ~ F
```

```css
.hello ~ li { color: red; }
```

```html
<ul>
  <li>1</li>
  <li class="hello">2</li>
  <li>3</li> <!--RED-->
  <li>4</li> <!--RED-->
  <li>5</li> <!--RED-->
</ul>
```

## 속성 선택자들 (Attribute Selectors)

### [속성]

`attr`속성이 포함된 `E` 선택

```
E[attr]
```

```css
[href] { color: red; }
```

```html
<a href="#">HELLO WORLD</a>
<a href="#" title="hello world">HELLO WOLRD</a>
```

### [속성=값]

`attr`속성의 값으로 `val`이 정확하게 일치하는 `E` 선택

```
E[attr=val]
```

```css
[title=hello] { color: red; }
```

```html
<a href="#" title="hello world">HELLO WORLD</a>
<a href="#" title="hello">HELLO</a> <!--RED-->
```

### [속성~=값]

`attr`속성의 값으로 `val`이 포함된 `E` 선택<br>
(공백으로 분리된 `val`값으로 일치해야 함)

```
E[attr~=val]
```

```css
[title=hello] { color: red; }
```

```html
<a href="#" title="hello world">HELLO WOLRD</a> <!--RED-->
<a href="#" title="hello_world">HELLO WORLD</a>
```

### [속성|=값]

`attr`속성의 값으로 `val`이 정확하게 일치하거나, `val-`로 시작하는 `E` 선택<br>
(`-`을 제외한 다른 기호는 불가)

```
E[attr|=val]
```

```css
[title=hello] { color: red; }
```

```html
<a href="#" title="hello">HELLO</a> <!--RED-->
<a href="#" title="hello-world">HELLO WORLD</a> <!--RED-->
<a href="#" title="hello world">HELLO WORLD</a>
```

### [속성^=값]

`attr`속성의 값이 `val`로 시작하는 `E` 선택

```
E[attr^=val]
```

```css
[title=hello] { color: red; }
```

```html
<a href="#" title="hello world">HELLO WORLD</a> <!--RED-->
```

### [속성$=값]

`attr`속성의 값이 `val`로 끝나는 `E` 선택

```
E[attr$=val]
```

```css
[title$=world] { color: red; }
```

```html
<a href="#" title="hello world">HELLO WORLD</a> <!--RED-->
```

### [속성*=값]

`attr`속성의 값으로 `val`이 포함되어 있는 `E` 선택

```
E[attr*=val]
```

```css
[type=lo_] { color: red; }
```

```html
<a href="#" title="hello_world">HELLO WORLD</a> <!--RED-->
```

## 가상 클래스 선택자들 (Pseudo-Classes)

### 링크 (The link)

#### BEFORE VISIT

방문한 적 없는 링크 `E` 선택

```
E:link
```

```css
a:link { color: red;}
```

#### AFTER VISIT

방문한 적 있는 링크 `E` 선택

```
E:visited
```

```css
a:visited { color: red; }
```

### 동적 (The user action)

#### ACTIVE

`E`에 마우스(클릭)나 키보드(엔터)가 눌린 동안에만 `E` 선택

```
E:active
```

```css
a:active { color: blue; }
```

#### HOVER

`E`에 마우스(포인터)가 올라가 있는 동안에만 `E` 선택

```
E:hover
```

```css
a:hover { color: green; }
```

#### FOCUS

`E`에 포커스가 되어있는 동안에만 `E` 선택

```
E:focus
```

```css
input:focus { color: red; }
```

### 구조적 (Structural)

#### ROOT

문서 최상위 요소(`html`)를 선택

```css
:root {
	background: red;
	color: white;
}
```

#### EMPTY

텍스트, 공백을 포함한 아무 자식(후손)요소도 없는 `E` 선택

```
E:empty
```

```css
div:empty { width: 100px; }
```

#### FIRST CHILD

`E`가 형제요소 중 첫번째 요소라면 선택

```
E:first-child
```

```css
.parent li:first-child { color: red; }
```

```html
<ul class="parent">
	<li>1</li> <!--RED-->
	<li>2</li>
	<li>3</li>
	<li>4</li>
</ul>
```

#### LAST CHILD

`E`가 형제요소 중 마지막 요소라면 선택

```
E:last-child
```

```css
.parent li:last-child { color: red; }
```

```html
<ul class="parent">
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li> <!--RED-->
</ul>
```

#### NTH CHILD

`E`가 형제요소 중 `n`번째 요소라면 선택<br>
(`n` 키워드 사용 시 `0`부터(Zero-base)로 해석)

```
E:nth-child(n)
```

```css
.parent li:nth-child(3) { color: red; }
.parent div:nth-child(3) { color: red; } /* 선택없음 */
.even li:nth-child(2n) { color: red; }
.odd li:nth-child(2n+1) { color: red; }
```

```html
<ul class="parent">
	<li>1</li>
	<li>2</li>
	<li>3</li> <!--RED-->
	<li>4</li>
</ul>
<ul class="even">
	<li>1</li>
	<li>2</li> <!--RED-->
	<li>3</li>
	<li>4</li> <!--RED-->
</ul>
<ul class="odd">
	<li>1</li> <!--RED-->
	<li>2</li>
	<li>3</li> <!--RED-->
	<li>4</li>
</ul>
```

#### NTH LAST CHILD

`E`가 형제요소 중 뒤에서 `n`번째 요소라면 선택<br>
(`n` 키워드 사용 시 `0`부터(Zero-base)로 해석)

```
E:nth-last-child(n)
```

```css
.parent li:nth-last-child(2) { color: red; }
```

```html
<ul class="parent">
	<li>1</li>
	<li>2</li>
	<li>3</li> <!--RED-->
	<li>4</li>
</ul>
```

#### ONLY CHILD

`E`가 유일한 자식요소일 경우 선택

```
E:only-child
```

```css
ul li:only-child { color: red; }
```

```html
<ul>
	<li>1</li> <!--RED-->
</ul>

<ul>
	<li>1</li>
	<li>2</li>
</ul>
```

#### FIRST OF TYPE

`E`의 타입(태그명)과 동일한 타입인 형제요소 중 `E`가 첫번째 요소라면 선택

```
E:first-of-type
```

```css
ul .hello:first-of-type { color: red; } /* 선택없음 */
div p:first-of-type { color: red; }
```

```html
<ul>
	<li>1</li>
	<li class="hello">2</li>
	<li class="hello">3</li>
	<li class="hello">4</li>
</ul>

<div>
	<h1>1</h1>
	<p>2</p> <!--RED-->
	<p>3</p>
	<p>4</p>
	<div>5</div>
	<p>6</p>
</div>
```

#### LAST OF TYPE

`E`의 타입(태그명)과 동일한 타입인 형제요소 중 `E`가 마지막 요소라면 선택

```
E:last-of-type
```

```css
ul .hello:last-of-type { color: red; }
div p:last-of-type { color: red; }
```

```html
<ul>
	<li>1</li>
	<li class="hello">2</li>
	<li class="hello">3</li>
	<li class="hello">4</li> <!--RED-->
</ul>

<div>
	<h1>1</h1>
	<p>2</p>
	<p>3</p>
	<p>4</p>
	<div>5</div>
	<p>6</p> <!--RED-->
</div>
```

#### NTH OF TYPE

`E`의 타입(태그명)과 동일한 타입인 형제요소 중 `E`가 `n`번째 요소라면 선택<br>
(`n` 키워드 사용 시 `0`부터(Zero-base)로 해석)

```
E:nth-of-type(n)
```

```css
ul .hello:nth-of-type(2) { color: red; }
div p:nth-of-type(2) { color: red; }
```

```html
<ul>
	<li>1</li>
	<li class="hello">2</li> <!--RED-->
	<li class="hello">3</li>
	<li class="hello">4</li>
</ul>

<div>
	<h1>1</h1>
	<p>2</p>
	<p>3</p> <!--RED-->
	<p>4</p>
	<div>5</div>
	<p>6</p>
</div>
```

#### NTH LAST OF TYPE

`E`의 타입(태그명)과 동일한 타입인 형제요소 중 `E`가 뒤에서 `n`번째 요소라면 선택<br>
(`n` 키워드 사용 시 `0`부터(Zero-base)로 해석)

```
E:nth-last-of-type(n)
```

```css
ul .hello:nth-last-of-type(2) { color: red; }
div p:nth-last-of-type(2) { color: red; }
```

```html
<ul>
	<li>1</li>
	<li class="hello">2</li>
	<li class="hello">3</li> <!--RED-->
	<li class="hello">4</li>
</ul>

<div>
	<h1>1</h1>
	<p>2</p>
	<p>3</p>
	<p>4</p> <!--RED-->
	<div>5</div>
	<p>6</p>
</div>
```

#### ONLY OF TYPE

`E`의 타입(태그명)과 동일한 타입인 형제요소 중 `E`가 유일한 자식요소일 경우 선택

```
E:only-of-type
```

```css
.parent h1:only-of-type { color: red; }
```

```html
<div class="parent">
	<h1>1</h1>
	<p>2</p>
	<p>3</p>
	<div>4</div>
</div>
```

### 언어 (Language)

`lang`속성의 값이 `language-code`인 `E` 선택

```
E:lang(language-code)
```

```css
:lang(ko) { color: red; }
```

```html
<html lang="ko">
	<head></head>
	<body>
		<!--ALL RED-->
	</body>
</html>
```

### 부정 (Negation)

`S`가 아닌 `E` 선택

```
E:not(S)
```

```css
ul li:not(.hello) { color: red; }
```

```html
<ul>
	<li>1</li> <!--RED-->
	<li class="hello">2</li>
	<li>3</li> <!--RED-->
	<li>4</li> <!--RED-->
</ul>
```

### 목적 (The target)

`E`의 URL 요청이 들어오면 선택<br>
(`E`에는 `id`속성이 지정되어 있어야 함)

```
E:target
```

```css
.world:target { color: red; }
```

```html
<a href="#hello">GO TO HELLO</a> <!--<a>를 선택할 경우-->
<div id="hello" class="world">HELLO WORLD</div> <!--RED-->
```

### UI 요소 상태 (The UI element states)

#### ENABLED

사용 가능한(활성화) 양식(form) `E` 선택<br>
(`<input>`, `<textarea>`, `<select>`, `<button>`)

```
E:enabled
```

```css
input:enabled { border: 1px solid red; }
```

```html
<input type="text" disabled>
<input type="text"> <!--RED-->
<input type="text"> <!--RED-->
```

#### DISABLED

사용 불가능한(비활성화) 양식(form) `E` 선택<br>
(`<input>`, `<textarea>`, `<select>`, `<button>`)

```
E:disabled
```

```css
input:disabled { border: 1px solid red; }
```

```html
<input type="text" disabled> <!--RED-->
<input type="text">
<input type="text">
```

#### CHECKED

선택된 양식(form) `E` 선택<br>
(`<input>`, `<option>`)

```
E:checked
```

```css
input:checked {
	position: relative;
	left: -10px;
}
```

```html
<input type="checkbox" checked> <!-- LEFT -10px -->
<input type="checkbox" checked> <!-- LEFT -10px -->
<input type="radio" name="a">
<input type="radio" name="a" checked> <!-- LEFT -10px -->
<input type="radio" name="a">
```


## 가상 요소 선택자들 (Pseudo-Elements)

### BEFORE

`E` 의 내부에 앞에 내용(content)을 삽입<br>
(`content` 속성 필수)

```
E::before
```

```css
ul li::before {
	content: "$";
}
div::before {
	content: url("../images/smile.png");
}
```

```html
<ul>
	<li>1</li> <!-- $1 -->
	<li>2</li> <!-- $2 -->
	<li>3</li> <!-- $3 -->
	<li>4</li> <!-- $4 -->
</ul>

<div>HAPPY</div> <!--이미지 삽입됨-->
```

### AFTER

`E` 의 내부에 뒤에 내용(content)을 삽입

```
E::after
```

```css
ul li::after {
	content: ".0";
}
```

```html
<ul>
	<li>1</li> <!-- 1.0 -->
	<li>2</li> <!-- 2.0 -->
	<li>3</li> <!-- 3.0 -->
	<li>4</li> <!-- 4.0 -->
</ul>
```

### FIRST LINE

`E`의 첫번째 줄(line) 글자들을 선택

```
E::first-line
```

```css
p::first-line { color: red; }
```

```html
<p>
	HELLO<br> <!--RED-->
	WORLD
</p>
```

### FIRST LETTER

`E`의 첫번째 글자(letter)를 선택

```
E::first-letter
```

```css
p::first-letter { color: red; }
```

```html
<p>HELLO WORLD</p> <!--가장 앞에 'H'만 RED-->
```

### 해야할 친구들

:in-range

:out-of-range

:valid

:invalid

:optional

:required

:read-only

:read-write

::selection
