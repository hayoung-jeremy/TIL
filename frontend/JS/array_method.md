## 배열 생성

### Array.from()

`Array.from(arrayLike, [, mapFn[, thisArg]])`

유사 배열, 또는 반복 가능 객체로부터 새 Array instance 를 생성한다.

```javascript
const createArray = (args) => {
  let arrayInstance = Array.from(args);
  console.log(arrayInstance);
};

createArray(1, 2, 3); // [1,2,3]
createArray("foo"); // ["f","o","o"]
```

### Array.isAray()

배열 여부 확인 — 인자로 전달받은 객체가 배열이면 true, 아니면 false 를 반환한다.

```javascript
Array.isArray([1, 2, 3]); // true
Array.isArray({ foo: 123 }); // false
Array.isArray("foobar"); // false
```

## 원본 배열 수정

### pop()

배열의 뒷 부분을 삭제한다.

```javascript
let arr = [1, 2, 3, 4];
arr.pop();
console.log(arr); // [1,2,3]
```

### push()

배열의 뒷 부분에 값을 삽입한다.

```javascript
let arr = [1, 2, 3, 4];
arr.push(5);
console.log(arr); // [1,2,3,4,5]
```

### shift()

배열의 앞 부분을 삭제한다.

```javascript
let arr = [1, 2, 3, 4];
arr.shift();
console.log(arr); // [2,3,4]
```

### unshift()

배열의 앞 부분에 값을 삽입한다.

```javascript
let arr = [1, 2, 3, 4];
arr.unshift(0);
console.log(arr); // [0,1,2,3,4]
```

### splice()

`splice(startIndex, deleteCount, items)`

배열의 특정 위치에 요소를 추가하거나 삭제한다.

startIndex 부터 deleteCount 만큼 삭제하고, items 를 그 위치에 추가 (원본 배열 수정)

```javascript
let arr = [1, 2, 3, 4];
arr.splice(1); // deleteCount 를 생략하면, startIndex 를 포함하여, 뒤의 모든 요소를 삭제
console.log(arr); // [1]

let arr2 = [1, 2, 3, 4, 5];
arr2.splice(2, 1); // 2번째 인덱스부터 요소를 하나 삭제 (즉 2번째 인덱스 자신이 삭제됨)
console.log(arr2); // [1,2,4,5]

let arr3 = [1, 2, 5, 6];
arr3.splice(2, 0, 3, 4); // 아무것도 제거하지않고 2번째 인덱스부터 3, 4 를 추가
console.log(arr3); // [1,2,3,4,5,6]
```

### reverse()

배열요소의 순서를 뒤집는다.

```javascript
let arr = [1, 2, 3, 4];
arr.reverse();
console.log(arr); // [4,3,2,1]
```

### sort()

`sort([compareFn])`

배열요소를 문자열로 변경후, 유니코드 코드 포인트에 따라 정렬한다.

```javascript
let arr = [1, 3, 2, 4];
arr.sort();
console.log(arr); // [1,2,3,4]

let arr2 = ["Mon", "Tue", "Wed", "Thur"];
arr2.sort();
console.log(arr2); // ["Mon", "Thur", "Tue", "Wed"];

let arr3 = [1, 9, 40, 70];
arr3.sort(); // 문자열로 변경된 후 정렬하기 때문에, '7'이있는 70이 '9' 보다 앞에온다.
console.log(arr3); // [1,40,70,9]

// 비교 정렬
arr3.sort(function (a, b) {
  return a - b;
});
console.log(arr3); // [1,9,40,70]
```

### fill()

`fill(value, startIndex, endIndex)`

배열의 startIndex 부터 endIndex 까지 정적 값으로 채운다. startIndex 기본값은 0, endIndex 기본값은 배열의 length 이다.

```javascript
const arr = Array(3); // length 가 3 인 빈 배열을 생성,
arr.fill(2); // 정적값 2로 빈 배열 arr 을 채운다 -> [2,2,2]
```

## 원본 배열 수정하지 않음

### concat()

배열들을 합쳐서 병합된 새로운 배열을 반환한다.

```javascript
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let arr3 = arr1.concat(arr2);
console.log(arr3); // [1,2,3,4,5,6]
```

### join()

배열안의 요소들을 하나의 문자열로 합쳐서 반환한다.

```javascript
let arr = [1, 2, 3];
arr.join(); // 1,2,3,4
arr.join("-"); // 1-2-3-4
```

### slice()

`slice(start, end)`

