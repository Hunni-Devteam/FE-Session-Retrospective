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

React는 UI 요소의 집합을 '컴포넌트'로 표현하며, 이는 React Element의 집합입니다.
React Element 는 HTML과 유사한 문법을 지닌 `JSX` 마크업으로 구현할 수 있습니다.

-

위에서 언급한 컴포넌트의 집합(트리)이 ReactDOM 이고,
ReactDOM은 state, props 변경을 감지해
트리를 다시 그리며 각 컴포넌트의 렌더링 여부(JSX 템플릿을 다시 만들어야 할 지)를 결정할 수 있습니다.

이전 렌더링에 사용된 트리와 새 렌더링에 사용될 트리를 비교하고,
실제로 DOM에서 어떤 부분을 변경해야 할 지 취합하는 과정이 **재조정(Reconciliation)** 입니다.

이 비교/렌더링 과정은 직접 DOM 엘리먼트의 값을 비교하지 않고,
JS 트리인 ReactDOM을 비교하기 때문에
이를 Virtual DOM 이라고 부르기도 합니다!

## State / Props

State 는 컴포넌트 내부의 상태, Props 는 컴포넌트 외부에서 주입받는 데이터입니다.

State 를 조작하면 React는 리렌더링을 실행하며(컴포넌트 트리를 다시 그리며),
각 컴포넌트의 State/Props 변경 여부를 확인하고, 렌더링이 필요할 경우 JSX 템플릿을 다시 생성합니다.

## Class Component

클래스 컴포넌트는 React 초기부터 존재했고, 지금도 여러 레거시 코드로 찾아볼 수 있습니다.

컴포넌트의 첫 렌더링 / state, props 변경으로 인한 컴포넌트 재 렌더링 / 컴포넌트 제거 과정을 통틀어



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
