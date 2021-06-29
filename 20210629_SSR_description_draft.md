
# React = JS 실행이 가능해지는 시점에 DOM API 사용해 렌더링을 한다

근데 .. 네트워크 환경이 안좋은 곳에서는 JS 로딩하는데까지 시간이
많이 걸릴 수 있음 (CSS flickering 과 비슷한 현상)

그래서 ... 빌드할 때 initial state 가지고 렌더링 결과(HTML)을 만들어놓는거임

그러고 ... JS 실행 가능해지기 전에 미리 그려놓음 (HTML 파일로 ReactDOM 초기 렌더링 결과를 받으니까)

이따가 ... React 초기화될 때 그려져있는 DOM에다가 state, event 를 바인딩하는거 (Hydration)

**그래서 이미 그려진 DOM 트리에 reactivity 를 "흘려 보낸다"
해서 hydration** (수화, 컴포넌트의 UI 반응성을 주입한다)

**Redux-persist 의 hydration 도 같은 뜻** (initial state => localStorage injection)

NextJS = 빌드시 Page 단위로 정적 HTML 생성 (SSR) 지원 = 서버에서 뼈대를 내려줌
(ReactDOM.render 할때 어차피 그리는데 서버에서 먼저 렌더 한번 해보고 결과물 뼈대 내려줌)

# 결론

1. 스켈레톤 UI 그리는 속도 빠르게 할려고 (Initial Page Loading)
2. (!!)페이지별로 Head 태그 (OpenGraph 태그) 다르게 쓰려고 (SEO)
없으면 로봇이 직접 클라이언트 라우터를 뒤져야하는데 …

서버사이드 렌더링 = HTML 뼈대귀 좀 더 만들어서 내주겠다.
