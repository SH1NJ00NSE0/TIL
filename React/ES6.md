# 리액트를 위한 ES6문법

> 앞으로의 프레임워크 공부를 위해 이전 버전의 문법보다<br>
ES6의 문법을 익히는 것이 중요할 것 같아 정리해보았읍니다...

<br>

## let, const
ES6이전에 변수 선언에 사용된 `var`이외에도 `let`과 `const`가 추가되었습니다.<br>
이전 버전에서 `var`의 가장 큰 문제는 변수의 재선언이 가능했다는 점이었습니다.<br>
이를 보완하기 위해 `let`과 `const`는 **변수의 재선언이 불가능**하도록 되어있습니다.<br>
특히 `const`는 상수를 의미하는 변수를 선언하기 때문에 재할당이 불가능합니다.

```js
var test1 = [1,2,3,4,5]; // undefined === pass
var test1 = [6,7,8,9,0]; // undefined === pass

let test2 = [1,2,3,4,5]; // undefined === pass
let test2 = [6,7,8,9,0]; // SyntaxError!
test2 = 'foo' // 가능

const test3 = 3; // undefined === pass
const test3 = 13; // SyntaxError!
test3 = 'bar' // 불가능

/*
현재 버전의 크롬 개발자도구 콘솔 상에서는 let의 변수 재선언이 적용됩니다.
하지만 eslint 를 적용한 vscode 에서는 기본적으로 이를 에러라고 인식하고 잡아냅니다. 

그게 아니더라도, 다른 목적을 위한 변수 재선언 사용은 좋지 않은 코딩 스타일 중 하나입니다.
*/
```
또한, `var`는 함수 범위의 scope를 가지고,<br>
`let`과 `const`는 블록 단위의 scope를 가집니다.

<br>

## 변수 선언 시 축약코딩
```js
// 이전 버전
let x;
let y = 0;
let z = 1;

//ES6
let = x, y = 0, z = 1;
```
여러개의 변수 선언 시 일일이 let, const를 입력하지 않아도 위와 같이 한줄로 축약가능합니다.

<br>

## Spread Operator (전개연산자) & Rest Parameters (나머지 매개변수)
**전개연산자**와 **나머지 매개변수**는 `...`을 통해 사용할 수 있습니다.<br>
`...`를 통해 전개연산자를 사용하면 
**반복 가능한 객체 arr이 인수 리스트로 확장됩니다.**<br>

```js
let arr = [3, 5, 1];

console.log(arr) //[3, 5, 1]
console.log(...arr) //3, 5, 1

alert( Math.max(arr) ); // NaN
alert( Math.max(...arr) ); // 5 (전개 연산자가 배열을 인수 리스트로 바꿔주었습니다.)
```
<br>
`...`뒤에 배열 이름을 적어준 뒤 함수 선언부의 매개변수 자리에 넣어주면<br>
나머지 매개변수들을 배열에 넣어줄 수 있습니다.<br>
이 때, 나머지 매개변수는 항상 마지막에 있어야 합니다.

<br>

```js
function showName(firstName, lastName, ...titles) {
  alert( firstName + ' ' + lastName ); // Julius Caesar

  // 나머지 인수들은 배열 titles에 할당됩니다.
  // titles = ["Consul", "Imperator"]
  alert( titles[0] ); // Consul
  alert( titles[1] ); // Imperator
  alert( titles.length ); // 2
}

showName("Julius", "Caesar", "Consul", "Imperator");
```
<br>

## Destructuring assignment (비구조화 할당)
객체의 속성들을 개별적인 변수에 담을 수 있는 선언방식입니다.<br>
범위를 벗어나거나 할당되지 않은 나머지 값이 있다면 자동적으로 undefined가 선언됩니다.
```js
//이전 버전 
let array = [1, 2, 3];
let x = array[0];
let y = array[1];
let z = array[2];

//ES6 배열 구조 분해
let array = [1, 2, 3];
let [x, y, z] = array;
console.log(x,y,z); // 1 2 3

//이전 버전
let object = {name : 'Aiden', job : 'coding', age : 20};
let name = object.name;
let job = object.job;
let age = object.age;

//ES6 객체 구조 분해
let {name, job, age} = {name : 'Aiden', job : 'coding', age : 20};
console.log(name, job, age) // Aiden coding 20
```
<br>

## template literals
ES6에서 도입된 template literals라는 문자열 표기법은 <br>
백틱( ` )을 활용하여 더욱 활용성이 높은 문자열 활용을 가능하게 합니다.
```js
let first = `John`
let last = `Piper`

//이전버전
console.log(`My name is ` + first + ' ' + last + '.'); // My name is John Piper.

//String Interpolation (문자열 보간)
console.log(`My name is ${first} ${last}.`) // My name is John Piper.


//String Interpolation은 ${변수명} 식으로 활용합니다.
//String Interpolation의 표현식 안에 변수명이 들어가면 변수의 값이 문자열로 강제 형변환됩니다.
//String Interpolation의 표현식 안에서 간단한 연산도 가능합니다.

let num =4
console.log (`4*2 = ${num*2}`); // 4*2 = 8
```