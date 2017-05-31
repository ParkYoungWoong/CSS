# 위치 (Position)

### TOC

| 속성 | 의미 | 특이사항 |
|---|---|---|
| `position` | 요소의 위치 지정 방법의 유형(기준)을 설정 | 요소 겹침 / 요소 쌓임 순서 |
| `top` | 요소의 `position`기준에 맞는 '위쪽'에서의 거리(위치)를 설정 |  |
| `bottom` | 요소의 `position`기준에 맞는 '아래쪽'에서의 거리(위치)를 설정 |  |
| `left` | 요소의 `position`기준에 맞는 '왼쪽'에서의 거리(위치)를 설정 |  |
| `right` | 요소의 `position`기준에 맞는 '오른쪽'에서의 거리(위치)를 설정 |  |
| `z-index` | `position`이 지정된 요소의 '요소 쌓임'정도를 설정 |  |

## `position`

요소의 위치 지정 방법의 유형(기준)을 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| `static` | 유형(기준) 없음 / 배치 불가능 | `static` |
| `relative` | 요소 자신을 기준으로 배치 |  |
| `absolute` | 위치 상 부모(조상)요소를 기준으로 배치 |  |
| `fixed` | 브라우저 창을 기준으로 배치 |  |

### 사용법

#### `position: relative;`

요소 자신을 기준으로 배치<br>
(배치의 용도로 활용하는 것을 권장하지 않음)

```css
.example {
  position: relative; /* 기준 + 배치 */
  top: 50px;
  right: 100px;
}
```

#### `position: absolute;`

위치 상 부모(조상)요소를 기준으로 배치<br>
(부모요소에 `static`을 제외한 `position`속성의 값이 존재해야 함(필수!) / 부모요소에 필요에 의해 미리 부여된 `position`이 없을 경우, 통상 `position: relative;` 지정)

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  position: relative; /* 기준 */
}
.child {
  position: absolute; /* 배치 */
  top: 50px;
  right: 100px;
}
```

부모요소에 `position`속성의 값이 없다면 조상(상위)요소로 올라가면서 위치 상 부모요소를 기준하게 됨.

```html
<div class="grandparent">
  <div class="parent">
    <div class="child"></div>
  </div>
</div>
```

```css
.grandparent {
  position: fixed; /* 기준 */
}
.parent {
  /* 기준 아님 */
}
.child {
  position: absolute; /* 배치 */
  top: 50px;
  right: 100px;
}
```

#### `position: fixed;`

사용자의 브라우저 창을 기준으로 배치

```css
.example {
  position: fixed; /* 브라우저를 기준으로 배치 */
  top: 50px;
  right: 100px;
}
```

### 특성: 요소 겹침(Overlapping Elements)

`position`으로 배치된 요소는 다른 요소와 겹쳐질 수 있음<br>
(특정한 기준을 가지기 때문에 다른 요소들의 위치에 영향을 받지 않음 / 기준에 따라 겹치는 형태가 다름)

```html
<div class="box_group">
  <div class="box positioned"></div>
  <div class="box static"></div>
</div>
```

`position: relative;`일 경우

```css
.box {
  width: 100px;
  height: 100px;
  background: red;
}
.positioned {
  background: blue;
  position: relative;
  top: 50px;
  left: 50px;
}
```

`position: absolute;`일 경우

```css
.box_group {
  width: 300px;
  height: 300px;
  background: yellow;
  position: relative;
}
.box {
  width: 100px;
  height: 100px;
  background: red;
}
.positioned {
  background: blue;
  position: absolute;
  top: 50px;
  left: 50px;
}
```

`position: fixed;`일 경우

```css
body {
  height: 3000px;
}
.box_group {
  width: 300px;
  height: 300px;
  background: yellow;
  position: relative;
}
.box {
  width: 100px;
  height: 100px;
  background: red;
}
.positioned {
  background: blue;
  position: fixed;
  top: 50px;
  left: 50px;
}
```

### 특성: 요소 쌓임 순서(Stack order)

요소가 쌓여 있는 순서를 통해 어떤 요소가 사용자와 가깝게 있는지(더 위에 쌓이는지)를 결정(Z축)

1. `static`을 제외한 `position`속성이 있을 경우 가장 위에 쌓임.(값은 무관)
1. `position`이 모두 존재한다면 `z-index`속성 값의 숫자가 높을 수록 위에 쌓임.
1. `position`과 `z-index` 모두 지정되고 같다면 'HTML'의 마지막 코드일 수록 위에 쌓임.

```
position > z-index > HTML마지막코드
```

```html
<div class="box box1"></div> <!-- (2) -->
<div class="box box2"></div> <!-- (4) -->
<div class="box box3"></div> <!-- (3) -->
<div class="box box4"></div> <!-- 가장 아래에 쌓임(5)-->
<div class="box box5"></div> <!-- 가장 위에 쌓임(1) -->
```

```css
.box {
  width: 100px;
  height: 100px;
  background: red;
}
.box1 {
  position: relative;
  z-index: 2;
}
.box2 {
  position: absolute;
}
.box3 {
  position: fixed;
  z-index: 1;
}
.box4 {
  z-index: 99;
}
.box5 {
  position: absolute;
  z-index: 2;
}
```

## `top`

요소의 `position` 기준에 맞는 '위쪽'에서의 거리(위치)를 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| `auto` | 브라우저가 계산 | `auto` |
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |

## `bottom`

요소의 `position` 기준에 맞는 '아래쪽'에서의 거리(위치)를 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| `auto` | 브라우저가 계산 | `auto` |
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |

## `left`

요소의 `position` 기준에 맞는 '왼쪽'에서의 거리(위치)를 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| `auto` | 브라우저가 계산 | `auto` |
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |

## `right`

요소의 `position` 기준에 맞는 '오른쪽'에서의 거리(위치)를 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| `auto` | 브라우저가 계산 | `auto` |
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |

## `z-index`

`position`이 지정된 요소의 '요소 쌓임' 정도를 설정

> `static`을 제외한 `position`속성이 있을 경우만 사용 가능.

| 값 | 의미 | 기본값 |
|---|---|---|
| `auto` | 부모요소와 동일란 '요소 쌓임' 정도로 설정 (`0`) | `auto` |
| 숫자 | 단위 없음, 숫자가 높을수록 위에 쌓임 |  |

### 사용법

```html
<div class="box box1"></div> <!-- box2 보다 위에 쌓임 -->
<div class="box box2"></div>
```

```css
.box {
  width: 100px;
  height: 100px;
  background: red;
  position: relative;
}
.box1 {
  z-index: 1;
}
```
