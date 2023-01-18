# 타입 시스템

<br>

## 1. 타입의 종류
타입은 자바스크립트에서 다루는 값의 **형태**라고 할 수 있습니다.<br>
Just like typeof...

타입의 종류에는 우선 7가지의 원시타입이 있습니다.
### 타입의 종류
- `null`
- `undefined`
- `boolean`
- `string`
- `number`
- `bigint`
- `symbol`

<br>

## 2. 타입 시스템

### 타입 시스템의 작동 순서
1. 코드를 읽고 존재하는 모든 타입과 값을 이해합니다.
2. 각 값이 초기 선언에서 가질 수 있는 타입을 확인합니다.
3. 각 값이 추후 코드에서 어떻게 사용될 수 있는지 모든 방법을 확인합니다.
4. 값의 사용법이 타입과 일치하지 않으면 사용자에게 오류를 표시합니다.

<br>

ex)
```js
let fisrtName = "Whitney";
firstName.length();
//        ~~~~~~
// Error: This expression is not callable.
//    Type 'Number' has no call signatures
```
이 스크립트에서 TS는 다음과 같은 순서로 오류를 표시합니다.
1. 코드를 읽고 `firstName`이라는 변수를 이해합니다.
2. 초깃값이 "Whitney"이므로 `firstName`이 string 타입이라고 결론짓습니다.
3. `firstName`의 `.length` 멤버를 함수처럼 호출하는 코드를 확인합니다.
4. string의 `.length` 멤버는 함수가 아닌 숫자라는 오류를 표시합니다.<br>
**즉, 함수처럼 호출할 수 없습니다.**

<br>

### 오류 종류
- **구문오류** : 타입스크립트가 자바스크립트로 변환되는 것을 차단한 경우
- **타입오류** : 타입 검사기에 따라 일치하지 않는 것이 감지된 경우
