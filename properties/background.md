# 배경 (Background)

## `background`

요소의 배경을 설정 (단축속성)

| 값 | 의미 | 기본값 |
|---|---|---|
| `background-color` | 배경 색상 | `transparent` |
| `background-image` | 하나 이상의 배경 이미지 | `none` |
| `background-repeat` | 배경 이미지의 반복 | `repeat` |
| `background-position` | 배경 이미지의 위치 | `0 0` |
| `background-size` | 배경 이미지의 크기 | `auto` |
| `background-origin` | 배경 이미지의 위치 범위 | `padding-box` |
| `background-clip` | 배경(색상 포함)이 나올 범위 | `border-box` |
| `background-attachment` | 배경 이미지의 스크롤 여부 | `scroll` |

### 사용법

```
background: COLOR IMAGE REPEAT POSITION / SIZE (ORIGIN CLIP) ATTACHMENT;
```

```css
.example1 {
  background: red url("../img/image.jpg") no-repeat left top / cover padding-box border-box scroll;
  /* COLOR IMAGE REPEAT POSITION(direction) / SIZE ORIGIN CLIP ATTACHMENT */
}
.example2 {
  background: url("../img/image.jpg") no-repeat 50px 100px / auto 100% content-box;
  /* IMAGE REPEAT POSITION(L,T) / SIZE (ORIGIN CLIP) */
}
.example3 {
  background: url("../img/image.jpg") no-repeat right 100px;
  /* IMAGE REPEAT POSITION(direction + T) */
}
.example4 {
  background: red;
  /* COLOR */
}
```

### 개별속성들

#### `background-color`

요소의 배경 색상을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 색상 | 요소의 배경 색상 |  |
| `transparent` | 투명 | `transparent` |

##### 사용법

```
background-color: COLOR;
```

```css
.example1 {
  background-color: red;
}
.example2 {
  background-color: #000;
}
.example3 {
  background-color: rgba(255,0,0,.5);
  /* Red Green Blue Alpha */
}
```

#### `background-image`

요소의 배경에 하나 이상의 이미지를 삽입

> 이미지를 사용할 수 없는 경우 배경 색상을 지정하세요.

| 값 | 의미 | 기본값 |
|---|---|---|
| url("경로") | 이미지 경로(URL) |  |
| `none` | 이미지 없음 | `none` |

##### 사용법

배경 이미지 삽입 시, 요소의 크기가 설정되어 있어야 배경 이미지가 보임.

```
background-image: url("URL");
```

```css
.example {
  background-image: url("../img/image.jpg");
  width: 120px;
  height: 80px;
}
```

하나 이상의 배경 이미지를 삽입할 경우 `,`로 구분  
(먼저 작성된 이미지 경로가 위에 쌓임)

> 하나 이상의 배경 이미지 사용은 IE8 이하 버전에서 지원 불가

```css
.example1 {
  /* 개별속성 */
  background-image: url("../img/i1.jpg")
    , url("../img/i2.jpg")
    , url("../img/i3.jpg");
}
.example2 {
  /* 단축속성 */
  background: url("../img/i1.jpg") no-repeat
    , url("../img/i2.jpg") no-repeat 100px 50px
    , url("../img/i3.jpg") repeat-x;
}
```

#### `background-repeat`

배경 이미지의 반복을 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| `repeat` | 배경 이미지를 수직, 수평으로 반복 | `repeat` |
| `repeat-x` | 배경 이미지를 수평으로 반복 |  |
| `repeat-y` | 배경 이미지를 수직으로 반복 |  |
| `no-repeat` | 반복 없음 |  |

##### 사용법

```
background-repeat: REPEAT;
```

```css
.example {
  background-image: url("../img/image.jpg");
  background-repeat: no-repeat;
  width: 300px;
  height: 200px;
}
```

#### `background-position`

배경 이미지의 위치를 설정

