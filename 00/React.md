- **React**
    - 프로젝트 스캐폴딩<br>

*console*
```
[~/Desktop]$ npm i -g create-react-app
[~/Desktop]$ create-react-app hello-react

또는

[~/Desktop]$ npx create-react-app hello-react
```

*visual studio code*
```
[~/Desktop/hello-react]$ npm install
```

*App.js*
```javascript
import logo from './logo.svg';
import './App.css';

function App() {
  const myName = '이서은';
  return (
    // jsx
    // {변수명} : 데이터 템플릿팅
    <div>Hello World! {myName}</div>
  );
}

export default App;
```
