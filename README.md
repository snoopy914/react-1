
# 201930413 박찬우
### 11주차

✅ Step 3: 최소한의 데이터만 이용해서 완벽하게 UI State 표현하기
🔹 핵심 요점 정리:
UI는 상호작용 가능해야 하며, 이를 위해 사용자가 데이터를 변경할 수 있어야 합니다.

React는 state를 통해 데이터를 변경할 수 있는 구조를 제공합니다.

state란 앱이 기억해야 하고, 변경 가능한 데이터의 최소 집합으로 간주해야 합니다.

가장 중요한 원칙은 DRY(Don’t Repeat Yourself): 중복된 state를 피해야 합니다.

앱이 필요로 하는 최소한의 state만 정의하고, 나머지는 실시간 계산하세요.

🔸 예시:
쇼핑 리스트를 만든다면, 상품 아이템 배열만 state로 관리합니다.

상품 개수를 표시하고 싶다면, 별도의 state를 만들지 말고 array.length를 실시간 계산하세요.

💡 요약 정리:
state는 꼭 필요한 최소한만!

중복 금지 (DRY 원칙)

계산 가능한 값은 state로 저장하지 말고 계산해서 쓰기

✅ Step 3: 최소한의 데이터만 이용해서 완벽하게 UI State 표현하기
🔹 핵심 요점 정리:
UI는 상호작용 가능해야 하며, 이를 위해 사용자가 데이터를 변경할 수 있어야 합니다.

React는 state를 통해 데이터를 변경할 수 있는 구조를 제공합니다.

state란 앱이 기억해야 하고, 변경 가능한 데이터의 최소 집합으로 간주해야 합니다.

가장 중요한 원칙은 DRY(Don’t Repeat Yourself): 중복된 state를 피해야 합니다.

앱이 필요로 하는 최소한의 state만 정의하고, 나머지는 실시간 계산하세요.

🔸 예시:
쇼핑 리스트를 만든다면, 상품 아이템 배열만 state로 관리합니다.

상품 개수를 표시하고 싶다면, 별도의 state를 만들지 말고 array.length를 실시간 계산하세요.

💡 요약 정리:
state는 꼭 필요한 최소한만!

중복 금지 (DRY 원칙)

계산 가능한 값은 state로 저장하지 말고 계산해서 쓰기

✅ Step 4: State가 어디에 있어야 할 지 정하기
🔹 핵심 원칙:
공통 부모 컴포넌트에 두는 것이 기본
→ 여러 컴포넌트에서 공통으로 사용하는 state라면 공통 부모에 두면 됩니다.

공통 부모보다 상위 컴포넌트에 둘 수도 있음
→ 상황에 따라 더 높은 곳으로 올릴 수 있습니다.

적절한 컴포넌트를 찾기 어렵다면, state를 위한 전용 컴포넌트를 만들고 상위 계층에 추가
→ 너무 하위에서 꼬이지 말고 state를 담당할 컴포넌트를 따로 만들어서 배치하는 방식도 OK.

🔸 실전 적용 예시:
예시 앱에서 발견한 두 state는:

“사용자의 검색어 입력”

“체크박스의 값”
이 두 state는 항상 함께 나타나므로, 같은 위치에 두는 것이 합리적입니다.

💡 요약 정리:
여러 컴포넌트가 함께 쓰는 state → 공통 부모에

함께 갱신되거나 항상 함께 나타나는 state → 같은 위치에

적절한 소유 컴포넌트가 없다면 → 상위에 전용 컴포넌트 만들어 관리



### 10주차
React로 사고하기
React를 사용하게 되면 우리가 고려하고 있는 디자인이나 만들 앱들에 대한 생각을 바꿀 수 있습니다.

React로 사용자 인터페이스를 빌드할 때, 먼저 이를 컴포넌트라는 조각으로 나눕니다.

그리고 각 컴포넌트의 다양한 시각적 상태들을 정의합니다.

마지막으로 컴포넌트들을 연결하여 데이터가 그 사이를 흘러가게 합니다.

