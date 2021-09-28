# String (문자열) 다루기

### 문자의 길이

`length`

문자의 길이를 저장하는 프로퍼티이며 함수가 아니다.

```javascript
const str = "Hello";
console.log(str.length); // "5"
```

### 대·소문자 변경

`toLowerCase()` , `toUpperCase()`

### 부분 문자열 변경

1. `slice(start [, end])`

   - 문자열의 `start` 부터 `end` 까지(`end` 는 미포함) 추출하여 반환
   - `end` 를 생략시 문자열 끝까지 반환
   - `start` 와 `end` 를 음수로 지정 가능

     ```javascript
     let str = "stringify";
     console.log(str.slice(0, 5)); // 'strin', 0번째부터 5번째 위치까지(5번째 위치의 글자는 포함하지 않음)
     console.log(str.slice(-4, -1)); // `gif` 끝에서 4번째부터 시작해서 끝에서 1번째 위치까지
     ```

2. `subString(start [, end])`

   - `slice` 와 매우 유사, `start` 가 `end` 보다 클 수 있음
   - 음수 사용 불가, 0 으로 처리됨

     ```javascript
     let str = "stringify";

     // 동일한 부분 문자열을 반환
     console.log(str.substring(2, 6)); // "ring"
     console.log(str.substring(6, 2)); // "ring"

     // slice를 사용하면 결과가 다름
     console.log(str.slice(2, 6)); // "ring" (같음)
     console.log(str.slice(6, 2)); // "" (빈 문자열)
     ```

3. `substr(start [, length])`

   - `start` 에서 시작하여 `length` 개의 글자 반환

     ```javascript
     let str = "stringify";

     console.log(str.substr(2, 4)); // "ring", 두 번째부터 글자 네 개
     ```

### references

- [문자열](https://ko.javascript.info/string)
