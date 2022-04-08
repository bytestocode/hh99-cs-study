## REST API: PUT vs PATCH

> put: 전체 변경   
> patch: 부분 변경

### 예시
```javascript
// 원본 데이터
{
  "name": "coco",
  "age": 33,
}

// PUT
{
  "name": "costco",
  "age": 47,
}

// PATCH
{
  "age": 32,
}
```