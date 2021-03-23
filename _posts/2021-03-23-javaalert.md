---
title: Java - Java에서 Alert창 띄우기
tags: Java
key: page-202103232304
summary : 자바에서 알림창을 띄워보자
---

## 자바에서 알림창 띄우기
```
response.setContentType("text/html; charset=UTF-8");
PrintWriter out = response.getWriter();

out.println("<script language='javascript'>');
out.println("alert('알림창')");
out.println("</script>");

out.flush();
```
**알림창**이라고 alert가 뜨는 것을 볼 수 있다. <br/>
자바에서 사용할 일이 있어서 찾았던 내용이다.
<br/><br/>
