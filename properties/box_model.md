# 요소의 모양 (Box model)

## `margin`

요소의 '바깥쪽 여백'을 지정 (`단축속성`)

| 값 | 의미 | 기본값 |
|---|---|---|
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |
| `auto` | 브라우저가 너비를 계산 |  |
| `%` | 부모 요소의 너비에 대한 비율로 지정 |  |

### 단축속성 사용법

#### 값이 4개일 경우

```
margin: TOP RIGHT BOTTOM LEFT;
```

```css
.hello {
  margin: 10px 20px 30px 40px;
  /*
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 40px;
  */
}
```

#### 값이 2개일 경우

```
margin: (TOP,BOTTOM) (LEFT,RIGHT)
```

```css
.hello {
  margin: 10px 30px;
  /*
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 30px;
  margin-right: 30px;
  */
}
```

#### 값이 1개일 경우

```
margin: (TOP,BOTTOM,LEFT,RIGHT)
```

```css
.hello {
  margin: 10px;
  /*
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  */
}
```

### 마진 중복 현상 (병합, Margin Collapse)

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

#### 부모와 자식 요소에서 중복 해결

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

### `margin-top`

요소의 '바깥 위쪽 여백'을 지정

### `margin-bottom`

요소의 '바깥 아래쪽 여백'을 지정

### `margin-left`

요소의 '바깥 왼쪽 여백'을 지정

### `margin-right`

요소의 '바깥 오른쪽 여백'을 지정

## `padding`

요소의 '안쪽 여백'을 지정 (`단축속성`)

| 값 | 의미 | 기본값 |
|---|---|---|
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |
| `%` | 부모 요소의 너비에 대한 비율로 지정 |  |
