# JavaSrcipt

<br>

- `중간 평가`
    - `중첩 반복문을 사용하는 피라미드`
- 혼자 공부하는 자바스크립트
- Yeoman
- JHipster

<br><br>

## JavaScript 활용

<br>

- 서버리스

<br>

- 모바일 애플리케이션의 종류
    - |종류|설명|
        |-|-|
        |네이티브 앱|특정 운영체제(OS)에서 직접 실행되는 애플리케이션|
        |크로스 플랫폼|한 번의 코드 작성으로 여러 운영체제에서 동작하는 애플리케이션<br>- Flutter, React Native|
        |하이브리드 앱|웹 기술(HTML, CSS, JavaScript)로 개발한 웹 페이지를 네이티브 앱처럼 감싼 형태의 애플리케이션<br>- WebView|
        |웹 앱|브라우저에서 실행되는 모바일 웹사이트|

<br><br>

## 기본 용어

<br>

- 표현식
    - 값을 만들어 내는 코드 조각

<br>

- 문장
    - 특정 작업을 수행하는 코드

<br><br>

## 기본 자료형

<br>

- 기본 자료형
    - 숫자(number)
    - 문자열(string)
    - 불(boolean)

<br>

- 모든 언어는
    - 기본 자료형
    - 객체 자료형이 있음

<br>

- 문자열 자료형
    - ```javascript
        // '\\ \\ \\ \\'
        // -> \\는 백 슬래시 자체를 의미
        "\\ \\ \\ \\"

        // Uncaught SyntaxError: Invalid or unexpected token
        // -> 백 슬래시는 이스케이프 문자로 사용
        // => "'"' : 문자열이 제대로 닫히지 않았다고 판단
        "\"
        ```
    - 문자열도 배열임

<br>

- 불 자료형
    - ```javascript
        '가방' > '하마' // false
        // 자바스크립트는 문자열을 유니코드 값을 기준으로 사전순으로 비교
        ```

<br>

- 자료형 검사
    - ```javascript
        typeof('문자열')        // 'string'
        typeof(273)             // 'number'
        typeof(true)            // 'boolean'
        typeof '문자열'         // 'string'
        typeof 273              // 'number'
        typeof 10 === 'number'  // true
        ```

<br>

- 템플릿 문자열
    - ```javascript
        console.log('표현식 273 + 52의 값은 ' + (273 + 52) + '입니다.');
        console.log(`표현식 273 + 52의 값은 ${273 + 52}입니다.`);

        // 표현식 273 + 52의 값은 325입니다.
        ```

<br>

- == 연산자와 != 연산자
    - ```javascript
        1 == "1"        // true
        false == "0"    // true

        "" == []        // true
        // 자바스크립트는 빈 배열을 숫자로 변환
        // 빈 배열 []은 빈 문자열로 변환된 다음, 이 빈 문자열이 다시 숫자 0으로 변환
        // 빈 문자열 ""도 숫자 0으로 변환

        0 == []         // ture
        ```

<br><br>

## 상수와 변수

<br>

- 변수
    - let을 쓰는 게 좋음

<br>

- 복합 대입 연산자
    - ```javascript
        // 변수를 선언합니다.
        let list = '';

        // 연산자를 사용합니다.
        list += '<ul>';
        list += '   <li>Hello</li>';
        list += '   <li>JavaScript..!</li>';
        list += '<ul>';
            
        // 문서에 출력합니다.
        document.write(list);
        ```

<br>

- undefined 자료형
    - 변수가 선언되지 않았을 때
    - 변수가 선언되었지만 초기화되지 않았을 때
    - 객체의 존재하지 않는 속성(프로퍼티)에 접근할 때

<br><br>

## 자료형 변환

<br>

- 문자열 변환
    - ```javascript
        // 상수를 선언합니다.
        const input = prompt('message', '_default');

        // result = window.prompt(message, default);
        // message  : 사용자에게 보여줄 문자열
        // default  : 텍스트 입력 필드에 기본으로 채워 넣을 문자열

        // 출력합니다.
        alert(input);
        ```

<br>

- 숫자 자료형으로 변환하기
    - Number 객체 사용
        - ```javascript
            Number("273")           // 273
            typeof(Number("273"))   // 'number'
            Number("$273")          // NaN
            typeof(Number("$273"))  // 'number'
            Number(true)            // 1
            Number(false)           // 0
            ```
    - 숫자 연산자 사용
        - ```javascript
            "52" - 0            // 52
            typeof("52" - 0)    // 'number'
            true - 0            // 1
            typeof (true - 0)   // 'number'
            1 + true            // 2
            1 + false           // 1
            ```

