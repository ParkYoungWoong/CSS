# 글자 1 (Font - Basic)

## `font`

글자 관련 속성들을 지정 (단축속성)

| 값 | 의미 | 기본값 |
|---|---|---|
| `font-style` | 글자 기울기 지정 | `normal` |
| `font-variant` | 글자를 '작은 대문자 폰트'로 표기할지 지정 | `normal` |
| `font-weight` | 글자 두께 지정 | `normal` |
| `font-size` | 글자 크기 지정 | `medium`(`16px`) |
| `line-height` | 줄 높이(줄 간격) 지정 | `normal`(`1.2`) |
| `font-family` | 글꼴(서체) 지정 | 운영체제(브라우저)에 따라 달라짐 |
| `caption` | '캡션'이 지정된 컨트롤(버튼 등)에 사용된 시스템 글꼴을 사용 |  |
| `icon` | '아이콘 라벨'에 사용된 시스템 글꼴을 사용 |  |
| `menu` | '드롭다운 메뉴' 등에 사용된 시스템 글꼴을 사용 |  |
| `message-box` | '대화 상자'에 사용된 시스템 글꼴을 사용 |  |
| `small-caption` | `caption`글꼴의 더 작은 버전 |  |
| `status-bar` | '상태 표시 줄'에 사용된 시스템 글꼴을 사용 |  |

### 사용법

```
font: 기울기 대문자변환 두께 크기 / 줄높이 글꼴;
```

```css
.example {  
  font: italic normal bold 20px / 1.5 "Arial", sans-serif;
  /*
  font-style: italic;
  font-variant: normal;
  font-weight: bold;
  font-size: 20px;
  line-height: 1.5;
  font-family: "Arial", sans-serif;
  */
}
```

`font-size`, `font-family` 필수로 사용!

```css
.example {
  font: 30px / 1.5;  /* ERROR */
  font: bold;  /* ERROR */
  font: bold sans-serif;  /* ERROR */
  font: 30px / 1.5 sans-serif;
  font: bold 30px sans-serif;
  font: italic 30px / 1.5 "Arial", sans-serif;
}
```

### `font-style`

글자 스타일(기울기)을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `normal` | 스타일 없음 | `normal` |
| `italic` | 이텔릭체(활자) |  |
| `oblique` | 기울어진 글자 |  |

#### 사용법

```
font-style: 스타일;
```

```css
.example {
  font-style: italic;
}
```

### `font-variant`

모든 소문자를 대문자로 변환, 변환된 대문자는 텍스트의 원래 대문자보다 작은 크기로 표시됨. (작은 대문자 폰트)

| 값 | 의미 | 기본값 |
|---|---|---|
| `normal` | 변환 없음 | `normal` |
| `small-caps` | '작은 대문자 폰트'로 변환 |  |

#### 사용법

```
font-variant: 대문자변환;
```

```css
.example {
  font-variant: small-caps;  /* 작은 대문자 폰트로 변환 */
}
```

### `font-weight`

글자의 두께(가중치)를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `normal` | 기본 글자 두께, `400`과 같음 | `normal`(`400`) |
| `bold` | 글자 두껍게, `700`과 같음 |  |
| `bolder` | 부모(상위) 요소보다 더 두껍게<br>(`bold` 보다 두껍다는 개념 아님) |  |
| `lighter` | 부모(상위) 요소보다 더 얇게 |  |
| 숫자 | `100`부터 `900`까지의 100단위의 숫자 9개, `normal`과 `bold` 이외의 두께를 제공하는 글꼴을 위한 설정 |  |

#### 사용법

```
font-weight: 두께;
```

```css
.example {
  font-weight: bold;
  font-weight: 600;
}
```

#### 상대적 두께

`bolder`나 `lighter`를 사용할 경우 부모(상위) 요소로 부터 상속받은 값에서 다음과 같이 계산됨.

| 상속값 | `bolder` | `lighter` |
|---|---|---|
| `100` | `400` | `100` |
| `200` | `400` | `100` |
| `300` | `400` | `100` |
| `400` | `700` | `100` |
| `500` | `700` | `100` |
| `600` | `900` | `400` |
| `700` | `900` | `400` |
| `800` | `900` | `700` |
| `900` | `900` | `700` |

#### 일반적인 두께 이름

`font-weight`의 각 값은 일반적으로 다음과 같은 글꼴의 이름으로 표현됨.

| 값 | 일반적인 두께 이름 |
|---|---|
| `100` | Thin (Hairline) |
| `200` | Extra Light (Ultra Light) |
| `300` | Light |
| `400` | Normal |
| `500` | Medium |
| `600` | Semi Bold (Demi Bold) |
| `700` | Bold |
| `800` | Extra Bold (Ultra Bold) |
| `900` | Black (Heavy) |

#### 특성: 숫자와 두께가 일치하지 않을 경우

글꼴(서체)의 정확한 두께를 숫자로 표현할 수 없는 경우 아래와 같이 적용됨.

1. `400`이 주어지면 `500` 사용, `500`이 불가하면 `500`미만의 두께 사용
1. `500`이 주어지면 `400` 사용, `400`이 불가하면 `400`미만의 두께 사용
1. `400`미만 값이 주어지면, 가장 가까운 숫자의 얇은 두께 사용
1. `500`초과 값이 주어지면, 가장 가까운 숫자의 두꺼운 두께 사용

### `font-size`

글자의 크기를 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 단위 | `px`, `cm` 등 단위로 지정 | `16px` |
| `%` | 부모(상위) 요소의 비율로 지정 |  |
| `medium` |  | `medium` |
| `xx-small` |  |  |
| `x-small` |  |  |
| `small` |  |  |
| `large` |  |  |
| `x-large` |  |  |
| `xx-large` |  |  |
| `smaller` | 부모(상위) 요소보다 작은 크기 |  |
| `larger` | 부모(상위) 요소보다 큰 크기 |  |

### `line-height`

### `font-family`