배열의 start부터 end까지(end 요소 제외) shallow copy하여 새로운 배열을 반환한다. (원본 배열 수정되지 않음)

```javascript
let arr = [1, 2, 3, 4, 5, 6, 7, 8];
arr.slice(undefined, 3); // start 가 undefined 면, 0 번째부터 slice 한다.
console.log(arr); // [1,2,3]

let arr2 = [1, 2, 3, 4, 5, 6];
arr2.slice(-2); // start 가 음수일 경우, 배열의 끝에서부터의 순서를 추출한다.
console.log(arr2); // [5,6]
```

## 배열 검색

### indexOf(), lastIndexOf()

`indexOf(value, startIndex)`

배열 중에 value 로 지정한 값이 존재하는지 찾는데, startIndex 를 지정하면 해당 인덱스부터 찾아서, 존재하는 값의 인덱스를 반환, 없을 경우 -1 을 반환한다. lastIndexOf 는 뒤에서부터 찾는다.

```javascript
// indexOf 일치하는 첫번째 요소 인덱스 반환
arr.indexOf(value, start);
arr.lastIndexOf(value, start);
// value - 찾는 요소, start - 시작 인덱스

let arr = [1, 5, "a", o, true, 5, [1, 2], "9"];

arr.indexOf(5); // 1
arr.lastIndexOf(5); // 5
arr.indexOf(5, 5); // 5
arr.indexOf(true, 5); // -1
```

### some(), every()

인자로 주어지는 함수로 판단하여,

`some()` → 배열의 요소 중 조건에 충족하는 값이 하나라도 있다면 true, 아니면 false

`every()` → 배열의 모든 요소가 조건에 충족할 경우에만 true, 아니면 false

```javascript
const arr = [2, 4, 6, 8];
arr.every((el) => el % 2 === 0); // true
arr.some((el) => el % 2); // true
```

### includes()

인자로 주어지는 값이 존재하면 true 를, 없다면 false 를 반환한다.

```javascript
arr.includes(searchElement);
// 배열에 특정 요소가 포함되어 있는지 여부를 확인하여 true/false 를 리턴.

let a = [1, 2, 3];
a.includes(2); // true
a.includes(4); // false
```

## 배열 조작

### map()

`map(function(value, index, array){})`

인자로 전달한 함수를 배열에 모두 한번씩 실행하여, 함수의 결과값으로 새로운 배열을 만들어 반환한다.

```javascript
let friends = ["Jeremy", "Hayoung", "Haram"];
const lovelyFriends = friends.map((items) => items + " ♥");

console.log(friends); // ["Jeremy", "Hayoung", "Haram"] 원본 배열은 변하지 않음
console.log(lovelyFriends); // [Jeremy ♥", "Hayoung ♥", "Haram ♥"]
```

### forEach()

배열 순회 — `map()` 과는 다르게, 인자로 전달한 함수를 배열의 요소에 모두 한번씩 실행하지만, 새로운 배열을 반환하지는 않는다. 단지 실행할 뿐이다.

```javascript
const arr = [1, 2, 3];
arr.forEach((el) => console.log(el));
// 1
// 2
// 3
```

### filter()

인자로 전달한 함수의 조건에 만족하는 요소들만 모아 새로운 배열을 만들어 반환한다.

```javascript
let tasks = [
  { item: "Buy Milk", completed: false },
  { item: "Go hospital", completed: true },
];

let uncompletedTasks = tasks.filter(function (task) {
  return !task.completed;
}); // [{item: "Buy Milk", completed: false}]
```

### reduce()

인자로 전달한 함수를 이용하여, 배열의 각 요소들을 순회하면서 모든 요소들을 합성한다.

```javascript
arr.reduce(function (acc, item, index, array) {}, init);
// acc - 누적값
// item - 각 요소
// index - 인덱스
// array - 배열자신
// init - 누적값의 초깃값

// ex) 배열의 숫자를 더하기
var arr = [5, 7, 2, 4];

var sum = arr.reduce(function (a, x) {
  return (a += x);
});

var sum = arr.reduce(function (a, x) {
  return (a += x);
}, 0); // 18 (5+7+2+4)
```

### references

- [JS Array 이해, push(), pop(), sort(), splice()
  ](https://tutorialpost.apptilus.com/code/posts/js/js-array/)

- [[ javascript ] Array method 정리](http://blog.302chanwoo.com/2017/08/javascript-array-method/)

- [JavaScript 배열 메소드 (Array method)](https://takeu.tistory.com/25)

- [Array.prototype.sort() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

- [Array.prototype.splice() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