<br>

- 문자열 자료형으로 변환하기
    - String 객체 사용

<br>

- 불 자료형으로 변환하기
    - Boolean 객체 사용
    - 논리 부정 연산자 사용
        - ```javascript
            !!273           // true
            !!0             // false
            !!'안녕하세요'  // true
            // 자바스크립트에서 비어 있지 않은 문자열은 true 값
            !!''            // false
            // 자바스크립트에서 빈 문자열('')은 false 값

            // false 값 :
            // - false
            // - 0
            // - '' (빈 문자열)
            // - null
            // - undefined
            // - NaN (Not-a-Number)

            // true 값 :
            // false 값이 아닌 모든 값
            ```

<br>

- inch를 cm 단위로 변경하기
    - ```javascript
        // 숫자를 입력받습니다.
        const rawInput = prompt('inch 단위의 숫자를 입력해주세요.');

        // 입력받은 데이터를 숫자형으로 변경하고 cm 단위로 변경합니다.
        const inch = Number(rawInput);
        const cm = inch * 2.54;

        // 출력합니다.
        alert(`${inch}inch는 ${cm}cm 입니다.`);
        ```

<br><br>

## if 조건문

<br>

- new Date().getMonth()
    - month는 항상 +1을 해야 됨

<br><br>

## switch 조건문

<br>

- switch 조건문
    - ```javascript
        // 표현식에 조건문을 넣을 수 있음
        switch (input % 2) {
            // ... 생략
        }
        ```

<br><br>

## 기타 조건문

<br>

- 조건부 연산자
    - ```javascript
        const readline = require('readline');

        // readline 인터페이스 생성
        const rl = readline.createInterface({
            input: process.stdin,
            output: process.stdout
        });

        // 사용자에게 숫자를 입력받음
        rl.question('숫자를 입력해주세요 : ', (answer) => {
            const number = Number(answer);  // 입력 받은 값을 숫자로 변환

            // 조건문
            const result = number >= 0 ? '0 이상의 숫자입니다.' : '0보다 작은 숫자입니다.';
            console.log(result);
            
            // readlin 인터페이스 닫기
            rl.close();
        });
        ```

<br><br>

## 배열

<br>

- 배열 만들기
    - 함수도 배열에 들어갈 수 있음
        - ```javascript
            const array = [273, 'String', true, function() { }, {}, [273, 103]]
            ```

<br>

- 배열 뒷부분에 요소 추가
    - push 메소드 사용
        - ```javascript
            const todos = ['우유 구매', '업무 메일 확인하기', '필라테스 수업']
            todos.push('저녁 식사 준비하기')
            ```
    - 인덱스 사용
        - ```javascript
            const fruitsA = ['사과', '배', '바나나']
            fruitsA[10] = '귤'
            
            fruitsA // ['사과', '배', '바나나', empty × 7, '귤']
            // 중간에 empty로 공백이 생김
            ```

<br>

- 배열 요소 제거하기
    - 인덱스 사용
        - ```javascript
            const itemsA = ['사과', '배', '바나나']
            itemsA.splice(2, 1) // 배열의 2번째 인덱스로부터 1개 요소를 제거
            ```
    - 값 사용
        - ```javascript
            const itemsA = ['사과', '배', '바나나']
            const index = itemsB.indexOf('바나나')
            index                       // 2
            itemsA.splice(index, 1)     // ['바나나']
            itemsB                      // ['사과', '배']
            itemsB.indexOf('바나나')    // -1
            ```

<br><br>

## 반복문

<br>

- for in 반복문
    - ```javascript
        const todos = ['우유구매', '업무 메일 확인하기', '필라테스 수업']

        for (const i in todos) {    // 배열의 인덱스 반환
            console.log(`${i}번째 할 일: ${todos[i]}`);
        }

        // 0번째 할 일: 우유구매
        // 1번째 할 일: 업무 메일 확인하기
        // 2번째 할 일: 필라테스 수업
        ```

<br>

- for of 반복문
    - ```javascript
        const todos = ['우유구매', '업무 메일 확인하기', '필라테스 수업']

        for (const todo of todos) { // 배열의 값 반환
            console.log(`오늘의 할 일: ${todo}`);
        }

        // 오늘의 할 일: 우유구매
        // 오늘의 할 일: 업무 메일 확인하기
        // 오늘의 할 일: 필라테스 수업
        ```

