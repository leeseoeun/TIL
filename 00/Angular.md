- **Angular**
    - 프로젝트 스캐폴딩<br>

*console*
```
[~/Desktop]$ npm i -g @angular/cli
[~/Desktop]$ ng new hello-angular
```

*visual studio code*
```
[~/Desktop/hello-angular]$ npm start
```

*app.module.ts*
```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'hello-angular';
  myName = '이서은';
}
```

*app.component.html*
```javascript
// {{변수명}} : 데이터 템플릿팅
<div>
  <h1>Hello World!</h1>
  <p>My name is {{myName}}</p>
</div>
```

*app.component.ts*
```javascript
h1 {
    color: blueviolet;
}
```