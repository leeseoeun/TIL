- **React**
    - 프로젝트 스캐폴딩<br>

*console*
```
[~/Desktop]$ npm i -g create-react-app
[~/Desktop]$ create-react-app hello-react
```

*visual studio code*
```
[~/Desktop/hello-react]> npm install
```

또는

*console*
```
// -g 옵션이 없어도 global로 생성
[~/Desktop]$ npx create-react-app hello-react
```

*visual studio code*
```
[~/Desktop/hello-react]> npm start
```

<br>

*App.js*
```javascript
import logo from './logo.svg';
import './App.css';

function App() {
  const myName = '이서은';
  return (
    // jsx
    // {변수명} : 데이터 템플릿팅
    <div>Hello World! {myName}</div>  // 한개의 태그만 리턴
  );
}

export default App;
```