<br>

- |for in|for of|
    |-|-|
    |배열의 인덱스 반환|배열의 값 반환|

<br>

- `중첩 반복문을 사용하는 피라미드`
    - ```javascript
        // let 변수를 선언합니다.
        let output = '';

        // 중첩 반복문
        for (let i = 1; i < 15; i++) {
            for (let j = 15; j > i; j--) {
                output += ' ';
            }
            for (let k = 0; k < 2 * i - 1; k++) {
                output += '*';
            }
            output += '\n';
        }

        // 출력합니다.
        console.log(output);
        ```

<br><br>

 - 함수 기본
    - ```javascript
        function min(array) {
            let output = array[0];
            for (const item of array) {
                // 현재 output 보다 더 작은 item이 있다면
                if (output > item) {
                    // output 값을 item으로 변경
                    output = item;
                }

                // 최댓값
                // if (output < item) {
                //     output = item;
                // }
            }
            return output;
        }

        const testArray = [52, 273, 32, 103, 275, 24, 57];
        console.log(`${testArray}중에서`);
        console.log(`최솟값 = ${min(testArray)}`);
        ```

<br>

- 나머지 매개변수
    - 함수의 매개변수로 전달된 인자 중, 정해진 매개변수 외의 나머지 인자들을 하나의 배열로 묶어주는 기능
    - 나머지 매개변수는 개수 제한이 없음
        - ```javascript
            function sample(...items) {
                console.log(items);
            }

            sample(1, 2);       // [ 1, 2 ]
            sample(1, 2, 3);    // [ 1, 2, 3 ]
            smaple(1, 2, 3, 4); // [ 1, 2, 3, 4 ]
            ```
        - ```javascript
            function min(first, ...rests) {
                // 변수 선언하기
                let output;
                let items;

                // 매개변수의 자료형에 따라 조건 분기하기
                if (Array.isArray(first)) {
                    output = first[0];
                    items = first;
                } else if (typeof first === 'number') {
                    output = first;
                    items = rests;
                }

                // 이전 절에서 살펴보았던 최솟값 구하는 공식
                for (const item of items) {
                    if (output > item) {
                        output = item;
                    }
                }
                return output;
            }

            console.log(`min(배열): ${min([52, 273, 32, 103, 275, 24, 57])}`);      // min(배열): 24
            console.log(`min(숫자, ...): ${min(52, 273, 32, 103, 275, 24, 57)}`);   // min(숫자, ...): 24
            ```

<br>

- 나머지 매개변수 > 일반 매개변수 조합
    - 나머지 매개변수는 끝에 있어야 함
        - ```javascript
            function sample(a, b, ...c) {
                console.log(a, b, c);
            }
            
            sample(1, 2);       // 1 2 []
            sample(1, 2, 3);    // 1 2 [ 3 ]
            sample(1, 2, 3, 4); // 1 2 [ 3, 4 ]
            ```

<br>

- 전개 연산자
    - ```javascript
        // 단순하게 매개변수를 모두 출력하는 함수
        function sample(...item) {
            console.log(items);
        }

        // 전개 연산자 사용 여부 비교하기
        const array = [1, 2, 3, 4];

        console.log('# 전개 연산자를 사용하지 않은 경우');
        sample(array);      // [ [ 1, 2, 3, 4 ] ]
        console.log('# 전개 연사자를 사용한 경우');
        sample(...array);   // [ 1, 2, 3, 4 ]
        ```

<br>

- ||나머지 매개변수 (rest)|전개 연산자 (spread)|
    |-|-|-|
    |역할|전달된 인자들을 배열로 묶음|배열이나 객체를 펼침|
    |사용 위치|함수의 매개변수 선언 시 마지막 인자로 사용|함수 호출 시, 배열이나 객체의 요소를 전달할 때 사용|
    |사용 예|function sum(...nums) {} (여러 인자를 배열로 받음)|Math.max(...arr) (배열을 개별 인자로 펼침)|
    |배열 반환 여부|여러 값을 하나의 배열로 묶음 ([1, 2, 3])|배열이나 객체를 개별 값으로 확장 (1, 2, 3)|

<br>

