# State 끌어올리기

## 흐름

- 한 데이터의 변경 사항을 여러 컴포넌트에 반영해야 하는 경우, 가장 가까운 공통 조상으로 state를 끌어올리는 것이 좋음
  - 그렇게 하지 않으면 값이 동기화되어 있어야 하는 각 컴포넌트가 동기화되지 않아서 서로 다른 정보를 보여준다.
  - 끌어올린 state가 있는 컴포넌트는 그 state에서 다루는 데이터에 대한 ‘진실 공급원’(source of truth)
- 그런데 상위 컴포넌트의 state에 있는 공통 데이터는 하위 컴포넌트에 props로 전달되는데, props는 읽기 전용이라 props를 직접 수정할 수 없음
  - JavaScript에서는 함수도 값이므로 props로 함수를 넘겨받아서 컴포넌트를 제어할 수 있음

## 정리

한 데이터의 변경 사항을 여러 컴포넌트에 반영해야 하는 경우,

1. 가장 가까운 공통 조상으로 state 끌어올리기
2. 상위 컴포넌트에서 핸들러 함수를 구현해 놓고, 이 함수를 하위 컴포넌트의 props로 전달

## 교훈

- 여러 컴포넌트 사이에서 데이터를 동기화하려고 이상한 짓 하지 말고, **하향식 데이터 흐름**에 맡길 것
- 장점
  - 어떤 state든 특정 컴포넌트 안에 존재하고 그 컴포넌트가 자기 state를 변경할 수 있으므로, 버그가 있을 수 있는 범위가 크게 줄어듦
  - 사용자 입력을 거부하거나 변형하는 자체 로직 구현 가능
- 단점: 양방향 바인딩 접근 방식보다 더 많은 ‘보일러 플레이트’ 코드 작성