이 자습서에서는 React로 검색할 수 있는 상품 테이블을 만드는 과정을 체계적으로 안내해 드리겠습니다.

# React는 component 기반으로 개발합니다.
이 장을 통해서 component의 조각들이 어떻게 App으로 완성되는지 다시 한번 확인해 보세요.

Step 1: UI를 컴포넌트 계층으로 쪼개기
먼저 모의 시안에 있는 모든 컴포넌트와 하위 컴포넌트 주변에 박스를 그리고, 그들에게 이름을 붙이면서 시작해 보세요.

디자이너와 함께 일한다면 그들이 이미 디자인 툴을 통하여 이 컴포넌트들에 이름을 정해 두었을 수도 있습니다. 한번 여쭤보세요!

어떤 배경을 가지고 있느냐에 따라, 디자인을 컴포넌트로 나누는 방법에 대한 관점이 달라질 수 있습니다.

Programming: 새로운 함수나 객체를 만드는 방식과 같은 방법으로 해봅시다.

이 중 단일책임 원칙을 반영하고자 한다면 컴포넌트는 이상적으로는 한 번에 한 가지 일만 해야 합니다.

만약 컴포넌트가 점점 커진다면 작은 하위 컴포넌트로 쪼개줘야 하겠죠.

CSS: 클래스를 선택자를 모으므로 만들지 생각해 봅시다. (실제 컴포넌트들은 약간 좀 더 세분되어 있습니다.)

Step 1: UI를 컴포넌트 계층으로 쪼개기
JSON이 잘 구조화 되어 있다면, 종종 이것이 UI의 컴포넌트 구조가 자연스럽게 데이터 모델에 대응된다는 것을 발견할 수 있습니다.

이는 UI와 데이터 모델은 보통 같은 정보 아키텍처, 즉 같은 구조를 가지기 때문입니다.

UI를 컴포넌트로 분리하고, 각 컴포넌트가 데이터 모델에 매칭될 수 있도록 하세요.

여기 다섯 개의 컴포넌트가 있습니다.

### 7주차 보강
🔹 한 번 더 state 끌어올리기 – 핵심 요약
Game 컴포넌트를 새로 만들고 export default로 지정

Game 안에서 Board 컴포넌트를 렌더링

한 파일엔 export default가 하나만 있어야 하므로 Board에서는 제거

index.js에서 최상위 컴포넌트로 Game을 사용하도록 지정

Game 컴포넌트에 div를 추가하여 추후 게임 정보 공간 확보

⚠️ 주의사항
index.js가 아니라 App에서 불러오고 있음

최상위 컴포넌트는 항상 최상단에 선언

컴포넌트 이름과 파일 이름을 일치시키면 관리에 좋음

📌 코드 예시
jsx
복사
편집
function Board() {
  // ...
}

export default function Game() {
  return (
    <div className="game">
      <div className="game-board">
        <Board />
      </div>
      <div className="game-info">
        <ol>{/*TODO*/}</ol>
      </div>
    </div>
  );
}

🔹 한 번 더 state 끌어올리기 – Part 2
✅ 6. Game 컴포넌트에 state 추가
xIsNext : 다음 차례가 누구인지 (true면 X, false면 O)

history : 각 턴의 squares 상태를 기록하는 배열

jsx
복사
편집
const [xIsNext, setXIsNext] = useState(true);
const [history, setHistory] = useState([Array(9).fill(null)]);
✅ 7. 현재 게임 상태 (squares) 얻기
history에서 마지막 값을 꺼내 currentSquares로 사용

렌더링 시 현재 상태만 필요하므로, 마지막 요소만 참조

jsx
복사
편집
const currentSquares = history[history.length - 1];
✅ 8. 계산만으로도 가능한 정보는 useState 불필요
currentSquares는 history에서 계산할 수 있으므로 따로 state로 관리하지 않아도 됨
🔹 한 번 더 state 끌어올리기 – Part 3
✅ 11. Board에 필요한 정보는 모두 props로 전달
Board 컴포넌트는 다음 3가지 props를 받도록 수정:

xIsNext (누구 차례인지)

squares (현재 게임 상태)

