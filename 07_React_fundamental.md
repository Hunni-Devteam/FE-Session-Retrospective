# 회고 양식 (배웠던 것 / 수업 피드백 / 본인 피드백)

#### 수업에서 좋았던 것
- React 수업을 했다. 누군가에게 React를 설명하는 방법을 어느 정도 깨우친 것 같다.
- 현대 UI 개발의 정수인 React를 처음부터 끝까지 넓고 깊게 다뤄볼 수 있는 기회가 되어 유익했다.
- 커리큘럼 수업 도중 여러 외부 과제를 직접 가져와 해보면서, 동작 방식 설명 / 코드 리뷰 / 리팩토링까지 다룰 수 있었다.
- => 덕분에 학생 숙련도가 생각보다 빨리 올라왔다. (Todo / Pagination / Random Quote)

#### 수업에서 아쉬웠던 점
- 본인 개인사가 심히 겹치면서 멘탈 관리가 어려웠다. 정말 힘들었다.
- 강의 제안이 들어오면서.. 자료 준비하느라 수업이 한두 번 미뤄졌다.

#### 본인에게서 개선된 점
- 공사과 개인사의 영역을 점점 분리해 사용하는 데 적응해가고 있는 듯 하다 (thread가 어설프게 늘어나고 있다..)
- 무너지지 않는다. 더 잘할 수 있고 앞으로도 잘 헤쳐나갈 거다.

#### 배우면서 힘들었던 것
- State/Props 컨셉 설명 => Class => Functional (Hooks) 하면서..
- 자바스크립트 동작(this binding / closure)과 Redux 까지 맥락적으로 다루게 되니 다소 설명이 어려워지는 문제가 있었다.

# React Concept Overview

## React / ReactDOM

React는 기존 DOM API를 사용한 UI 조정, 엘리먼트 추가 및 삭제 과정을
데이터의 변경(state, props)에 반응하도록 도와 주며, 이를 통해 다양한 DOM 동작을 제어할 수 있습니다.

React는 UI 요소의 집합을 `컴포넌트`로 표현하며, 이 UI 요소는 React Element로 표현됩니다.
React Element 는 HTML과 유사한 문법을 지닌 `JSX` 마크업을 사용해 구현할 수 있습니다.

--------- 

위에서 언급한 컴포넌트의 집합(트리)이 ReactDOM 이고,
ReactDOM은 state, props 변경을 감지해
트리를 다시 그리며 각 컴포넌트의 렌더링 여부(JSX 템플릿을 다시 만들어야 할 지)를 결정할 수 있습니다.

이전 렌더링에 사용된 트리와 새 렌더링에 사용될 트리를 비교하고,
실제로 DOM에서 어떤 부분을 변경해야 할 지 취합하는 과정이 **재조정(Reconciliation)** 입니다.

이 비교/렌더링 과정은 직접 DOM 엘리먼트의 값을 비교하지 않고,
JS 트리인 ReactDOM을 비교하기 때문에
이를 Virtual DOM 이라고 부르기도 합니다!

## State / Props

`State`는 컴포넌트 내부의 상태, `Props`는 컴포넌트 외부에서 주입받는 데이터입니다.

`State`를 조작하면 React는 리렌더링을 실행하며(컴포넌트 트리를 다시 그리며),
각 컴포넌트의 `State/Props` 변경 여부를 확인하고, 렌더링이 필요할 경우 JSX 템플릿을 다시 생성합니다.

## Class Component

클래스 컴포넌트는 React 초기부터 존재했고, 지금도 여러 레거시 코드로 찾아볼 수 있습니다.

Component 클래스를 구현하게 되고, 기본적으로 render/lifecycle method, state 속성을 지원하며,
생성자에서 컴포넌트 외부 상태인 props 를 주입받을 수 있습니다.

클래스 컴포넌트의 state는 인스턴스 내부의 상태입니다.
setState 메서드를 사용해 새 값을 할당하고 렌더링을 실행할 수 있습니다.

또한, 컴포넌트는 생명 주기를 가집니다.

컴포넌트의 첫 렌더링 / State, Props 변경으로 인한 컴포넌트 업데이트 / 컴포넌트 제거 등을 통틀어
컴포넌트 라이프사이클이라고 부르며,

실행 시점에 라이프사이클 메서드를 활용해 동작을 추가할 수 있습니다.

대표적으로 아래 3개의 라이프사이클 메서드가 사용됩니다:
`Component[Will/Did]Mount/ Component[Will/Did]Update / Component[Will/Did]Destroy`

## Class Component - this binding issue

클래스 컴포넌트에서 특정 버튼의 이벤트를 통해 state를 갱신하기 위해 `this.setState` 를 실행하려 할 때,

## Class Component - props mutation issue in async function

비동기 함수에서 this.props 를 직접 참조할 경우, setState

## Functional Component / Hooks

Functional Component는 기본적으로 상태를 가지지 못하며,
오직 JSX를 리턴하는 렌더 함수와 같은 동작을 합니다(SFC).

그러나, React 16에서 Hooks가 추가되면서