- 기본 매개변수
    - ```javascript
        function earnings(name, wage = 8590, hours = 40) {
            console.log(`# ${name} 님의 급여 정보`);
            console.log(`- 시급: ${wage}원`);
            console.log(`- 근무 시간: ${hours}시간`);
            console.log(`- 급여: ${wage * hours}원`);
            console.log('');
        }

        // 최저 입금으로 최대한 일하는 경우
        earnings('구름');

        // 시급 1만원으로 최대한 일하는 경우
        earnings('별', 10000);

        // 시급 1만원으로 52시간 일하는 경우
        earnins('인성', 10000, 52)
        ```

<br><br>

## 함수 고급

<br>

- 콜백 함수
    - ```javascript
        // 함수를 선언합니다.
        function callThreeTimes(callback) {
            for (let i = 0; i < 3; i++) {
                callback(i);
            }
        }

        function print(i) {
            console.log(`${i}번째 함수 호출`);
        }

        // 함수를 호출합니다.
        callThreeTimes(print);
        ```
    - ```javascript
        // 함수를 선언합니다.
        function callThreeTimes(callback) {
            for (let i = 0; i < 3; i++) {
                callback(i);
            }
        }

        // 함수를 호출합니다.
        callThreeTimes(function (i) {
            console.log(`${i}번째 함수 호출`);
        });
        ```

<br>

- 콜백 함수 활용
    - foreach()
        - ```javascript
            const numbers = [273, 52, 103, 32, 57];

            numbers.foreach(function (value, index, array) {
                console.log(`${index}번째 요소 : ${value}`);
            });

            // foreach(callbackfn)
            // - callbackfn
            //   - element    : 배열에서 처리 중인 현재 요소
            //   - index      : 배열에서 처리 중인 현재 요소의 인덱스
            //   - array      : foreach()를 호출한 배열
            ```
    - map()
        - ```javascript
            // 배열을 선언합니다.
            let numbers = [273, 52, 103, 32, 57];

            // 배열의 모든 값을 제곱합니다.
            numbers = numbers.map(function (value, index, array) {
                return value * value;
            });

            // arr.map(callback(currentValue[, index[, array]])[, thisArg])
            // - callback
            //   - currentValue   : 처리할 현재 요소
            //   - index          : 처리할 현재 요소의 인덱스
            //   - array          : map()을 호출한 배열

            // 출력합니다.
            numbers.forEach((value, index, array) => {
                console.log(`${value} ${index} ${array}`);
            });

            // 출력합니다.
            numbers.forEach(console.log);
            ```
    - filter()
        - ```javascript
            const numbers = [0, 1, 2, 3, 4, 5];
            const evenNumbers = numbers.filter(function (value) {
                return value % 2 === 0;
            });

            // filter(callbackFn)
            // - callback
            //   - element    : 배열에서 처리 중인 현재 요소
            //   - index      : 배열에서 처리 중인 현재 요소의 인덱스
            //   - array      : foreach()를 호출한 배열

            console.log(`원래 배열: ${numbers}`);       // 원래 배열: 0, 1, 2, 3, 4, 5
            console.log(`짝수만 추출: ${evenNumbers}`); // 짝수만 추출: 0, 2, 4
            ```

<br>

- 화살표 함수
    - ```javascript
        // 배열을 선언합니다.
        let numbers2 = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

        // 배열의 메소드를 연속적으로 사용합니다.
        numbers2
            .filter((value) => value % 2 === 0)
            .map((value) => value * value)
            .forEach((value) => {
                console.log(value);
            });
        ```

<br>

- 타이머 함수
    - ```javascript
        let id;
        let count = 0;
        id = setInterval(() => {
            console.log(`1초마다 실행됩니다(${count}번째)`);
            count++;
        }, 1 * 1000);

        setTimeout(() => {
            console.log('타이머를 종료합니다.');
            clearInterval(id);
        }, 5 * 1000);
        ```

<br><br>

## 객체 기본

<br>

- 배열도 객체임
    - ```javascript
        typeof([])  // 'obejct'
        ```

<br>

- 객체
    - ```javascript
        const product = {
            제품명: '7D 건조 망고',
            // ... 생략
        }

        product['제품명']   // '7D 건조 망고'
        ```

<br>

- 속성과 메소드
    - 메소드 내부에서 this 키워드 사용
        - ```javascript
            // 변수를 선언합니다.
            const pet = {
                name: '구름',
                eat: function (food) {
                    console.log(this.name + '은/는' + food + '을/를 먹습니다.');
                },

                // - 메소드 간단 선언 구문
                eat(food) {
                    console.log(this.name + '은/는' + food + '을/를 먹습니다.');
                },
            };

            // 메소드를 호출합니다.
            pet.eat('밥');  // 구름은/는 밥을/를 먹습니다.
            ```

<br>

- 동적으로 객체 속성 추가
    - ```javascript
        // 객체를 선언합니다.
        const student = {};
        student.이름 = '윤인성';
        student.취미 = '악기';
        student.장래희망 = '생명공학자';

        // - 동적으로 객체 속성 제거
        // 객체의 속성을 제거합니다.
        delete student.장래희망;

        // 출력합니다.
        console.log(JSON.stringify(student, null, 2));
        
        // JSON.stringify(value[, replacer[, space]])
        // - value      : JSON 문자열로 변환할 값
        // - replace    : JSON으로 변환할 때 특정 값이나 속성을 필터링하거나 수정할 수 있는 선택적인 매개변수
        // - space      : JSON 문자열에 들여쓰기를 추가

        //  JSON.parse(text[, reviver])
        // - text       : JSON으로 변환할 문자열
        ```

<br><br>

## 속성과 메소드

<br>

- 객체 자료형
    - ```javascript
        const a = []
        a.sample = 10
        a.sample    // 10

        // 함수도 객체이기 때문에 속성을 추가할 수 있음
        function b () { }
        b.sample = 10
        b.sample    // 10
        ```

<br>

- 기본 자료형
    - ```javascript
        // 기본형은 속성을 추가할 수 없음
        // 추가하고 싶으면 객체로 선언해야 됨
        const c = 273
        c.sample = 10
        c.sample    // undefined
        const d = '안녕하세요'
        d.sample = 10
        d.sample    // undefined
        const e = true
        e.sample = 10
        e.sample    // undefined

        // - 기본 자료형을 객체로 선언하기
        const f = new Number(273)
        f.sample = 10
        f.sample    // 10
        f           // Number {273, sample: 10}
        f + 0       // 273
        f.valueOf() // 273
        ```

<br>

- 프로토타입으로 메소드 추가하기
    - ```javascript
        // power() 메소드를 추가합니다.
        Number.prototype.power = function (n = 2) {
            return this.valueOf() ** n; // ** : 제곱
        };

        // Number 객체의 power() 메소드를 사용합니다.
        const a = 12;
        console.log('a.power():', a.power());   // a.power(): 144
        console.log('a.power(3):', a.power(3)); // a.power(3): 1728
        console.log('a.power(4):', a.power(4)); // a.power(4): 20736
        ```
    - ```javascript
        // contain() 메소드를 추가합니다.
        String.prototype.contain = function (data) {
            return this.indexOf(data) >= 0;
        }

        Array.prototype.contain = function (data) {
            return this.indexOf(data) >= 0;
        }

        // String 객체의 contain() 메소드를 사용합니다.
        const a2 = '안녕하세요';
        console.log('안녕 in 안녕하세요:', a.contain('안녕'));          // 안녕 in 안녕하세요: true
        console.log('없는데 in 안녕하세요', a.contain('없는데'));       // 없는데 in 안녕하세요: false

        // Array 객체의 contain() 메소드를 사용합니다.
        const b = [273, 32, 103, 57, 52];
        console.log('273 in [273, 32, 103, 57, 52]:', b.contain(273));  // 273 in [273, 32, 103, 57, 52]: true
        console.log('0 in [273, 32, 103, 57, 52]:', b.contain(0));      // 0 in [273, 32, 103, 57, 52]: false
        ```

<br>

- Number 객체
    - ```javascript
        const l = 123.456789
        l.toFixed(2)    // 123.45

        // numObj.toFixed([digits]);
        // - digits : 소수점 뒤에 나타날 자릿수
        ```

<br><br>

## 객체/배열 고급

<br>

- 속성 존재 여부 확인
    - ```javascript
        // 객체를 생성합니다.
        const obejct = {
            name: '혼자 공부하는 파이썬',
            // ... 생략
        };

        // 객체 내부에 속성이 있는지 확인합니다.
        if (obejct.name !== undefined) {
            console.log('name 속성이 있습니다.');
        } else {
            console.log('name 속성이 없습니다.');
        }
        ```

<br>

- 배열 기반의 다중 할당
    - ```javascript
        let [a, b] = [1, 2]
        console.log(a, b)       // 1 2

        [a, b] = [b, a]
        console.log(a, b)       // 2 1

        let arrayA = [1, 2, 3, 4, 5]
        const [c, d, e] = arrayA
        console.log(c, d, e)    // 1 2 3
        ```

<br>

- 객체 기반의 다중 할당
    - ```javascript
        // 객체를 생성합니다.
        const object = {
            title: '혼자 공부하는 파이썬',
            price: 18000,
            publisher: '한빛미디어',
        };

        // 객체에서 변수를 추출합니다.
        const { title, price } = object;
        console.log('# 속성 이름 그대로 꺼내서 출력하기');
        console.log(title, price);  // 혼자 공부하는 파이썬 18000

        const { a = title, b = price } = object;
        console.log('# 다른 이름으로 꺼내서 출력하기');
        console.log(a, b);          // 혼자 공부하는 파이썬 18000
        ```

<br>

- 배열 전개 연산자
    - ```javascript
        // 사야 하는 물건 목록
        const 물건_200301 = ['우유', '식빵'];
        const 물건_200302 = 물건_200301;
        물건_200302.push('고구마');
        물건_200302.push('토마토');

        // 출력
        console.log(물건_200301);   // [ '우유', '식빵', '고구마', '토마토' ]
        console.log(물건_200302);   // [ '우유', '식빵', '고구마', '토마토' ]

        // 메모리 주소를 복사했기 때문에 두배열에 추가됨
        ```
    - ```javascript
        // 사야 하는 물건 목록
        const 물건_200301 = ['우유', '식빵'];
        const 물건_200302 = [...물건_200301];
        물건_200302.push('고구마');
        물건_200302.push('토마토');

        // 출력
        console.log(물건_200301);   // [ '우유', '식빵' ]
        console.log(물건_200302);   // [ '우유', '식빵', '고구마', '토마토' ]

        // 요소만 복사됐기 때문에 한배열에만 추가됨
        ```

<br>

- 객체 전개 연산자
    - ```javascript
        const 구름 = {
            이름: '구름',
            나이: 6,
            종족: '강아지',
        };
        const 별 = {
            ...구름,
            이름: '별',
            나이: 1,
            예방접종: true,
        };

        console.log(JSON.stringify(구름));  // {"이름":"구름","나이":6,"종족":"강아지"}
        console.log(JSON.stringify(별));    // {"이름":"별","나이":1,"종족":"강아지","예방접종":true}
        ```
    - ```javascript
        const 구름 = {
            이름: '구름',
            나이: 6,
            종족: '강아지',
        };
        const 별 = {
            이름: '별',
            나이: 1,
            예방접종: true,
            ...구름,
        };

        console.log(JSON.stringify(구름));  // {"이름":"구름","나이":6,"종족":"강아지"}
        console.log(JSON.stringify(별));    // {"이름":"구름","나이":6,"예방접종":true,"종족":"강아지"}
        ```

<br><br>

## DOM 조작

<br>

- 문서 객체 조작
    - 요소[HTML 세계] = 문서 객체[자바스크립트 세계]

<br>

- 문서 객체 가져오기
    - ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Document</title>
            <script>
                document.addEventListener('DOMContentLoaded', () => {
                    // 요소를 읽어들입니다.
                    const headers = document.querySelectorAll('h1');

                    // 텍스트와 스타일을 변경합니다.
                    headers.forEach((header) => {
                        header.textContent = 'HEADERS';
                        header.style.color = 'white';
                        header.style.backgroundColor = 'black';
                        header.style.padding = '10px';
                    });
                });
            </script>
        </head>
        <body>
            <h1></h1>
            <h1></h1>
            <h1></h1>
            <h1></h1>
        </body>
        </html>
        ```

