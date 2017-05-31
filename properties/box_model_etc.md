# 모양 (기타, Box model - etc)

## TOC

| 속성 | 의미 | 특이사항 |
|---|---|---|
| `box-sizing` | 요소의 크기에 `padding`, `border` 포함 여부 |  |
| `box-shadow` | 요소의 그림자 지정 |  |
| `overflow` | 내용(자식요소) 넘쳤을 때 |  |
| `overflow-x` | 내용이 X축으로 넘쳤을 때 |  |
| `overflow-y` | 내용이 Y축으로 넘쳤을 때 |  |
| `visibility` | 내용의 보여짐을 지정 | 다른 속성들과 비교 |
| `opacity` | 요소의 투명도 지정 |  |
| `border-image` | 테두리 선으로 사용될 이미지 설정 |  |
| `border-image-source` |  |  |
| `border-image-slice` |  |  |
| `border-image-width` |  |  |
| `border-image-outset` |  |  |
| `border-image-repeat` |  |  |

## `box-sizing`

요소의 크기(`width`, `height`)에 포함되는 박스모델(box model)을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `content-box` | 요소의 크기에 내용만 포함 | `content-box` |
| `border-box` | 요소의 크기에 `padding`, `border`를 포함,<br> `margin`은 포함하지 않음 |  |

### 사용법

#### 일반 사용

`padding`, `border`가 있을 때 요소의 크기가 변하거나 변하지 않음

```css
.box1 { /* 420 x 220(px) */
  width: 300px;
  height: 100px;
  padding: 50px;
  border: 10px solid red;
}
.box2 { /* 300 x 100(px) */
  width: 300px;
  height: 100px;
  padding: 50px;
  border: 10px solid red;
  box-sizing: border-box;
}
```

#### 응용

`border`가 포함된 `25%`너비의 4개 요소를 수평 정렬 후, 총 너비를 `100%`로 유지하기 위해 `box-sizing` 사용.

```html
<ul class="list">
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

```css
.list li { /* 25% x 4(<li></li>) = 100% */
  float: left;
  width: 25%;
  border: 1px solid red;
  box-sizing: border-box;
}
```

## `box-shadow`

요소에 하나 이상의 그림자를 추가

```
box-shadow: 수평 수직 흐림 크기 색상 내부;
```

| 값 | 의미 | 기본값 |
|---|---|---|
| `none` | 그림자 없음 | `none` |
| h-shadow | `필수`, 수평 그림자 위치 (음수 허용) |  |
| v-shadow | `필수`, 수직 그림자 위치 (음수 허용) |  |
| blur | 흐려짐의 크기(거리) |  |
| spread | 그림자의 크기 |  |
| color | 그림자의 색상 ('SF'에서는 `필수`) | `black` |
| `inset` | 외부 그림자를 내부 그림자로 변경 |  |

### 사용법

```css
.box1 {
  width: 300px;
  height: 100px;
  box-shadow: 10px 20px 5px red; /* 수평 수직 흐림 색상 */
}
.box2 {
  width: 300px;
  height: 100px;
  /* Multiple shadows, 쉼표로 구분 */
  box-shadow: 0 0 10px 5px blue inset,
    10px 10px 10px green,
    20px 20px 10px 10px yellow inset;
}
```

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 10.0(4.0) | 9.0 | 4.0(3.5) | 5.1(3.1) | 10.5 |

## `overflow`

요소의 크기 이상으로 내용(자식요소)이 넘쳤을 때, 내용의 보여짐을 제어

| 값 | 의미 | 기본값 |
|---|---|---|
| `visible` | 넘친 부분이 잘리지 않고 그대로 보임 | `visible` |
| `hidden` | 넘친 부분을 잘라내고, 보이지 않도록 함 |  |
| `scroll` | 넘친 부분을 잘라내고, 스크롤바를 이용하여 볼 수 있도록 함 |  |
| `auto` | 넘친 부분이 있는 경우만 잘라내고, 스크롤바를 이용하여 볼 있도록 함 |  |

### `overflow-x`

요소의 X축(좌,우)으로 내용이 넘쳤을 때, `overflow` 지정

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 4.0 | 9.0(8.0) | 3.5 | 3.0 | 9.5 |

### `overflow-y`

요소의 Y축(위,아래)으로 내용이 넘쳤을 때, `overflow` 지정

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 4.0 | 9.0(8.0) | 3.5 | 3.0 | 9.5 |

## `visibility`

요소의 보여짐을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `visible` | 요소가 보여짐 | `visible` |
| `hidden` | 요소가 보여지지 않음(여전히 공간은 차지) |  |
| `collapse` | 표(table)에서만 사용 가능, 행이나 열을 보여지지 않게 할 수 있으나 표 레이아웃에는 영향이 없음.<br> (표의 모든 부분에 대한 너비와 높이를 다시 계산하지 않고도 표 내의 행과 열을 빠르게 제거할 수 있도록 설계, 다른 요소에서 사용된다면 `hidden`으로 적용) |  |

### 다른 속성들과 비교

|  | 보여지지 않음 | 클릭되지 않음 | 실제 제거됨 | `transition` 사용 |
|---|:---:|:---:|:---:|:---:|
| `opacity(0);` | O | X | X | O |
| `visibility(hidden)` | O | O | X | O |
| `display(none)` | O | O | O | X |
| `pointer-events(none)` | X | O | X | X |

## `opacity`

요소의 투명도를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 숫자 | `0`부터 `1`사이의 소수점 숫자 | `1` |

### 사용법

```
opacity: OPACITY;
```

```css
.half {
  opacity: 0.5; /* 50% 투명도, 반투명 */
}
.transparent {
  opacity: 0; /* 0% 투명도, 투명 */
}
```

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 4.0 | 9.0 | 2.0 | 3.1 | 9.0 |

## `border-image`

일반 `border` 대신에 사용될 이미지를 설정 (단축속성)

| 값 | 의미 | 기본값 |
|---|---|---|
| `border-image-source` | 사용할 이미지 경로 |  |
| `border-image-slice` |  |  |
| `border-image-width` |  |  |
| `border-image-outset` |  |  |
| `border-image-repeat` |  |  |

### `border-image-source`

### `border-image-slice`

### `border-image-width`

### `border-image-outset`

### `border-image-repeat`