| 값 | 의미 | 기본값 |
|---|---|---|
| 방향 | 방향을 입력하여 위치 설정<br> `top`, `bottom`, `left`, `right`, `center` |  |
| `%` | 왼쪽 상단 모서리는 `0% 0%`, 오른쪽 하단 모서리는 `100% 100%` | `0% 0%` |
| 단위 | `px`, `cm` 등 단위로 지정 |  |

##### 사용법

```
background-position: (VALUE1 VALUE2);
```

값이 방향일 경우

```
background-position: (방향1, 방향2);
```

값이 단위(`%`, `px` 등)일 경우

```
background-position: (X축, Y축);
```

```css
.example {
  background-position: left top; /* 왼쪽, 위쪽 */
  background-position: top left; /* 위쪽, 왼쪽  */
  background-position: center center; /* 가운데, 가운데 */
  background-position: center; /* 가운데, 가운데 */

  background-position: 0% 0%; /* X: 0%, Y: 0% */
  background-position: 0 0; /* X: 0, Y: 0 (추천!) */
  background-position: 20% 50%; /* X: 20%, Y: 50% */
  background-position: 10%; /* X: 10%, Y: 0% */
  background-position: 50%; /* X: 50%, Y: 50% (가운데) */
  background-position: 10px 20px; /* X: 10px, Y: 20px */
  background-position: 10px; /* X: 10px, Y: 0 */
  background-position: 50% 30px; /* X: 50%, Y: 30px */

  background-position: 30% bottom; /* X: 30%, 아래쪽 */
  background-position: left 50px; /* 왼쪽, Y: 50px */
  background-position: 50px left; /* ERROR */
  background-position: top 30%; /* ERROR */
}
```

#### `background-size`

배경 이미지의 크기를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `auto` |  | `auto` |
| 단위 | `px`, `cm` 등 단위로 지정 |  |
| `%` | 요소의 크기에 비례하여 지정.<br>`background-attachment: fixed;`가 지정되어 있을 경우 브라우저에 크기에 비례하여 지정됨. |  |
| `cover` | 배경 이미지가 가능한 한 가장 크게 되도록 비율 조정.<br>요소의 전체 가로나 세로 너비를 덮음. |  |
| `contain` | 배경 이미지의 가로, 세로 너비가 내용 영역 안에 모두 들어갈 수 범위에서 최대 크기로 조정 |  |

##### 사용법

```
background-size: (VALUE1 VALUE2);
```

```css
.example {
  width: 100px;
  height: 200px;
  background-image: url("../img/image.jpg"); /* 20 x 20(px) */

  background-size: auto; /* 20px, 20px */
  background-size: 50px 100px; /* 50px, 100px (비율 깨짐) */
  background-size: auto 50px; /* 50px, 50px */
  background-size: 50px; /* 50px, auto = 50px, 50px */
  background-size: 50% 50%; /* 50px, 100px (비율 깨짐) */
  background-size: 50%; /* 50px, auto = 50px, 50px */

  background-size: cover; /* 200px, 200px (오른쪽 넘침) */
  background-size: contain; /* 100px, 100px */
  background-size: cover contain; /* ERROR */
}
```

`background-attachment: fixed`가 지정되어 있을 경우, `%`, `cover`, `contain` 값은 브라우저의 크기에 비례하여 지정됨.

```css
/* 브라우저 크기: 1600px, 800px 일 경우 */
.example {
  width: 100px;
  height: 200px;
  background-image: url("../img/image.jpg"); /* 20 x 20(px) */
  background-attachment: fixed;

  background-size: auto; /* 20px, 20px */
  background-size: 50px; /* 50px, auto = 50px, 50px */
  background-size: 50%; /* 800px, 800px */
  background-size: cover; /* 1600px, 1600px */
  background-size: contain; /* 800px, 800px */
}
```

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 4.0(1.0) | 9.0 | 4.0(3.6) | 4.1(3.0) | 10.5(10.0) |

#### `background-origin`

#### `background-clip`

#### `background-attachment`
