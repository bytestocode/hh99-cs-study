## 몽고DB 테이블 설계

### 게시글 스키마
> 데이터 타입, 필수 여부 구분
```javascript
const mongoose = require("mongoose");

const postsSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true,
  },
  author: {
    type: String,
    required: true,
  },
  contents: {
    type: String,
    required: true,
  },
  date: {
    type: Date,
    required: true,
  },
  comments: {
    type: Array,
  },
});

module.exports = mongoose.model("Posts", postsSchema);
```

### 게시글 목록 조회 API
> 게시글 데이터 전체 불러오기
```javascript
router.get("/", async (req, res) => {
  const posts = await Posts.find({});
  return res.render("main", { posts });
});
```