<br>

- 글자 조작하기
    - |textContent|innerHTML|
        |-|-|
        |순수 텍스트|HTML 파싱|

<br>

- 문서 객체 생성
    - ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Document</title>
            <script>
                document.addEventListener('DOMContentLoaded', () => {
                    // 문서 객체 생성하기
                    const header = document.createElement('h1');

                    // 생성한 태그 조작하기
                    header.textContent = '문서 객체 동적으로 생성하기';
                    header.setAttribute('data-custom', '사용자 정의 속성');
                    header.style.color = 'white';
                    header.style.backgroundColor = 'black';

                    // h1 태그를 body 태그 아래 추가하기
                    document.body.appendChild(header);
                });
            </script>
        </head>
        <body>
        </body>
        </html>
        ```

<br>

- 문서 객체 이동
    - ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Document</title>
            <script>
                document.addEventListener('DOMContentLoaded', () => {
                    // 문서 객체 읽어들이고 생성하기
                    const divA = document.querySelector('#first');
                    const divB = document.querySelector('#second');
                    const h1 = document.createElement('h1');
                    h1.textContent = '이동하는 h1 태그';

                    // 서로 번갈아가면서 실행하는 함수를 구현합니다.
                    const toFirst = () => {
                        divA.appendChild(h1);
                        setTimeout(toSecond, 1000);
                    };
                    const toSecond = () => {
                        divB.appendChild(h1);
                        setTimeout(toFirst, 10000);
                    }
                    toFirst();
                });
            </script>
        </head>
        <body>
            <div id="first">
                <h1>첫 번째 div 태그 내부</h1>
            </div>
            <div id="second">
                <h1>두 번째 div 태그 내부</h1>
            </div>
        </body>
        </html>
        ```

