# 모양 (Box model - Space)

## TOC

| 속성 | 의미 | 특이사항 |
|---|---|---|
| `margin` | 바깥 여백 | 마진 중복, 값이 1~4개일 때 |
| `margin-top` | 바깥 위쪽 여백 |  |
| `margin-bottom` | 바깥 아래쪽 여백 |  |
| `margin-left` | 바깥 왼쪽 여백 |  |
| `margin-right` | 바깥 오른쪽 여백 |  |
| `padding` | 내부 여백 | 크기 증가, 값이 1~4개일 때 |
| `padding-top` | 내부 위쪽 여백 |  |
| `padding-bottom` | 내부 아래쪽 여백 |  |
| `padding-left` | 내부 왼쪽 여백 |  |
| `padding-right` | 내부 오른쪽 여백 |  |
| `border` | 테두리 선 | 크기 증가 |
| `border-width` | 선의 두께 | 값이 1~4개일 때 |
| `border-style` | 선의 종류 | 값이 1~4개일 때 |
| `border-color` | 선의 색상 | 값이 1~4개일 때 |
| `border-top` | 위쪽 선 |  |
| `border-top-width` | 위쪽 선의 두께 |  |
| `border-top-style` | 위쪽 선의 종류 |  |
| `border-top-color` | 위쪽 선의 색상 |  |
| `border-bottom-top` | 아래쪽 선 |  |
| `border-bottom-width` | 아래쪽 선의 두께 |  |
| `border-bottom-style` | 아래쪽 선의 종류 |  |
| `border-bottom-color` | 아래쪽 선의 색상 |  |
| `border-left` | 왼쪽 선 |  |
| `border-left-width` | 왼쪽 선의 두께 |  |
| `border-left-style` | 왼쪽 선의 종류 |  |
| `border-left-color` | 왼쪽 선의 색상 |  |
| `border-right` | 오른쪽 선 |  |
| `border-right-width` | 오른쪽 선의 두께 |  |
| `border-right-style` | 오른쪽 선의 종류 |  |
| `border-right-color` | 오른쪽 선의 색상 |  |

## `margin`

요소의 '바깥(외부) 여백'을 지정 (`단축속성`)

| 값 | 의미 | 기본값 |
|---|---|---|
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |
| `auto` | 브라우저가 너비를 계산 |  |
| `%` | 부모 요소의 너비에 대한 비율로 지정 |  |

### 사용법

하단 공통 사용법 [(값(단위)이 1~4개일 경우)](#margin-padding-border-공통-사용법-값단위이-14개일-경우) 참조

### 특성: 마진 중복 (병합, Margin Collapse)

마진의 특정 값들이 '중복'되어 합쳐지는 현상

1. 형제 요소들의 `margin-top`과 `margin-bottom` 이 만났을 때.
1. 부모 요소의 `margin-top`과 자식 요소의 `margin-top`이 만났을 때.
1. 부모 요소의 `margin-bottom`과 자식 요소의 `margin-bottom`이 만났을 때.

#### 계산법

| 조건 | 요소 A | 요소 B | 계산법 | 중복값 |
|---|---|---|---|---|
| 둘 다 양수 | `30px` | `10px` | 더 큰 값으로 중복 | `30px` |
| 둘 다 음수 | `-30px` | `-10px` | 더 작은 값으로 중복 | `-30px` |
| 각각 양수와 음수 | `-30px` | `10px` | -30 + 10 = -20 | `-20px` |

#### 형제 요소에서 중복

```html
<div class="box"></div>
<div class="box"></div>
```

```css
.box {
  width: 200px;
  height: 100px;
  background: red;
  margin: 20px; /* Margin 중복 */
}
```

#### 부모와 자식 요소에서 중복

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  width: 300px;
  height: 200px;
  background: yellow;
}
.child {
  width: 100px;
  height: 100px;
  background: red;
  margin-top: 50px; /* Margin 중복 */
}
```

#### 해결 방법

##### 형제 요소에서 중복 해결

각 요소에 `float: left(right)` 추가  
(수직으로 정렬될 수 있도록 부모 요소의 '가로 너비'를 지정)

```html
<div class="box_group">
  <div class="box"></div>
  <div class="box"></div>
