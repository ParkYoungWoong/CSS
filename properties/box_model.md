# 요소의 모양 (Box model)

## `margin`

요소의 바깥쪽 여백을 지정

| 값 | 의미 | 기본값 |
|---|---|---|
| 단위 | `px`, `cm` 등 단위로 지정 | `0` |
| `auto` | 브라우저가 너비를 계산 |  |
| `%` | 부모 요소의 너비에 대한 비율로 지정 |  |

### 마진 중복 (병합, Margin Collapse)

마진의 특정 값들이 중복되어 합쳐지는 현상

1. 형제 요소들의 `margin-top`과 `margin-bottom` 이 만났을 때.
1. 부모 요소의 `margin-top`과 자식 요소의 `margin-top`이 만났을 때.
1. 부모 요소의 `margin-bottom`과 자식 요소의 `margin-bottom`이 만났을 때.

<p data-height="265" data-theme-id="dark" data-slug-hash="EmpzKP" data-default-tab="css,result" data-user="heropark" data-embed-version="2" data-pen-title="Margin Collapse 1" class="codepen">See the Pen <a href="https://codepen.io/heropark/pen/EmpzKP/">Margin Collapse 1</a> by park young woong (<a href="http://codepen.io/heropark">@heropark</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
