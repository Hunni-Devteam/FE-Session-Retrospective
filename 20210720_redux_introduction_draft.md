# Redux = Action 으로 모든 상태 변화를 추적할 수 있다

Store : 전역 데이터 저장소(JS Object)

Action : State 변경 트리거 (Setter)
dispatch(setProductsAction(products))

Reducer : Action 별 State 갱신 방식 정의 넘어온 값의 후처리 - setProductsAction: (products) => ({ allProduct, ids })

Middleware:
Action 실행시 같이 실행되어야 하는 동작들
미들웨어도 다른 Action을 실행할 수 있음
(GetProducts 수신 => [API 요청] => API 요청 결과로 미들웨어가 SetProducts 트리거)

Reducer - Action = 1:1 대응


```js

productReducer: () => {}

userReducer: () => {}

postsReducer

friendsReducer

combineReducer({
  product: productReducer,
  user: userReducer,
});

Redux.runReducer = (state, action) => {
    const prevState = state;
    let newState = state;

    Redux.registeredReducers.forEach((reducer) => {
      newState = reducer(state,action);
    });

    const isChanged = compareObject(prevState, newState);
    
    if (isChanged) React.setState(newState);
}
```

## Redux Core 코드 굉장히 짧음 한번 볼만함 (200줄 안되는걸로아는데..?)

string literal 사용하면 실수하기 쉬우니 ..
변수에 action type 할당하고 
reducer switch, action creator 에서 재활용

```js
store.dispatch = (action) => {
  runReducer(store.state, action);
  // 미들웨어 실행
  store.subscribers.forEach((cb) => cb(store.state, action);
}

// 니가 로그인 액션을 커스터마이즈 (비동기 등등..)하고싶으면
// 직접 콜백 함수(비동기 리듀서 비스무레한거..)를 등록해
store.subscribe((state, action) => {
  
  if (action.type === 'LOGIN') {
    const loginResult = await ajax.post('api/login', { action.id, action.pw });

    if (loginResult.status === 200) {
       redux.dispatch({ type: 'SET_USER', loginResult });
    }
  }
});
```

// 리듀서가 비동기로 동작하면 Action 의 실행 순서를 추적할수가 없음
// Redux Devtools 에서 Action 실행 순서 === 상태 변경 순서
// ㄱㅡ러니까 .. Action 이 실행되는 순간은 무조건 상태가 갱신되는거야

```js
class store {
   subscribers: [],
   subscribe: (cb) => {
      this.subscribers.push(cb)
   },
   dispatch: (action) => {
      let newState = {…this.state};
      this.reducers.forEach((reducer) => {
        newState = reducer(this.state, action);
      });

      this.subscribers.forEach((middleware) => middleware(this.state, action);
      // react-redux?
      if (compare(this.state, newState)) {
         ReduxProviderComponent.setState();
      }
   },
   state: null,
   reducers: [],
   createStore: (reducers) => this.reducers = reducers,
}
```

간단하게 얘기하면 비동기 Reducer 임

브라우저에서 마우스 이동할 때 특정 함수를 실행하고 싶으면 addEventListener 를 쓰는 것처럼

Redux Action 실행됬을때 특정 함수를 실행하고 싶으면 store.subscribe 로 넘기면 됨

Reducer 랑 완전 똑같이 state, action 받고 if (action.type === 'USER_LOGIN') 로 분기 치는데

Middleware 에선 Reducer 처럼 state 갱신할 의무도 없고, 비동기 처리만 해도 괜찮고... 무슨 짓을 해도 상관 없음.

```js
store.subscribe(() => {
  const state = store.getState();
  const action = store.dispatchedActions[store.dispatchedActions.length-1];
  
  // 요런 느낌..?
  if (action.type === 'LOGIN') 비동기 처리...
});
```

# 20210721 Redux Core Overview

## Middleware !== Store.Subscribe

https://github.com/reduxjs/redux/blob/master/src/createStore.ts
https://github.com/reduxjs/redux/blob/master/src/applyMiddleware.ts

store 인스턴스 생성 =>
default state, reducer 주입 => 
enhancer 에서
applied middlewares 받아서 주입
=>
미들웨어가 부착된 Store 인스턴스 반환(dispatch 오버라이드)

미들웨어는 store 생성 시점에
store.getState API를 주입받아야 하니 런타임에 추가하는 게 불가능하고

subscriberFn 은 dispatch 될 때마다 nextSubscribers 에 머 들어왔는지 체크하고 실행하니 런타임에도 추가가 가능하다 ..