onPlay (클릭 시 실행할 함수)

✅ onPlay는 클릭된 후 업데이트된 squares를 Game으로 전달하기 위한 함수

✅ 12. Board 내부에서 useState 제거
상태는 Game에서 관리하므로, Board에서는 상태 정의(useState) 삭제

js
복사
편집
function Board({ xIsNext, squares, onPlay }) {
  function handleClick(i) {
    // ...
  }
}
✅ 13. 클릭 시 처리 로직 변경
setSquares, setXIsNext 등 직접 상태 변경 로직은 제거하고,

onPlay(nextSquares)로 Game에 알리도록 처리

js
복사
편집
if (xIsNext) {
  nextSquares[i] = "X";
} else {
  nextSquares[i] = "O";
}
onPlay(nextSquares);
📌 핵심 요약

상태 관리는 전부 Game 컴포넌트에서

Board는 props로만 상태를 받아 렌더링
🔹 과거 움직임 보여주기 – 핵심 요약
✅ 기본 개념
이제 history 배열을 이용해서 과거 플레이 기록을 보여줄 수 있음

<button>과 같은 엘리먼트는 일반 JS 객체 → 이를 React 엘리먼트 배열로 변환 필요

✅ React에서 다수 엘리먼트 렌더링 방법
배열을 map()으로 돌려서 React 엘리먼트로 변환
예시:

js
복사
편집
[1, 2, 3].map((x) => x * 2); // 결과: [2, 4, 6]
🛠 구현을 위한 Step-by-Step 요약
history 배열의 각 항목마다 버튼을 생성

React 엘리먼트 배열로 만들어 렌더링

각 버튼은 과거 특정 턴으로 '점프'하는 기능 수행

Game 컴포넌트에서 history.map()을 사용하여 구현

즉, map()을 활용해 아래와 같은 구조로 만들게 될 거야:

jsx
복사
편집
const moves = history.map((squares, move) => {
  const description = move ? `Go to move #${move}` : 'Go to game start';
  return (
    <li key={move}>
      <button onClick={() => jumpTo(move)}>{description}</button>
    </li>
  );
});

Step 1: UI를 컴포넌트 계층으로 쪼개기
FilterableProductTable (회색)

예시 전체를 포함하는 최상위 컴포넌트입니다.

SearchBar (파란색)

사용자의 입력을 받는 입력창입니다.

ProductTable (라벤더색)

데이터를 리스트 형태로 보여주고, 사용자 입력(SearchBar)을 기반으로 필터링합니다.

ProductCategoryRow (초록색)

각 카테고리의 헤더(예: Fruits, Vegetables)를 보여줍니다.

ProductRow (노란색)

각 개별 제품 항목을 보여주는 행(예: Apple, Pumpkin 등)입니다.

### 7주차 250417

animals.slice(2) -> end point가 없다.
마지막으로 보드 컴포넌트 내부에 handleClick 함수를 정의하여, 보드의 state를 담고 있는 squares 배열로 만드시오
State 포인팅하기 - 3

다음으로 handleClick()이 저장해야 합니다.

Square의 onSquareClick prop에 아까 같이 JSX에서 직접 handleClick()으로 설정할 수도 있지
만, 이 방법은 작동하지 않습니다.

<Square value={squares[i]} onSquareClick={handleClick(i)} />

이 이유는 다음과 같습니다.

handleClick() 호출은 Board 컴포넌트 렌더링의 일부가 됩니다.

handleClick()은 setSquares를 호출하며, Board 컴포넌트의 state를 변경하기 때문에 Board 컴포넌트 자체가 다시 렌더링 됩니다.

하지만 이 과정에서 handleClick()은 다시 실행되기 때문에 무한 루프에 빠지게 됩니다.

Too many re-renders. React limits the number of renders to prevent an infinite loop.

📌 핵심 요점 정리
문제 인식

9개의 Square 각각에 대해 함수 이름을 따로 정하는 건 비효율적이다.

해결 방안

JSX에서 화살표 함수 ( ) => handleClick(0)을 사용해 간단하게 처리.

