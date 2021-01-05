# [React] 메모

* Real DOM과 Virtual Dom이 있음

* Real DOM

  * 어떠한 변경 사항이 생길 때, 전부를 Reload 해야한다.

* Virtual DOM

  * 어떠한 변경 사항이 생길 때, 변경된 부분만 Reload 한다.
    * Virtual은 처음에 페이지가 Load 될 때, 스냅샷을 찍어서 변경 사항을 감시한다.
    * 변경 사항이 생기면 해당 부분만 로드한다.

* 예전에는 React를 설정하는데 오랜 시간이 걸렸다.

  * `Babel`과 `Webpack`을 설정하는 것이 힘들었다.
    * 이제는 자동으로 설정 해줌

* Babel

  * 최신 자바스크립트 문법을 지원하지 않는 브라우저들을 위해서 최신 자바스크립트 문법을 구형 브라우저에서도 실행 될 수 있게 변환 시켜준다.
    * 최신 자바스크립트 문법을 ES5 자바스크립트 문법으로 변환시킴

* Webpack

  * 기존에는 HTML, JS, CSS로 간단하게 만들었지만, 현재는 많은 라이브러리들과 프레임워크를 사용하게 됨.
    * 즉, 복잡해졌다.
  * Webpack은 이러한 것들을 묶어주는 역할을 한다.
  * 배울 것이 많은 부분...
  * 많은 것들을 간단하게 합쳐준다.

* **프로젝트 구성**

  * 특정 디렉토리에서 리엑트 자동 구성

    ```bash
     npx create-react-app .
    ```

    ```
    Success! Created source at C:\dev\project\react\react.study\source
    Inside that directory, you can run several commands:
    
      npm start
        Starts the development server.
    
      npm run build
        Bundles the app into static files for production.
    
      npm test
        Starts the test runner.
    
      npm run eject
        Removes this tool and copies build dependencies, configuration files      
        and scripts into the app directory. If you do this, you can’t go back!    
    
    We suggest that you begin by typing:
    
      cd C:\dev\project\react\react.study\source
      npm start
    ```

* 원래는 npm을 이용하여 설치를 진행하였음

* NPM vs NPX

  * NPM은 Package Manager
    * Package를 관리해 줌

* NPM package 설치

  * locally

    ```
    npm install <package>
    ```

  * globally

    ```
    # 전역
    npm install -g <package>
    ```

* 원래는 react app을 global하게 받았다.

  ```
   # 전역
   npm install -g create-react-app
  ```

* 이제는 `npx`를 이용하여 굳이 다운로드하지 않아도 npm registry에서 `create-react-app` package를 알아서 실행 시켜준다.

  * 항상 최신 버전을 사용할수 있다.
  
* react app을 실행한 디랙토리에 프로젝트 구성 파일들이 생성된 것을 확인할 수 있다.

  ```
  npm run start
  ```

* `app.js`의 일부를 수정하면 바로 반영된다.

* `index.js`

  ```javascript
  import React from 'react';
  import ReactDOM from 'react-dom';
  import './index.css';
  import App from './App';
  import reportWebVitals from './reportWebVitals';
  
  ReactDOM.render(
    <React.StrictMode>
      // App이라는 컴포넌트가 포함된 것
      <App />
    </React.StrictMode>,
    document.getElementById('root')
  );
  
  // If you want to start measuring performance in your app, pass a function
  // to log results (for example: reportWebVitals(console.log))
  // or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
  reportWebVitals();
  ```

* `webpack`은 `src` dir만 관리한다. `public` dir은 관리하지 않음.

  * 따라서 `webpack`이 관리해주어야 하는 resource는 `src` dir에 넣어주어야 한다.

* 프로젝트 디렉토리 구조 변경

  ```
  /src
  	+ _actions    -- Redux를 위한 폴더들
  	+ _reducers
  	+ components  
  		+ views	  -- Page들이 위치
  			+ something/Sections  -- 해당 페이지에 관련된 css 파일이나, Component가 위치
      + App.js	  -- Routing 관련 일을 처리
      + Config.js	  -- 환경 변수같은 것들을 정함
      + hoc		  -- Higher Order Component 재사용이 되는 것들을 이곳에 넣어줌
      + utils		  -- 여기도 재사용성 높은 것들을 넣어둠
              
  		
  ```

* HOC는 굉장히 유용한 듯

  * 로그인 여부 체크 같은 로직에 사용하면 좋음

* **ES7 React/Redux/GraphQL/React-Native snippets**

  * 코드 양식?? 자동완성 해줌. 

    ```
    // react funtional component
    rece
    
    // react class component
    rcc
    ```

* Router예제

  ```react
  import React from 'react';
  import {
    BrowserRouter as Router,
    Switch,
    Route
  } from "react-router-dom";
  import LandingPage from './components/views/LandingPage/LandingPage';
  import LoginPage from './components/views/LoginPage/LoginPage';
  import RegisterPage from './components/views/RegisterPage/RegisterPage';
  
  function App() {
    return (
      <Router>
        <div>
          {/*
            A <Switch> looks through all its children <Route>
            elements and renders the first one whose path
            matches the current URL. Use a <Switch> any time
            you have multiple routes, but you want only one
            of them to render at a time
          */}
          <Switch>
            <Route exact path="/" component={LandingPage} />
            <Route path="/login">
              <LoginPage />
            </Route>
            <Route path="/register">
              <RegisterPage />
            </Route>
          </Switch>
        </div>
      </Router>
    );
  }
  
  export default App;
  ```

  

