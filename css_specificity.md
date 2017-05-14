# CSS Specificity (명시도, 우선순위)

## 우선순위 결정

같은 요소가 여러 선언의 대상이 될 경우, 어떤 선언의 CSS 속성(property)을 우선 적용할지 결정하는 방법

1. 아래의 선언 방식들이 가지는 점수를 합하여 큰 점수를 가지는 선언이 우선
1. 점수가 같을 경우 가장 나중에 발견되는(더 늦게 해석된) 선언이 우선
1. 아래의 선언 방식들은 '상속' 규칙보다 우선
1. `!important`가 적용된 선언 방식은 모든 방식보다 우선

### 가장 중요 (!important)

모든 선언을 무시하고 가장 우선, 점수 없음

```css
div {
  color: red !important; /* 가장 우선 */
}
```

### 인라인 선언 방식 (Style attribute)

인라인 선언(HTML `style`속성을 사용) `1,000`점

```html
<div style="color: red;">HELLO WORLD</div> <!-- 1,000pt -->
```

### 아이디 (ID selector)

아이디 선택자 `100`점

```css
#hello {
  color: red; /* 100pt */
}
```

### 클래스 (Class selector)

클래스 선택자 `10`점<br>
(가상 클래스 선택자(pseudo-classeds) 포함, `E:not(S)` 선택자에서는 `E`와 `S` 점수 포함, `:not`은 포함되지 않음)

```css
.a {
  color: red; /* 10pt */
}
.list li.a:nth-child(1) {
  color: blue; /* 31pt */
}
.list li:not(.a) {
  color: green; /* 21pt */
}
```

### 태그 (Element)

태그 선택자 `1`점<br>
(가상 요소 선택자(pseudo-elements) 포함)

```css
div {
  color: red; /* 1pt */
}
nav ul li {
  color: blue; /* 3pt */
}
```

### 전체 (Universal selector)

전체 선택자 `0`점

```css
* {
  color: red; /* 0pt */
}
.hello > * {
  color: blue; /* 10pt */
}
```

### 상속 (CSS inheritance)

항상 우선하지 않음, 점수 없음

```css
html {
  color: red; /* body 이하 모든 요소에게 상속 */
}
div {
  color: blue; /* 태그 선택자, 우선 */
}
```

## 정리

`!important` > 인라인선언 > 아이디 > 클래스 > 태그 > 전체 > 상속
