# useState

## 변수 말고 useState쓰는 이유
state가 변경될 때 자동으로 그 state와 관련된 **DOM을 재렌더링**되게 해야합니다.<br>
따라서 변수가 아닌 `useState`를 사용하는 것입니다.<br>	
SPA(SinglePageApplication)로 웹 개발을 할려면 state를 사용해야한다는 것입니다.

<br>

## 사용법

```js
import { useState } from 'react';
```
우선 `useState`를 사용하기 위해선 `useState`를 임포트 해주어야합니다.
```js
const ["state명", "state변경함수명"] = useState("초기값");
```
보통 state변경함수는 state명 앞에 set을 붙여서 작명하는 것이 국룰<br>


state 선언 시 `const`를 사용하는 이유는 state를 직접 수정하는 것을
방지하고, <br>`setState`를 사용하도록 하기 위함입니다.