---
title: CSS - 요소 쌓임 순서 (position, z-index)
tags: CSS TIL
key: page-202106110748
summary: css에서 요소가 쌓이는 순서를 알아보자
---

## 요소 쌓임 순서 (Stack order)

요소가 쌓여 있는 순서를 통해 어떤 요소가 더 위에 쌓이는지를 알아보자

1. static을 제외한 `position`속성의 값이 있는 경우 제일 위에 쌓인다.
2. `position`속성이 모두 존재할 경우 `z-index`속성의 값으로 위에 쌓인다. (큰 수가 더 위로간다.)
3. `position`속성이 존재하고 `z-index`속성의 수가 같다면, html에서 마지막에 작성한 코드가 위에 쌓인다.

`position > z-index > 마지막 작성된 코드`순으로 요소가 쌓인다.

<br/>

<p class="codepen" data-height="300" data-theme-id="light" data-default-tab="css,result" data-user="hhyemi" data-slug-hash="wvJYMGB" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="wvJYMGB">
  <span>See the Pen <a href="https://codepen.io/hhyemi/pen/wvJYMGB">
  wvJYMGB</a> by Hyemi Lee (<a href="https://codepen.io/hhyemi">@hhyemi</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
<br/>

#### :heavy_check_mark: box1과 box2 비교

box1에 `position`속성이 있기 때문에 box1이 box2보다 위에 쌓인다.

#### :heavy_check_mark: box3과 box4 비교

box3와 box4 모두 `position`속성이 있기 때문에 `z-index`의 숫자가 높은 box3이 box4보다위에 쌓인다.

#### :heavy_check_mark: box4과 box4 비교

box4와 box5 모두 `position`속성이 있고 `z-index`의 숫자가 같기 때문에 마지막에 작성된 box5이 box4보다위에 쌓인다.

<br/><br/>
