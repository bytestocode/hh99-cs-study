## 템플릿 엔진

### 강의에서 사용한 방식은?

> 정적파일(HTML)을 클라이언트로 전송

```javascript
router.get("/", (req, res) => {
  return res.sendFile(path.join(__dirname, "/index.html");
});
```

```javascript
$(document).ready(() => {
  getGoods(null, (goods) => {
    for (let i = 0; i < goods.length; i++) {
      make_card(goods[i]);
    }
  });
});
```

```javascript
function getGoods(category, callback) {
  $("#goodsList").empty();
  $.ajax({
    type: "GET",
    url: "/api/goods",
    success: (response) => {
      callback(response["goods"]);
    },
  });
}
```

```javascript
router.get("/api/goods", async (req, res) => {
  const goods = await Goods.find({});
  return res.json({ goods });
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
  const goods = await Goods.find({});
  return res.render("main", { goods });
});
```

```jade
body
    each good in goods
        h3=good.name
        h4=good.price
```

장점

1. HTML에 데이터를 담아서 응답할 수 있음

단점

1. 템플릿 엔진의 사용방법을 익혀야 함