jsx
복사
편집
<Square value={squares[0]} onSquareClick={() => handleClick(0)} />
화살표 함수 개념

() => handleClick(0)은 handleClick(0)을 호출하는 익명 함수를 생성하는 것.

즉, Square가 클릭되었을 때 해당 함수가 실행됨.

⚠️ 주의사항

handleClick(0)을 직접 넘기면 즉시 실행되기 때문에, 반드시 함수로 감싸서 넘겨야 클릭 시점에 실행됨.

🧠 추가 팁
만약 9개의 Square를 반복문으로 처리한다면 아래처럼 만들 수 있어요:

jsx
복사
편집
{squares.map((value, idx) => (
  <Square key={idx} value={value} onSquareClick={() => handleClick(idx)} />
))}
📌 핵심 정리
부모 컴포넌트에서 상태 관리

Board가 모든 state를 관리하며,

각 Square는 props를 통해 값을 전달받습니다.

자식 → 부모로 이벤트 전달

Square가 클릭되면 → Square 컴포넌트는 부모인 Board에게 state 업데이트 요청을 보냅니다.

자동 리렌더링

Board의 state가 변경되면,

Board 자신과 모든 자식 Square 컴포넌트가 자동으로 다시 렌더링됩니다.

일관된 상태 관리

Board가 모든 Square의 상태를 통합해서 관리하므로,

게임의 승자 판별 등 복잡한 로직도 부모 컴포넌트에서 쉽게 처리할 수 있습니다.

🧠 쉬운 비유
Square는 버튼처럼 단순한 입력기.

Board는 두뇌 역할로 상태를 기억하고 판단합니다.

그래서 "버튼은 누르면 끝", 판단은 "Board가" 하게 설계된 거예요.
🎯 클릭 후 상태 변화 흐름 (왼쪽 위 사각형 클릭 시)
✅ 1. Square의 클릭 이벤트 처리
Square는 onClick prop으로 전달받은 함수를 실행함.

이 함수는 Board에서 onSquareClick이라는 prop으로 전달한 함수.

이 함수 내부에서 handleClick(0)을 실행함 → 0번 인덱스 클릭

✅ 2. handleClick(0)의 역할
squares[0]을 null에서 'X'로 업데이트.

즉, 첫 번째 칸에 X를 표시하도록 state를 변경함.

✅ 3. 상태 업데이트에 따른 리렌더링
Board의 state가 변경됨 → React는 자동으로 Board와 그 자식들(Square)을 리렌더링.

이에 따라 value={squares[0]}이 'X'로 변경됨.

✅ 4. 최종 렌더 결과
왼쪽 위 사각형에는 'X'가 보이게 됨.

사용자는 클릭 → X가 나타나는 흐름을 확인.

📌 정리 요약

단계	설명
1	Square가 클릭됨 (0번 인덱스)
2	handleClick(0) 호출로 squares[0] = 'X' 업데이트
3	state 업데이트로 컴포넌트 자동 리렌더
4	Square의 value가 'X'로 변경되어 보이게 됨

🔹 불변성이 왜 중요할까요?
배열을 직접 수정하는 것 대신 slice() 등으로 새로운 배열을 만드는 방식을 권장합니다.

불변성과 불변성을 지키는 이유를 이해하는 것이 중요하다고 강조합니다.

🔹 데이터 변경 방식 2가지
직접 변경 (Mutate):

기존 데이터를 직접 수정함.

예시:

javascript
복사
편집
const squares = [null, null, ..., null];
squares[0] = 'X';
원래 배열 자체가 바뀜 → 부작용 발생 가능

복사 후 변경 (Immutable 방식):

기존 데이터를 건드리지 않고 복사본을 만들어 수정함.

예시:

javascript
복사
편집
const nextSquares = [...squares];  // 또는 slice()
nextSquares[0] = 'X';
원본은 그대로 유지 → 예측 가능성, 디버깅 용이성, React 리렌더링 최적화에 도움

🔹 결론
불변성을 유지하면 상태 변화 감지 및 리렌더링 처리가 쉬워지고, 코드의 안정성과 예측 가능성이 높아집니다.

