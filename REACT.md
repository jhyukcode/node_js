react

1. react 설치
2. 디자인 적용 - antd / 반응형 / 최적화 렌더링
3. redux
4. saga
5. etc - 스크롤링, faker dummy ..

---

1. react 설치

- node : 자바스크립트를 실행할 수 있게 해주는 런타임
  비동기식으로 이뤄지는 대표적인 프로그램
- npm : 노드 패키지 매니저

```bash
node -v
npm -v
```

```bash
mkdir front
cd front
```

1-2. next
https://npmtrends.com/

react : 데이터 연동 시 단방향
vue : 양방향

1-3. next
npm 초기화

```bash
npm init
```

npm 설치

```bash
npm i next@13.4.13
```

react 설치

```bash
npm i react@18.3.1 react-dom@18.3.1
```

package.json 실행

```bash
"author":"kjh",
"scripts":{"dev" : "next"}
```

```bash
npm run dev
```

[pages] - index.js

```bash
import React from "react";

const Home = () => {
  return <div> Hello, next</div>;
};
export default Home;
```

```bash
npm run dev
```

[pages] - profile.js, signup.js
localhost:3000/profile
localhost:3000/signup

1-4. chrome 확장 프로그램
React Develop Tools
Redux Dev Tools

---

2.  디자인적용 - antd / 반응형 / 최적화 렌더링

2-1. 구조확인
[NODE]
└[back]
└[front]
│└package.json
│└[pages]-index.js, profile.js, signup.js
│└[components]-부품들
│└[hooks]
│└[store]
│└[reducers]
│└[sagas]

2-2. [front] - [components] - AppLayout.js 부품들

2-3 [front] - [pages] - index.js, profile.js, signup.js - AppLayout 사용

- error ./components/AppLayout.js:2:0
  Module not found: Can't resolve 'prop-types'

```bash
npm i --save prop-types
```

2-4. 디자인 적용 - ant design

- https://4x.ant.design/
- react, vue에서 모두 사용 가능한 컴포넌트
- styled-components : 내가 만든 컴포넌트에 자체 css 입혀서 컴포넌트 만들기
- @ant-design/icons : 아이콘 이미지

```bash
npm install --save antd@4
npm install --save styled-components@5
npm install --save @ant-design/icons@5
```

2-5. 디자인 고르기

- https://4x.ant.design/

2-6. [front] - [components] - AppLayout.js - menu 적용
2-7. [pages] - index.js - css 적용

2-8. 웹팩

- 모듈번들러, 웹애플리케이션을 구성하는 여러 파일을 하나의 번들로 묶어주는 역할
  (html, css, js, 이미지 등)
- 로더 : css, 이미지 ..
- 코드 최적화

- nextjs 기본적인 웹팩이 포함됨
- 웹팩이 css를 찾아서 style태그로 바꿔서 html에 넣어줌

2-9. [pages] - \_app.js

- 공통 css import
- 모든 페이지 공통

2-10. 공통 레이아웃, 검색폼
[front] - [components] - AppLayout.js

- https://4x.ant.design/components/grid/

- 컬럼 24개
- 각 디바이스 사이즈별로 디자인 가능
  xs : 모바일, sm : 태블릿, md : 데스크탑
- gutter : grid layout 컬럼 간격 사이 간격 주기
- <a href="https://company.com
  target="\_blank"
  rel="noreferrer noopener>Company</a>
  noreferrer : 다른 페이지 이동 시 링크를 건 페이지의 주소 정보를 브러우저가 header로 송신하지 않음
  noopener : 다른 페이지 이동 시 링크를 건 페이지를 참조할 수 없게 됨

2-11. 왼쪽메뉴 : 로그인폼 / 프로필

- [front] - [components] - LoginForm.js / Profile.js
- 사용 > [front] - [components] - AppLayout.js

Hook : React의 상태를 관리, 컴포넌트 내부에서 가변 역할

비구조화 할당 문법
let arr = [1, 2];
lat a = arr[0];
let b = arr[1];
let [c,d] = arr;

2-12. Component - signup.js / profile.js / [hooks] - userinput.js

- 화살표함수
  ()=>{} return 필요
  ()=>() 자동반환, 출력할 때

const user1 = () => { return {name:'name', age:3};};
const user2 = () => ( {name:'name', age:3};);
[!] ()=>() 에 return 사용 시 "Uncaught SyntaxError: Unexpected token 'return'" 오류 발생

const num = [1,2,3,4];
const test1 = num.filter((num) => {return num%2==0;});
const test2 = num.filter((num) => ( num%2==0 ) );

2-13. 리렌더링

- style={{}}
- 객체와 객체를 비교하면 false

let obj1={}
let obj2={}
obj1 === obj2

> false

- virtual dom 으로 검사하다가 새로 바뀐 부분이 생기면 렌더링 반복

- UserProfile.js > ButtonWrapper : style``
- AppLayout.js > styled : style('components')``
- useMemo : stylebg 값 캐싱

test. FollowList.js 최적화

2-14. 댓글쓰기 폼 - 리렌더링 / 댓글폼은 test

---

3. redux

3-1. redux

- 중앙 데이터 저장소
- 로그인한 정보
- 에러추적 가능

```bash
npm i redux@4.0.5
npm i react-redux@8.0.5
npm i next-redux-wrapper@8.1.0
npm i redux-devtools-extension
```

3-2.

최상위 컴포넌트 - index.js
↓
[AppLayout] isLoggedIn 값 [redux]
↓
[LoginForm], [UserProfile]

Action -> Dispatch -> Reducer -> Store 데이터가 단방향

Dispatch -> Store R1 R2 [State]
↑
[LoginForm] 버튼 누르기(Action)

3-3. 전개함수
const arr1 = [1,2,3];
const arr2 = [4,5,6];
const arr = [...arr1, ...arr2];
console.log(arr); > [1, 2, 3, 4, 5, 6]

const obj1 = {a:1, b:2};
const obh2 = {c:3, d:4};
const obj = {...obj1, ...obj2};
console.log(obj);

3-4. PostCard - Image

이미지 캐러셀 ( react - slick )

> https://www.npmjs.com/package/react-slick

```bash
npm i react-slick
```

---

4. saga

4-1. redux-saga

- redux의 미들웨어
- 미들웨어 : 기능향상
- 비동기 액션을 디스패치 할 수 있게 해주는 역할

4-2. axios

- 웹 요청 비동기 라이브러리

4-3. 설치

```bash
npm i redux-saga@1.1.3
npm i axios
```

4-4. generator 함수

- function\*
- yield 에서 멈춤, 중간지점이 있는 함수

(1) generator

```bash
const gen = function(){}

gen()
gen().next()
```

(2) yield

```bash
const gen = function*(){
  console.log(1);
  yield;

  console.log(2);
  yield;

  console.log(3);
  yield;
}

const g = gen()
g.next()
g.next()
g.next()
g.next()

```

(3) 무한반복

```bash
let i=0;
const gen = function*(){
  while(true){
    yield i++;
  }
}

const g = gen()
g.next()

```
