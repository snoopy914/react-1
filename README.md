# 201930413 박찬우
## 5주차 250403
8. 이벤트에 응답하기
- component 내부에 event handler 함수를 선언하면 event에 응답할 수 있습니다.
- onClick={handleClick]

9. 화면 업데이트하기
- comonet가 특정 정보를 "기억"해 두었다가 표시하기를 원하는 경우가 있습니다.
- 예를 들어 버튼이 클릭된 횟수를 세고 싶을 수 있습니다.
- 이렇게 하려면 componet에 state를 추가하면 됩니다.

- 먼저, React에서 useState를 import합니다.
- 이 코드를 보면 useState는 reat 파일 안에 Named Exports로 선언되어 있는 여러개의 componet 중 하나는 것을 알 수 있습니다.
- 이제 componet 내부에 state 변수를 선언할 수 있습니다.

import { useState} from 'react';

function MyButton() {
const [count,setCount] = useState(0);

- useState로부터 현재의 state를 저장할 수 있는 변수인 count와 이를 업데이트할 수 있는ㄴ 함수인 setCount를 얻ㅇ르 수 있습니다.
이름은 자유롭게 지정할 수 있지만 [something, setSomething]으로 작성하는 것이 일반적이다.
즉, 변수 일므과 변수 일므 앞에 set을 붙인 업데이트 함수를 관용적을 사용합니다.

[실습]
-버튼이 처음 표시될 떄는 useState()에 0을 전달했기 때문에 count가 0이 됩니다.
- state를 변경하고 싶다면 setCount()를 실행하고 새 값을 전달하세요.
이 버튼을 클릭하면 카운터가 증가합니다.

📘 9. 화면 업데이트하기
[실습]

버튼이 처음 표시될 때는 useState(0)을 전달해서 count가 0이 되도록 합니다.

state를 변경하고 싶다면 setCount()를 실행하고 새 값을 전달 합니다.

버튼에서 event handler를 호출하여 setCount() 함수를 실행합니다.

이제 버튼을 클릭하면 카운터가 증가합니다.

⚠ 문서의 코드는 component 안에 2개의 버튼을 반환하도록 하였으나 불필요하게 복잡합니다.

💡 우리는 useState에 집중할 수 있게 버튼 하나만 반환하도록 수정하겠습니다.

이번 실습은 CountState라는 이름의 component를 만들어서 사용하겠습니다.

CountState.js 파일을 만들고 예제의 코드를 작성해 넣습니다.

🔟 Hook 사용하기
use로 시작하는 함수를 Hook이라고 합니다.

useState는 React에서 제공하는 내장 Hook입니다.

다른 내장 Hook은 API 참고서에서 찾아볼 수 있습니다.

또한 기존의 것들을 조합하여 자신만의 Hook을 작성할 수도 있습니다. → 사용자 Hook

Hook은 다른 함수보다 더 제한적입니다.

예를 들면...

component 또는 다른 Hook의 상단에서만 Hook을 호출할 수 있습니다.

조건이나 반복문에서 useState를 사용하고 싶다면 새 컴포넌트로 추출하여 그곳에 넣으세요.

default는 이름을 바꿀 수 있다.

#Hooks의 사용 규칙(Rules of Hooks)
Hook은 React의 랜더링 및 상태 관리 메커니즘과 밀접하게 연결되어 있으며, 아래 같은 규칙을 따라야 한다.
1. 최상위에서만 호출해야한다.
- if, for, while 등의 블록 내부에서 Hooks를 호출하면 안 됩니다.
- 함수의 조건문 내부에서 호출하면 실행 순서가 달라질 수 있따.
2. REact 함수형 componet 또는 사용자 hook 내부에서만 사용 가능
- 일반적인 javaSccript 함수에서 sueState, useEffect 등의 hook을 사용할 수 없다.

# hooks의 사용 규칙(rules of hooks)
왜 이런 제한이 필요한가?
: react의 동작을 예측 가능하고 ,안정성을 높이기 위해 필요한 규칙이빈다.

1. rendering 순서를 보장하기 위해
조건문이나 반복문 안에서 hooks를 사용하면 매 rendering마다 hook의 호출 순서가 달라질 수 있기 떄무에 react가 상태를 제대로 추적할 수 없습니다.

2. 불필요한 사이드 이펙트 방지
componet가 여러 번 rendering될 떄마다 동일한 순서로 hook이 실행되어야 react가 의도한 동작을 실행할 수 있습니다.

🔎 왜 function형 컴포넌트에서만 Hook을 사용할까?
Class형 component는 lifecycle 함수를 통해서 상태 관리를 했습니다.

그런 이유 때문에 Class형 component는 유지보수가 어렵고 복잡해질 수 있었습니다.

React는 component의 상태 관리(lifecycle)와 로직을 더 간결하게 만들기 위해
Hooks를 도입하게 됩니다.

따라서 React 팀은 function형 component를 권장하고 있습니다.

Hook은 function형 component 전용으로 설계되었습니다.

⚠️ 결론
이런 이유 때문에 function형 component에서만 Hook을 사용하는 것입니다.

🔍 function component vs class component
💬 왜 요즘은 함수형 컴포넌트를 주로 사용할까?
인터넷 자료를 보면 예전엔 class형 컴포넌트가 많이 사용됨

이유는 React의 역사와 기능 제한 때문

🕰️ 1. React 초창기 (2013.05.29 ~ 2014년)
함수형 컴포넌트는 존재했지만
➤ 단순히 props를 받아 UI만 반환하는 역할만 가능

state나 lifecycle 기능 없음

따라서 중요한 컴포넌트는 class형으로만 작성됨

⚡ 2. React 16.8 (2019년 2월) → Hooks 도입
useState, useEffect 같은 Hook 등장 ➤ 함수형 컴포넌트에서도 상태 관리, 생명주기 처리 가능해짐

이후 React 공식 문서도 함수형 컴포넌트 + Hook 사용을 권장

🔔 요약
초기에는 기능 제한으로 class형이 중심이었지만,
Hook의 등장 이후 함수형이 더 강력하고 단순해져서 표준이 됨.

📘 function component vs class component (계속)
3. React 17 (2020년 10월) 이후
React 17은 주로 내부 개선 중심 업데이트였지만,

이 시기부터 function형 component + Hooks 사용이 사실상 표준이 됨.

4. React 18 (2022년 3월)
자동 배치 (Automatic Batching)
→ 여러 상태 업데이트를 묶어서 한 번에 처리
→ function형 컴포넌트에서 성능 최적화가 더 쉬워짐

.useTransition, .useDeferredValue 같은 새로운 Hook 추가됨
→ 비동기 렌더링 최적화 등 고급 기능 제공

이 변화로 인해 class component → function component 전환이 더 빨라짐

11. componet 간 데이터 고유



## 3주차 250320
오늘 배운 내용 :

## 2주차 250313
오늘 배운 내용 :
git 사용법 npx create-react-app react-1 경로가 자꾸 꼬여서 힘들었다.
`npm start`
`npm test`
`git pull`
`git push orgin main`

