## REST API: PUT vs PATCH

> restAPI의 put 과 patch 는 어떤 차이점이 있을까요? 어떤 경우에 사용하면 좋을까요?

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