<br>

- 이벤트 설정하기
    - ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Document</title>
            <script>
                document.addEventListener('DOMContentLoaded', () => {
                    let counter = 0;
                    let isConnect = false;

                    const h1 = document.querySelector('h1');
                    const p = document.querySelector('p');
                    const connectButton = document.querySelector('#connect');
                    const disconnectButton = document.querySelector('#disconnect');

                    const listener = (event) => {
                        h1.textContent = `클릭 횟수: ${++counter}`;
                    };

                    connectButton.addEventListener('click', () => {
                        if (!isConnect) {
                            h1.addEventListener('click', listener);
                            p.textContent = '이벤트 연결 상태: 연결';
                            isConnect = true;
                        }
                    });
                    disconnectButton.addEventListener('click', () => {
                        if (isConnect === true) {
                            h1.removeEventListener('click', listener);
                            p.textContent = '이벤트 연결 상태: 해제';
                            isConnect = false;
                        }
                    });
                });
            </script>
            <style>
                h1 {
                    /* 클릭을 여러 번 했을 때
                    글자가 선택되는 것을 막기 위한 스타일 */
                    user-select: none;
                }
            </style>
        </head>
        <body>
            <h1>클릭 횟수: 0</h1>
            <button id="connect">이벤트 연결</button>
            <button id="disconnect">이벤트 제거</button>
            <p>이벤트 연결 상태: 해제</p>
        </body>
        </html>
        ```

<br><br>

## 이벤트 활용

<br>

- 키보드 이벤트
    - 키보드 키 코드 사용하기
        - ```html
            <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="UTF-8">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>Document</title>
                <script>
                    document.addEventListener('DOMContentLoaded', () => {
                        // 별의 초기 설정
                        const star = document.querySelector('h1');
                        star.style.position = 'absolute';

                        // 별의 이동을 출력하는 기능
                        let [x, y] = [0, 0];
                        const block = 28;
                        const print = () => {
                            star.style.left = `${x * block}px`;
                            star.style.top = `${y * block}px`;
                        };
                        print();

                        // 별을 이동하는 기능
                        const [left, up, right, down] = [37, 38, 39, 40];
                        document.body.addEventListener('keydown', (event) => {
                            switch (event.keyCode) {
                                case left:
                                    x -= 1;
                                    break;
                                case up:
                                    y -= 1;
                                    break;
                                case right:
                                    x += 1;
                                    break;
                                case down:
                                    y += 1;
                                    break;
                            }
                            print();
                        });
                    });
                </script>
            </head>
            <body>
                <h1>*</h1>
            </body>
            </html>
            ```

<br>

- 글자 입력 양식 이벤트
    - 라디오 버튼 활용
        - 라디오 버튼의 name 속성이 같아야 같은 그룹

<br>

- 기본 이벤트 막기
    - |event.preventDefault()|event.stopPropagation()|
        |-|-|
        |기본 동작 방지|이벤트 전파 방지|
        |특정 이벤트에 대한 기본 동작을 차단|이벤트가 더 이상 상위 요소로 전달되지 않음|
    - [버블링과 캡처링](https://ko.javascript.info/bubbling-and-capturing#ref-892)

<br><br>

## 구문 오류와 예외

<br>

- 오류의 종류
    - 구문 오류
    - 예외
        - 실행될 때 발생하는 것
    - ```javascript
        // 구문 오류가 발생하는 부분
        console.log('괄호를 닫지 않는 실수를 했습니다.'

        // 예외가 발생하는 부분
        console.rog('log를 rog로 적는 실수를 했습니다.');
        ```

<br><br>

## 예외 처리 고급

<br>

- 예외 객체
    - ```javascript
        try {
            const array = new Array(999999999999999);
        } catch (exception) {
            console.log(exception);
            console.log(`예외 이름: ${exception.name}`);
            console.log(`예외 메시지: ${exception.message}`);
        }
        ```

<br>

- 예외 강제 발생
    - ```javascript
        function divide(a, b) {
            if (b === 0) {
                throw '0으로는 나눌 수 없습니다.';
            }
            return a / b;
        }

        console.log(divide(10, 0)); // 0으로는 나눌 수 없습니다.
        ```
    - ```javascript
        function test(object) {
            if (object.a !== undefined && obejct.b !== undefined) {
                console.log(object.a + object.b);
            } else {
                throw new Error('a 속성과 b 속성을 지정하지 않았습니다.');
            }
        }

        test({});
        ```

<br><br>

## 클래스 기본 기능

<br>

- 같은 형태의 객체 만들기
- 객체를 처리하는 함수
- 객체의 기능을 메소드로 추가하기
    - ```javascript
        function createStudent(이름, 국어, 영어, 수학, 과학) {
            return {
                // 속성을 선언합니다.
                이름: 이름,
                국어: 국어,
                영어: 영어,
                수학: 수학,
                과학: 과학,
                // 메소드를 선언합니다.
                getSum() {
                    return this.국어 + this.영어 + this.수학 + this.과학;
                },
                getAverage() {
                    return this.getSum() / 4;
                },
                toString() {
                    return `${this.이름}\t${this.getSum()}점\t${this.getAverage()}점\n`;
                },
            };
        }

        // 객체를 선언합니다.
        const students = [];
        students.push(createStudent('구름', 87, 98, 88, 90));
        students.push(createStudent('별이', 92, 98, 96, 88));

        // 출력합니다.
        let output = '이름\t총점\t평균\n';
        for (const s of students) {
            output += s.toString();
        }
        console.log(output);
        ```

<br>

- 클래스 선언하기
- 생성자
- 메소드
    - ```javascript
        // 클래스를 선언합니다.
        class Student {
            constructor(이름, 국어, 영어, 수학, 과학) {
                this.이름 = 이름;
                this.국어 = 국어;
                this.영어 = 영어;
                this.수학 = 수학;
                this.과학 = 과학;
            }

            getSum() {
                return this.국어 + this.영어 + this.수학 + this.과학;
            }
            getAverage() {
                return this.getSum() / 4;
            }
            toString() {
                return `${this.이름}\t${this.getSum()}점\t${this.getAverage()}점\n`;
            }
        }

        // 객체를 선언합니다.
        const students = [];
        students.push(new Student('구름', 87, 98, 88, 90));
        students.push(new Student('별이', 92, 98, 96, 88));

        // 출력합니다.
        let output = '이름\t총점\t평균\n';
        for (const s of students) {
            output += s.toString();
        }
        console.log(output);
        ```

<br><br>

## 고급 기능

<br>

- 상속
    - ```javascript
        // 사각형 클래스
        class Rectangle {
            constructor(width, height) {
                this.width = width;
                this.height = height;
            }

            // 사각형의 둘레를 구하는 메소드
            getPerimeter() {
                return 2 * (this.width + this.height);
            }

            // 사각형의 넓이를 구하는 메소드
            getArea() {
                return this.width * this.height;
            }
        }

        // 정사각형 클래스
        class Square extends Rectangle {
            constructor(length) {
                super(length, length);
            }
        }

        // 클래스 사용하기
        const square = new square(10, 20);
        console.log(`정사각형의 둘레: ${square.getPerimeter()}`);   // 정사각형의 둘레: 40
        console.log(`정사각형의 넓이: ${square.getArea()}`);        // 정사각형의 넓이: 100
        ```

<br>

- private 속성과 메소드
    - ```javascript
        // 정사각형 클래스
        class Square {
            #length;            // private

            // ... 생략
        }

        // 클래스 사용하기
        const square = new Square(10);
        square.#length = -10;   // 오류 발생
        // SyntaxError: Private field '#length' must be declared in an enclosing class
        ```

<br>

- getter / setter
    - ```javascript
        // 정사각형 클래스
        class Square {
            #length;

            // ... 생략

            get length() {
                return this.#length;
            }

            // ... 생략

            set length(length) {
                if (length <= 0) {
                    throw '길이는 0보다 커야 합니다.';
                }
                this.#length = length;
            }

            // 값을 넣지 않고 호출하면 get 함수가 호출되고
            // 값을 넣고 호출하면 set 함수가 호출됨
        }
        ```
