## for 문

> for 문이 있는데 for ... in for...of 문법이 새로 나온 이유는 무엇일까요? 우리가 이것을 고르는 기준은 무엇일까요?

```javascript
let arr = [1, 2, 3]

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);  // 1 2 3
}
```

## for...in

> 객체의 모든 프로퍼티를 순회   
> 프로퍼티의 키를 할당

```javascript
arr = [1, 2, 3]
arr.x = 10;

for (const i in arr) {
  console.log(arr[i]);  // 1 2 3 10
}

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);  // 1 2 3
}
```

## for...of

> 이터러블을 순회   
> 이터러블의 요소를 할당

```javascript
arr = [1, 2, 3]

for (const item of arr) {
  console.log(item);  // 1 2 3
}

const iterable = [1, 2, 3];
const iterator = iterable[Symbol.iterator]();

for (; ;) {
  const res = iterator.next();  // { value: 1, done: false }
  if (res.done) break;
  const item = res.value;
  console.log(item);  // 1 2 3
}
```

## 이유

1. 반복문은 프로그래밍에서 굉장히 많이 활용되는 문법이므로, 쉽게 사용할 수 있는 방법이 있으면 개발자의 삶이 행복해 질 것으로 보입니다. 따라서 조금이라도 더 편리한 방법들이 나오게 된 것 같습니다.

## 선택 기준

1. for...in 사용 지양 (문법상 하자 있음)
2. for문 사용 지양 (의도 파악 어려움) => 배열 메서드 사용 추천 (forEach, filter, map, reduce 등)