</div>
```

```css
.box_group {
  width: 200px;
}
.box {
  width: 200px;
  height: 100px;
  background: red;
  margin: 20px;
  float: left; /* 중복 해결 */
}
```

##### 부모와 자식 요소에서 중복 해결

부모 요소에 아래의 속성들 중 하나를 추가  
(무조건적 해결은 아니므로 상황에 맞게 활용)

1. `float: left(right)`
1. `overflow: hidden(auto)`, (`visible` X)
1. `position: absolute(fixed)`, (`relative` X)
1. `padding: 1px(이상)`, (`0` X)
1. `border: 1px(이상) STYLE COLOR`, (`0` X)

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  width: 300px;
  height: 200px;
  background: yellow;
  overflow: hidden; /* 중복 해결 */
}
.child {
  width: 100px;
  height: 100px;
  background: red;
  margin-top: 50px;
}
```
### 개별속성들

#### `margin-top`

요소의 '바깥 위쪽 여백'을 지정

#### `margin-bottom`

요소의 '바깥 아래쪽 여백'을 지정

#### `margin-left`

요소의 '바깥 왼쪽 여백'을 지정

#### `margin-right`

요소의 '바깥 오른쪽 여백'을 지정

## `padding`

요소의 '내부 여백'을 지정 (`단축속성`)  
음수값 (Negative valuse) 사용 불가

| 값 | 의미 | 기본값 |
|---|---|---|
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |
| `%` | 부모 요소의 너비에 대한 비율로 지정 |  |

### 사용법

