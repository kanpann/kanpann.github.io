---
layout: post
title: ajax 200 성공 반환하는데 success 호출 안되는 문제
category: JavaScript
tag: [JavaScript]
---

![image](https://user-images.githubusercontent.com/45007556/91047538-32604500-e655-11ea-8aa8-50c53e222fc7.png)

# 문제

```js
$.ajax({
  url: "/reply/api/",
  type: "POST",
  contentType: "application/json",
  data: JSON.stringify({
    postsId: postsId,
    content: replyContent,
  }),
  dataType: "json",
  success: function () {
    alert("댓글 입력");
  },
});
```

위에 코드를 실행했을 때 200을 반환하는데도 success 함수가 무슨 짓을 해도 호출이 되지 않아서 삽질한 내용

# 해결 방법

```js
$.ajax({
  url: "/reply/api/",
  type: "POST",
  contentType: "application/json",
  data: JSON.stringify({
    postsId: postsId,
    content: replyContent,
  }),
  success: function () {
    alert("댓글 입력");
  },
});
```

> dataType: 'json' 을 삭제해주면 된다.

일단 이렇게 해결은 했으나 원인은 서버에서 넘어오는 데이터가 json형식이 아닌게 아닌가 추측중이다