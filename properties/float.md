# 정렬 (Float)

| 속성 | 의미 | 특이사항 |
|---|---|---|
| `float` | 요소를 좌우 방향으로 띄움(수평 정렬) | `float`해제 방법 /  `display`수정 |
| `clear` | `float`속성이 적용되지 않도록 지정(해제) |  |

## `float`

요소를 좌우 방향으로 띄움(수평 정렬)

| 값 | 의미 | 기본값 |
|---|---|---|
| `none` | 요소 띄움 없음 | `none` |
| `left` | 왼쪽으로 띄움 |  |
| `right` | 오른쪽으로 띄움 |  |

### 사용법

#### 단순 띄움

`float`속성으로 요소를 띄움 (후 형제요소에 `clear` 속성 추가)

```html
<img src="img/flag.png" alt="태극기" class="flag">
동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라 만세.
무궁과 삼천리 화려강산 대한 사람, 대한으로 길이 보전하세
<div class="next"></div>
```

```css
.flag {
  float: left;
}
.next {
  clear: left;
}
```

#### 정렬

왼쪽(오른쪽)부터 차례로 수평 정렬 (후 부모요소에 `clearfix` 클래스 추가)

```html
<ul class="list clearfix">
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

```css
.clearfix::after {
  content: "";
  clear: both;
  display: block; /* or `table` */
}
.list li {
  width: 100px;
  height: 100px;
  background: red;
  float: left;
}
```

#### 양쪽 정렬

2개 이상의 요소를 양쪽(좌우)에 따로 수평 정렬 (후 부모요소에 `clearfix` 클래스 추가)

```html
<div class="clearfix">
  <div class="left"></div>
  <div class="right"></div>
</div>
```

```css
.clearfix::after {
  content: "";
  clear: both;
  display: block; /* or `table` */
}
.left {
  float: left;
}
.right {
  float: right;
}
```

### 특성: `float` 해제

`float`속성이 적용된 요소의 주위로 다른 요소들이 흐르게 되는데 이를 방지하기 위해 속성을 '해제'해야 함

1. 형제요소에 `clear(left,right,both)`속성 추가하여 해제
1. 부모요소에 `overflow(hidden,auto)`속성 추가하여 해제
1. 부모요소에 `clearfix`클래스 추가하여 해제

#### 형제요소에서 해제

`float`속성이 추가된 요소의 다음 형제요소에 `clear`속성 추가

```html
<div class="left"></div>
<div class="left"></div>
<div class="next"></div>
```

```css
.left {
  width: 100px;
  height: 100px;
  background: red;
  float: left;
}
.next {
  clear: both;
}
```

#### 부모요소에서 해제 1

`float`속성이 추가된 요소의 부모요소에 `overflow`속성 추가

```html
<div class="parent">
  <div class="child"></div>
  <div class="child"></div>
</div>
```

```css
.parent {
  overflow: hidden; /* or `auto` */
}
.child {
  float: left;
}
```

#### 부모요소에서 해제 2 (추천)

`float`속성이 추가된 요소의 부모요소에 `clearfix`클래스 추가

```html
<div class="parent clearfix">
  <div class="child"></div>
  <div class="child"></div>
</div>
```

```css
.clearfix::after {
  content: "";
  clear: both;
  display: block; /* or `table` */
}
.child {
  float: left;
}
```

### 특성: `display` 수정

`float`속성이 추가된 요소는 `display`속성의 값이 `block`으로 수정됨

| 지정값 | 변화값 |
|---|---|
| `inline` | `block` |
| `inline-block` | `block` |
| `inline-table` | `block` |
| `table-row` | `block` |
| `table-row-group` | `block` |
| `table-column` | `block` |
| `table-column-group` | `block` |
| `table-cell` | `block` |
| `table-caption` | `block` |
| `table-header-group` | `block` |
| `table-footer-group` | `block` |
| `flex` | `flex`, 효과없음 |
| `inline-flex` | `inline-flex`, 효과없음 |
| 그외 | 변화없음 |

## `clear`

`float`속성이 적용되지 않도록 지정 (해제)

| 값 | 의미 | 기본값 |
|---|---|---|
| `none` | 요소 띄움 허용 | `none` |
| `left` | 왼쪽 띄움 해제 |  |
| `right` | 오른쪽 띄움 해제 |  |
| `both` | 양쪽(왼쪽,오른쪽) 모두 띄움 해제 |  |
