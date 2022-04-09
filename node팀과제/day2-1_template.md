## 템플릿 엔진

### 강의에서 사용한 방식은?
> 정적파일(HTML)을 클라이언트로 전송
```javascript
router.get("/", (req, res) => {
  return res.sendFile(path.join(__dirname, "/index.html");
});
``` 
```html
$.ajax({
    type: "GET",
    url: '/posts',
    success: () => {
    },
    error: () => {
    }
});
```

```javascript
router.get("/posts", async (req, res) => {
  const posts = await Posts.find({});
  return res.json(posts);
});
```
장점
1. 익숙한 HTML을 사용하여 화면 구성

단점
1. 데이터를 동적으로 삽입하기 어려움   

<hr>
 
### 템플릿 엔진 (PUG)
> 클라이언트의 요청을 반영하여 응답
```javascript
router.get("/", async (req, res) => {
  const posts = await Posts.find({});
  return res.render("main", { posts });
});
```

```jade
body
    each post in posts
        h3=post.title
        h4=post.author
```

장점
1. HTML을 자바스크립트로 컨트롤할 수 있음

단점
1. 템플릿 엔진의 사용방법을 익혀야 함
