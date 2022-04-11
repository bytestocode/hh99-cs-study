## 몽고DB 테이블 설계

> 몽고DB로 테이블 설계를 해봅시다. 회원가입을 한 유저가 게시판에 글을 쓰는 서비스입니다. 게시판 목록 페이지에서는 게시글 제목, 작성자 이름 등이 보이겠죠? 각각의 모델은 어떤 모양새이면 좋을까요? 게시판 글 리스트를 불러오는 api 에서는 몽구스 데이터를 어떻게 가져오면 좋을까요?

### 게시글 스키마

> 데이터 타입, 필수 여부 구분

```javascript
const mongoose = require("mongoose");
const {Schema, model} = mongoose;

const postsSchema = new Schema({
  title: {type: String, required: true},
  author: {type: String, required: true},
  contents: {type: String, required: true},
  date: {type: Date, required: true, default: Date.now},
  // comments: { type: Array },
  comments: [{type: String}],
});

module.exports = model("Posts", postsSchema);
```

### 게시글 목록 조회 API

> 게시글 데이터 전체 불러오기

```javascript
router.get("/", async (req, res) => {
  const posts = await Posts.find({});
  return res.render("main", {posts});
});
```