특히 React 개발 시 핵심 개념으로 자리 잡고 있습니다.
🔹 왜 불변성이 중요한가요? (추가 이유)
결과는 같아도, 원본 데이터를 직접 변형하지 않음으로써 여러 이점을 얻을 수 있음

🔹 구체적인 이점들
복잡한 기능 구현이 쉬워짐

예: 상태 변경 이력을 저장하고, 이전 상태로 되돌리는 기능(Undo/Redo, “돌아가기” 등)

시간 여행(Time Travel) 기능이 가능해짐

게임의 진행 과정을 기록 → 이전 상태로 “되감기”

React에서 Redux DevTools도 이 원리를 활용함

특정 작업의 최소화/재실행 기능

이는 단순 게임에 국한되지 않고 일반 앱에도 자주 사용됨 (예: 메모장 Ctrl+Z)

초기화 및 재사용 용이

직접 변경을 피하면 이전 데이터를 그대로 보관할 수 있어
→ 나중에 재사용하거나 초기 상태로 쉽게 복원 가능

✅ 요약 정리
불변성을 유지하면 상태 이력 추적, 디버깅, 롤백, 리렌더링 최적화, 재사용 등 다양한 이점이 있음

특히 상태 기반 UI 프레임워크(React 등)에서는 거의 기본 철학처럼 사용됨

필요하다면 이 두 슬라이드 내용을 하나로 정리해서 학습용 요약본이나 발표 스크립트 형태로 정리해줄게!

## 6주차 250410
const [ foo, setFoo ] = useState(null)
const [ value, setValue ] = useState(null)
📌 단계별 설명
1. handleClick 함수 정의
Square 함수 내부에 클릭 이벤트를 처리할 handleClick 함수를 먼저 선언:

javascript
복사
편집
function handleClick() {
  console.log("clicked!");
}
2. JSX 버튼에 이벤트 연결
JSX에서 onClick prop을 버튼에 추가해서 클릭 이벤트 연결:

javascript
복사
편집
function Square() {
  function handleClick() {
    console.log("clicked!");
  }

  return (
    <button className="square" onClick={handleClick}>
      {/* 버튼 내용 */}
    </button>
  );
}

props를 통해 데이터 전달하기 요약
Component 재사용과 중복 제거

React의 component architecture를 활용해 재사용 가능한 component를 만들고, 중복된 코드를 제거함.

Component 구성 단계

Board component를 만들고, Square component의 내용을 복사.

Square component에서 button 하나만 남기고 나머지는 제거.

Board component의 button을 Square component로 교체.

App에서 호출하는 component를 Square에서 Board로 변경.

출력이 정상적인지 확인.

문제 인식

현재는 숫자 출력이 1만 반복됨. 즉, 각 Square가 고유 상태를 갖고 있지 않음.

문제 해결: props 도입

props를 통해 부모 component(Board)에서 자식 component(Square)로 값을 전달.

데이터를 전달하는 방향은 항상 부모 → 자식.1. 기본 개념
Square 컴포넌트가 value라는 prop을 받을 수 있도록 구조를 변경함.

javascript
복사
편집
function Square({ value }) {
  return <button className="square">1</button>;
}
현재는 value 값을 받아도 실제 버튼에는 1이 고정되어 있어 의미가 없음.

2. 문자열 vs JavaScript 변수
"value"처럼 문자열로 쓰면 그냥 글자 그대로 "value"가 출력됨.

실제 JavaScript 변수로서 value를 사용하려면 중괄호 {}를 써야 함.

javascript
복사
편집
function Square({ value }) {
  return <button className="square">{ value }</button>;
}
3. JSX에서 표현식 사용
JSX는 JavaScript가 아니므로 표현식을 사용할 땐 반드시 {}로 감싸야 함.

위 예시처럼 <button>{ value }</button>로 작성해야 동적으로 렌더링 가능.

4. 값 전달이 안 되면 아무것도 표시되지 않음
Board 컴포넌트에서 value prop을 실제로 전달하지 않으면 버튼에는 아무것도 표시되지 않음.

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