하단 공통 사용법 [(값(단위)이 1~4개일 경우)](#margin-padding-border-공통-사용법-값단위이-14개일-경우) 참조

### 특성: 크기 증가

하단 공통 특성 [(크기 증가)](#padding-border-공통-특성-크기-증가) 참조

### 개별속성들

#### `padding-top`

요소의 '내부 위쪽 여백'을 지정

#### `padding-bottom`

요소의 '내부 아래쪽 여백'을 지정

#### `padding-left`

요소의 '내부 왼쪽 여백'을 지정

#### `padding-right`

요소의 '내부 오른쪽 여백'을 지정

## `border`

요소의 '테두리 선'을 지정 (`단축속성`)

| 값 | 의미 | 기본값 |
|---|---|---|
| `border-width` | 선의 두께 | `medium` |
| `border-style` | 선의 종류 | `none` |
| `border-color` | 선의 색상 | `black` |

### 사용법

```
border: WIDTH STYLE COLOR;
```

```css
.hello {
  border: 1px solid red;
}
```

### 특성: 크기 증가

하단 공통 특성 [(크기 증가)](#padding-border-공통-특성-크기-증가) 참조

### 개별속성들

#### `border-width`

선의 두께(width)를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `medium` | 중간 두께 | `medium` |
| `thin` | 얇은 두께 |  |
| `thick` | 두꺼운 두께 |  |
| 단위 | `px`, `cm` 등 단위 |  |

##### 사용법

하단 공통 사용법 [(값(단위)이 1~4개일 경우)](#margin-padding-border-공통-사용법-값단위이-14개일-경우) 참조

```css
.example {
  border-width: 10px 20px 30px;
  /*
  border-top-width: 10px;
  border-bottom-width: 30px;
  border-left-width: 20px;
  border-right-width: 20px;
  */
}
```

#### `border-style`

선의 종류(style)를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `none` | 선 없음 | `none` |
| `hidden` | 선 없음과 동일 (`table` 요소의 `border` 충돌 제외) |  |
| `dotted` | 점선 |  |
| `dashed` | 파선 |  |
| `solid` | 실선(일반선) |  |
| `double` | 두 줄선 |  |
| `groove` | 홈이 파여있는 모양(선) |  |
| `ridge` | 솟은 모양(선, `groove`의 반대) |  |
| `inset` | 전체가 들어간 모양(선) |  |
| `outset` | 전체가 나온 모양(선) |  |

##### 사용법

하단 공통 사용법 [(값(단위)이 1~4개일 경우)](#margin-padding-border-공통-사용법-값단위이-14개일-경우) 참조

```css
.example {
  border-style: solid dotted dashed double;
  /*
  border-top-style: solid;
  border-right-style: dotted;
  border-bottom-style: dashed;
  border-left-style: double;
  */
}
```

#### `border-color`

선의 색상(color)를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 색상 | 선의 색상을 지정 | `black` |
| `transparent` | 투명한 선 (요소의 배경색이 보임) |  |

##### 사용법

하단 공통 사용법 [(값(단위)이 1~4개일 경우)](#margin-padding-border-공통-사용법-값단위이-14개일-경우) 참조

```css
.example {
  border-color: red blue #000 rgba(255,255,255,.5);
  /*
  border-top-color: red;
  border-right-color: blue;
  border-bottom-color: #000;
  border-left-color: rgba(255,255,255,.5);
  */
}
```

#### `border-top`

요소의 '위쪽 선'을 지정

```
border-top: WIDTH STYLE COLOR;
```

##### `border-top-width`

요소의 '위쪽 선 두께'를 지정

```
border-top-width: WIDTH;
```

##### `border-top-style`

요소의 '위쪽 선 종류'를 지정

```
border-top-width: STYLE;
```

##### `border-top-color`

요소의 '위쪽 선 색상'을 지정

```
border-top-width: COLOR;
```

#### `border-bottom`

요소의 '아래쪽 선'을 지정

```
border-bottom: WIDTH STYLE COLOR;
```

##### `border-bottom-width`

요소의 '아래쪽 선 두께'을 지정

```
border-bottom-width: WIDTH;
```

##### `border-bottom-style`

요소의 '아래쪽 선 종류'를 지정

```
border-bottom-style: STYLE;
```

##### `border-bottom-color`

요소의 '아래쪽 선 색상'을 지정

```
border-bottom-color: COLOR;
```

#### `border-left`

요소의 '왼쪽 선'을 지정

```
border-left: WIDTH STYLE COLOR;
```

##### `border-left-width`

요소의 '왼쪽 선 두께'을 지정

```
border-left-width: WIDTH;
```

##### `border-left-style`

요소의 '왼쪽 선 종류'를 지정

```
border-left-style: STYLE;
```

##### `border-left-color`

요소의 '왼쪽 선 색상'을 지정

```
border-left-color: COLOR;
```

#### `border-right`

요소의 '오른쪽 선'을 지정

```
border-right: WIDTH STYLE COLOR;
```

##### `border-right-width`

요소의 '오른쪽 선 두께'을 지정

```
border-right-width: WIDTH;
```

##### `border-right-style`

요소의 '오른쪽 선 종류'을 지정

```
border-right-style: STYLE;
```

##### `border-right-color`

요소의 '오른쪽 선 색상'을 지정

```
border-right-color: COLOR;
```

---

## 공통

### `margin`, `padding`, `border` 공통 사용법: 값(단위)이 1~4개일 경우

#### 값이 4개일 경우

'위'을 시작으로 '시계 방향'으로 해석

```
속성: TOP RIGHT BOTTOM LEFT;
```

```css
.box {
  margin: 10px 20px 30px 40px;
  /*
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 40px;
  */
}
```

#### 값이 3개일 경우

1. 위
1. 좌우 각각
1. 아래

```
속성: TOP (LEFT,RIGHT) BOTTOM;
```

```css
.box {
  padding: 10px 20px 30px;
  /*
  padding-top: 10px;
  padding-bottom: 30px;
  padding-left: 20px;
  padding-right: 20px;
  */
}
```

#### 값이 2개일 경우

1. 위, 아래 각각
1. 좌, 우 각각

```
속성: (TOP,BOTTOM) (LEFT,RIGHT);
```

```css
.box {
  border-width: 10px 30px;
  /*
  border-top-width: 10px;
  border-bottom-width: 10px;
  border-left-width: 30px;
  border-right-width: 30px;
  */
}
```

#### 값이 1개일 경우

위, 아래, 좌, 우 모두 같은 값

```
속성: (TOP,BOTTOM,LEFT,RIGHT);
```

```css
.box {
  margin: 10px;
  /*
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  */
}
```

---

### `padding`, `border` 공통 특성: 크기 증가

추가된 `padding`, `border` 값만큼 요소의 크기가 커지는 현상

```css
.box {
  width: 100px; /* +44px = 144px */
  height: 100px; /* +24px = 124px */
  background: red;
  padding: 10px 20px;
  border: 2px solid red;
}
```

#### 크기가 커지지 않도록 해결

##### 값을 직접 계산

`padding`과 `border`를 추가하면서 `100 x 100`(px) 크기의 요소를 만들 경우,  
`padding`과 `border`가 추가된 만큼 `width`, `height`에서 계산.

```css
.box {
  width: 56px; /* +44px = 100px */
  height: 76px; /* +24px = 100px */
  background: red;
  padding: 10px 20px;
  border: 2px solid red;
}
```

##### 자동으로 계산

`padding`과 `border`를 추가하면서 `100 x 100`(px) 크기의 요소를 만들 경우,  
계산하지 않고 `box-sizing(border-box)` 를 추가.

```css
.box {
  width: 100px; /* 100px */
  height: 100px; /* 100px */
  background: red;
  padding: 10px 20px;
  border: 2px solid red;
  box-sizing: border-box;
}
```
