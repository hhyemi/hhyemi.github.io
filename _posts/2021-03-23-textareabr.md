---
title: HTML - textarea에서 줄바꿈처리하기
tags: HTML
key: page-202103232315
summary : textarea에서 처리해보자
---

## textarea에서 개행처리하기
```html
<textarea>
줄바꿈 해주세요 <br/> \n 개행처리\r하기 &#10; 줄바꿔지나요
</textarea>
```
<img src="/assets/images/htmlbr.png" height="260"/><br/><br/>
textarea안에서 `<br/>`과 `\r` `\n` `\r\n`으로 줄바꿈 처리를 할 수 없다. <br/>
```javascript
&#10;
```
&#10; 을 이용하면 줄바꿈 처리가 가능하다.

<br/><br/>
