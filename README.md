
1. setting up
node.js 최신버전 설치
vscode 설치
작업폴더 생성
터미널에 npx create-react-app blog 입력

src/App.js -> 메인페이지에 들어갈 내용
public/index.html -> 실질 메인페이지
App.js 에 있는 내용을 index.html 에 넣는것
넣어주는역할은 index.js 가 해줌

2. 태그에 class 주는 법
react는 자바스크립트를 사용하기 때문에 class라는 문법이 있음. 그래서 className을 씀 (camelCASE 작명관습)
<div className="클래스명"></div>
디자인은 App.css에서 하면됨

3. 리액트에서 데이터 바인딩 쉽게하는 법
자바스크립트에선 document.getElementbuId().innerHTML = '내용';

리액트에선
let 변수명 = "내용";
<h4>{ 변수명 }</h4>

src, id, href 등의 속성에도 {변수명, 함수 등}

4. JSX 에서 style 속성 집어넣을 때
style = {object 자료형으로 만든 스타일}
(귀찮으니 className 쓰샘)
style 속성도 let 변수명 = "style내용"; 하면 변수로 지정가능

5. useState 만드는 법
리액트의 데이터 저장공간

import React, { useState } from 'react';      //리액트에 있는 내장 함수 하나를 쓰겠다는 말

useState('내용'); [a, b]
a에는 내용 데이터가 들어감
b에는 내용 state 정정해주는 함수

let [a, b] = useState('내용1, 내용2, ...');      //state 는 요렇게 씀
(참고, ES6 destructuring 문법)
var [a, b] = [10, 100];           //array, objcet 에 있던 자료를 변수에 쉽게 담고 싶을 때

useState를 사용할 땐
변수 대신 쓰는 데이터 저장공간이므로 useState()를 이용해 만들어야함
<h3> { a[0] } </h3>

* state에 데이터를 저장해놓는 이유 : 웹이 App처럼 동작하게 만들고 싶어서
  데이터가 바뀌는 경우에 새로고침을 하지않고 **HTML이 자동으로 재렌더링**이 된다.
  그러므로 자주 바뀌거나, 중요한 데이터는 변수 말고 state로 저장해서 쓰자

터미널에 뜨는 warning eslint 보기싫으면 맨위에 /* eslint disable */ 라고 쓰면됨

6. 버튼 만드는 법
리액트에서는
onClick = { 클릭될 때 실행할 함수 }
onClick = { () => { 실행할 내용} }

ex) 따봉 누를 때마다 1 증가시키게 하려면
먼저 state로 만듬
let [따봉, 따봉변경] = useState(0);
다음으로 state 시용해서 함수, state는 변경방법이 따로있음. -> 따봉변경()
<h3> <span onClick={ ()=>{ 따봉변경(따봉 + 1) } }>따봉</span> {따봉} </h3>

7. state 맘대로 변경하는법

수정덴 [데이터]를 만듬. 근데 state를 **deep copy** 해서 수정해야함
ex) 버튼을 누루면 남자코트추천 -> 여자코트추천 으로 바뀌게 하고싶음
let [글제목, 글제목변경] = useState(['남자 코트 추천', '강남 우동 맛집', '파이썬독학']);
 function 제목바꾸기(){
    var newArray = [...글제목];        // var newArray = 글제목; (이건 복사가 아니라 값 공유) deep copy 란 값공유 X, 서로 독립적인 값을 가지는 복사, 리액트 대 원칙 : immutable data
    newArray[0] = '여자 코트 추천';
    글제목변경( newArray );
 }

 <Array, Object state 데이터 수정 방법>
 - 일단 변경함수 써야함
 - 변경함수(대체할데이터)
 - state는 직접 건들지마셈, deep copy해서 그걸 건드셈
   1. 일단 기존 state 카피본 만들고
   2. 카피본에 수정사항 반영하고
   3. 변경함수()에 집어넣기        (꼭 외우기)

8. Component로 HTML 깔끔하게 줄이는 법

- Component 만드는 법
  fucntion Modal()[      // 이름짓기
  return (
  <div></div>            // 원하는 HTML 담고
  )
  }

<Modal />                // 맘대로 사용

정리하면
- 함수 만들고 이름짓고 (첫글자 대문자하기)
- 축약을 원하는 HRML 넣고
- 원하는 곳에서 <함수명 />

**주의할점!**
1. 이름은 대괄호, 대문자사용
2. return() 안에 있는건 태그하나로 묶어야함
3. return() 내부를 묶을 때 의미없는 <div> 쓰기 싫으면 <> </>

반복출현하는 HTML 덩어리나 자주 변경되는 HTML UI들을 Component로 만들면 좋음

Component 많이 만들면 단점 : state 쓸 때 복잡해짐
state는 다른 function 안에서 선언함 -> 범위가 다른 function 까지
Component 범위 function 에선 적용이 안됨
상위 component에서 만든 state 쓰려면 props 문법 이용해야함 
  
  
  

# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