상태 관리와 라이프사이클 메서드 등을 기존 클래스 컴포넌트에서 사용하던 방식보다 훨씬 간결하게 사용할 수 있게 되었습니다.

주로 사용되는 훅은 `useState`, `useEffect`, `useMemo`, `useCallback` 으로,
각각 함수형 컴포넌트 내의 상태 관리, 라이프사이클 훅, 변수 재선언 방지, 함수 재선언 방지 기능을 제공합니다.

이는 자바스크립트의 동작 중 하나인 `클로저`를 통해 구현되고,
함수 내부의 변수가 외부 스코프로 리턴되었을 경우 메모리에서 해제되지 않는 것을 활용해

Hooks 내부의 값 (state, callback, deps 등...)을
Functional Component의 렌더링을 실행하게 될 React 라이브러리 내부에 붙여 둡니다.

매 렌더링마다 붙여 둔 값과 현재 값을 비교해 렌더링 실행 여부를 결정합니다.

=> React 라이브러리에서 Hook 목록을 저장하는 배열을 가지고 있게 됩니다.

이러한 구현 상의 특징에 따라, Hooks 는 절대 순서와 실행 갯수가 변경되어서는 안 되며,
이는 React 디버깅 과정에서 흔히 발견되는 실수 중 하나입니다.

## Rendering Strategy

기본적으로, 클래스/함수형 컴포넌트 모두 props 변경 여부에 상관 없이 무조건 렌더링을 실행합니다....

클래스 컴포넌트의 경우 최적화를 위해 state, props의 변경점을 체크하고 렌더링 여부를 결정할 수 있는 `shouldComponentRender` 메서드를 직접 작성할 수 있습니다.

함수형 컴포넌트의 경우 아래서 언급할 `React.memo(Compoennt, equalityFn)` 함수의 두 번째 파라미터를 조작하는 것으로 해결할 수 있습니다.

보통의 경우 props 내의 모든 속성이 변경되지 않았을 때에만 렌더링을 방지해도 충분한데,

클래스 컴포넌트의 경우 Component 대신 PureComponent 클래스를 상속받는 것으로 해결할 수 있고,

함수형 컴포넌트의 경우, 고차 함수인 React.memo 를 사용해 직접 작성한 컴포넌트를 감싸주는 것으로 해결할 수 있습니다.


# What i did

### 2021.05.25 - React의 기원과 역사
### 2021.05.26 - 강훈쌤 멘탈바사삭치킨
### 2021.05.27 - 정규상 퇴사 + Farewell Party
### 2021.05.28 - 정규상 개인사
### 2021.05.29 - 토
### 2021.05.30 - 일
### 2021.05.31 - 강훈 회식
### 2021.06.01 - 정규상 회식
### 2021.06.02 - 강훈 12시간 무호흡 코딩 (업무)
### 2021.06.03 - 자습 (JSX)
### 2021.06.04 - 자습 (Stateless Functional Component)
### 2021.06.05 - 토 (김지유 강훈 정규상 술)
### 2021.06.06 - 일 (현충일)
### 2021.06.07 - Class Component, How to pass props (prop drilling)
### 2021.06.08 - Set VSCode development environment
### 2021.06.09 - TodoList(Class Component) Start
### 2021.06.10 - TodoList(Class Component) End / 피드백 (Class to Functional) 
### 2021.06.11 - TodoList - Class Component to Functional Component 마이그레이션
### 2021.06.12 - 토
### 2021.06.13 - 일
### 2021.06.14 - 강훈 강의 제작 미팅, 자습(TodoList 점검 및 Git CLI 사용법)
### 2021.06.15 - React Class Component - this binding 이슈
### 2021.06.16 - React Pagination Component Start
### 2021.06.17 - React Pagination Component End w/styled-components
### 2021.06.18 - React Pagination Component 피드백
### 2021.06.19 - 토
### 2021.06.20 - 일
### 2021.06.21 - 자습
### 2021.06.22 - 자습
### 2021.06.23 - freecodecamp ex1 (Random Quote) start
### 2021.06.24 - Random Quote 자습
### 2021.06.25 - 강훈 개인사정
### 2021.06.26 - 토
### 2021.06.27 - 일
### 2021.06.28 - Random Quote 구현 피드백
### 2021.06.29 - React Lifecycle Methods (willmount / willUpdate / willDestroy <> useEffect)
### 2021.06.30 - Random Quote 구현 피드백 2
### 2021.07.01 - 김지유 첫출근!!
### 2021.07.02 - 다같이 한강가서 술먹음
### 2021.07.03 - 토
### 2021.07.04 - 일
### 2021.07.05 - 강훈 휴가나온 동생 데리러 감
### 2021.07.06 - StudyArchive 초안 기획
### 2021.07.07 - 강훈 멘탈 파괴 + React Session 회고
  
  
# Next Curriculum

Redux - 전역 상태 관리 도구
+ 지역 상태 관리 (react-query + jotai/recoil)

~ 하기 전에..

## Resume Session

Education 탭을 야무지게 채워봅시다.
... 나머지 (Projects / Skills / 등등..)는 지금 채우기가 쉽지 않을 듯 합니다...
