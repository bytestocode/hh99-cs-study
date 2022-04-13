## npm의 require 동작 방식
> Node.js에서 리팩토링시 사용하며,    
> npm을 통해 다운로드 했던 모듈을 불러오는 require 함수는 어떻게 동작하나요?    
> IIFE와 연결지어 찾아보고 정리해보세요.

### IIFE (즉시실행함수)
#### 익명함수 (한번만 사용하기 때문에 기명으로 할 필요가 없음)
```javascript
(function () {
  let a = 3;
  let b = 5;
  return a * b;
}());
```
#### 전역 변수의 사용을 제한하는데 사용할 수 있음   
> 즉시실행함수로 감싼 코드의 모든 변수는 즉시실행함수의 지역변수가 됨
```javascript
(function () {
  let foo = 10;
  // ...
}());

console.log(foo);  // ReferenceError: foo is not defined
```

### require
#### 우리에게 익숙한 코드 한줄
```javascript
const express = require('express');
```
#### 생김새
```javascript
require('/경로/파일명')
// 1. 위와 같이 경로/파일명으로 찾음
// 2. 경로만 표기하면 해당 경로에서 index.js 파일을 찾음
// 3. '/'가 없는 경우는 node_modules에서 찾음
```
#### 기능
> '/경로/파일명'에 해당하는 파일을 실행
```javascript
// some.js
console.log("ok");
```
```javascript
// index.js
require("./some");  // 콘솔에 ok 출력됨
```
#### 그대로 전달하려면...?
> some.js 파일에서 module.exports 에 객체를 담을 수 있음    
> index.js 파일에서는 변수에 저장해서 사용 가능 
```javascript
// some.js
const log = () => console.log("ok");
module.exports = log;
```
```javascript
// index.js
const logFromSome = require("./some");  
logFromSome();  // ok
```
#### require 작동 해부
```javascript
(function (exports, require, module, __filename, __dirname) {
  const log = function () {
    console.log("ok");
  };
  module.exports = log
} (module.exports, require, module, filename, dirname));
return module.exports;
```

### import
#### ES6(ES2015), TypeScript 에서 사용
> require는 CommonJS 형식
```javascript
// const express = require('express');
import express from "express";
```
