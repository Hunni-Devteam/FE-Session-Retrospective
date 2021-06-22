# Block Scope

자바스크립트가 기본적으로 함수 단위로 실행 환경을 수집 (실행 컨텍스트를 만들...텐데)할텐데?
그럼 JS 엔진에 block scope 구현이 추가된건가?

아니면 익명 함수로 감싸서 그냥 함수 컨텍스트를 하나 더 만들어준건가?
동작은 같을 것 같고 컴파일러 최적화할 게 아니라면 ... 그냥 함수 스코프를 하나 만드는 것도 딱히 이상한 방법은 아닐 것 같습니다.


## 예시:


```js
var a = 0;

// using var - 함수 컨텍스트 생성 시 var 선언이 미리 수집되므로 
for (var a = 0; a < 20; a++) {
  // for문은 함수 스코프(위의)의 a를 갱신하고 로그 출력
  console.log(a);
}

// using let - for 블록 스코프 생성되므로 전역 컨텍스트의 a를 덮어씌우지 않음
for (let a = 0; a < 20; a++ {
  // 마찬가지로 블록 스코프의 a를 갱신하고 로그 출력. 외부 스코프 값은 그대로임.
  console.log(a);  
}

// 블록 스코프는 어떻게 구현되었는가? 사실 익명 함수 스코프를 생성하는 걸로도 해결할 수 있지 않나..?
// 구세대 엔진으로 transpile 할 때는 (구버전 브라우저라거나..IE9이나..그런거..) 함수 스코프 생성밖에 답이 없을 것 같은 ...

// 익명 함수 스코프 생성
(function() {
  // 독립적인 실행 환경 (콜스택에 함수가 하나 더쌓임)
  for (var a = 0; a < 20; a++) {
    console.log(a);
  }
})();

```