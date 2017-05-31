# 애니메이션 전환 (Transition)

## `transition`

요소의 속성 변화에 전환(애니메이션) 효과를 추가 (단축속성)

| 값 | 의미 | 기본값 |
|---|---|---|
| `transition-property` | 전환 효과를 적용할 CSS 속성 | `all` |
| `transition-duration` | 전환 효과를 완료하는데 걸리는 시간 | `0s` |
| `transition-timing-function` | 전환 효과의 속도 곡선 | `ease` |
| `transition-delay` | 전환 효과가 언제 시작할지 '대기시간'을 지정 | `0s` |

### 사용법

```
transition: 속성 시간 시간함수 대기시간;
```

```css
.example {
  width: 100px;
  height: 100px;
  background: red;
  transition: all .5s ease-in-out 1s;
}
.example:hover {
  background: blue;
}
```

```css
.example {
  transition: 2s; /* all 2s ease 0s */
}
```

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 26.0(4.0) | 10.0 | 16.0(4.0) | 6.1(3.1) | 12.1(10.5) |

### 개별속성들

#### `transition-property`

전환(애니메이션) 효과를 적용할 CSS 속성을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `none` | 전환 효과 없음 |  |
| `all` | 모든 속성에 전환 효과 적용 | `all` |
| 속성명 | 전환 효과를 적용할 속성의 이름을 '쉼표'로 구분하여 작성 |  |

##### 사용법

```
transition-property: 속성명;
```

```css
.example {
  width: 100px;
  height: 100px;
  background: red;
  transition-property: width, height;
  transition-duration: 1s;
}
.example:hover {
  width: 200px;
  height: 200px;
}
```

단축속성을 사용하여 속성을 구분할 경우 `duration`을 속성마다 적용

```css
.example {
  transition: width 1s, height 1s; /* 단축속성 */
}
```

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 26.0(4.0) | 10.0 | 16.0(4.0) | 6.1(3.1) | 12.1(10.5) |

#### `transition-duration`

전환(애니메이션) 효과를 완료하는데 걸리는 시간을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 시간 | 전환 효과를 완료하는데 걸리는 시간 | `0s` |

##### 사용법

```
transition-duration: 시간;
```

```css
.example {
  transition-duration: 1s;
  transition-duration: 2.4s;
  transition-duration: .5s; /* 0.5초 */
}
```

| Browsers | CR | IE/EG | FF | SF | OP |
|---|---|---|---|---|---|
| Version | 26.0(4.0) | 10.0 | 16.0(4.0) | 6.1(3.1) | 12.1(10.5) |

#### `transition-timing-function`

전환(애니메이션) 효과의 속도 곡선을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| `ease` | 빠르게 >> 느리게 | `ease` |
| `linear` | 일정하게 |  |
| `ease-in` | 느리게 >> 빠르게 |  |
| `ease-out` | 빠르게 >> 느리게 |  |
| `ease-in-out` | 느리게 >> 빠르게 >> 느리게 |  |
| `steps(n, start|end)` | 애니메이션을 `n`번 분할하여 보여줌 /<br>`n`은 양의 정수로 지정, `start` 혹은 `end`는 간격 내에서 값 변경이 발생하는 지점을 지정, 생략하면 `end`로 설정됨 |  |
| `step-start` | `steps(1, start)`와 동일  |  |
| `step-end` | `steps(1, end)`와 동일 |  |
| `cubic-bezier(n,n,n,n)` | 자신의 값을 정의(`0`과 `1` 사이의 값) |  |

> [Easing Functions Cheat sheet](http://easings.net/ko) 에서 값을 선택할 수 있습니다.

> [Cubic Bezier](http://cubic-bezier.com/) 에서 값을 선택할 수 있습니다.

##### 사용법

```
transition-timing-function: 시간함수;
```

```css
.example {
  transition-timing-function: linear;
  transition-timing-function: ease-in-out;
  transition-timing-function: steps(3);
  transition-timing-function: steps(10, start);
  transition-timing-function: cubic-bezier(.17,.67,.83,.67); /* `ease` 와 동일 */
}
```

###### `step`속성의 `start`와 `end` 차이점

`start`의 경우 각 분할된 애니메이션의 '앞'에서 전환을 보여줌

```css
.start {
  width: 100px;
  height: 100px;
  background: red;
  transition: 3s step-start; /* `steps(1, start)` 과 동일 */
}
.start:hover {
  background: blue;
}
```

`end`의 경우 각 분할된 애니메이션의 '뒤'에서 전환을 보여줌

```css
.end {
  width: 100px;
  height: 100px;
  background: red;
  transition: 3s step-end; /* `steps(1, end)`, `steps(1)` 과 동일 */
}
.end:hover {
  background: blue;
}
```

#### `transition-delay`

전환(애니메이션) 효과가 언제 시작할지 '대기시간'을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 시간 | 전환 효과가 언제 시작할지 '대기시간'을 설정 | `0s` |
