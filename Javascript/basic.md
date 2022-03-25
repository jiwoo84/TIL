# Basic

[→ Open in Slid](https://slid.cc/docs/26ad00c849fe490da9cb94bb82907b25)

---

### javascript

- frontend 에서 사용하는 유일한 언어
- 프로그래밍 언어인 이유
    
    ‘프로그램’의 어원은 시간 순서와 연관이 깊다.
    
    자바스크립트는 시간 순서대로 진행되므로 프로그래밍 언어이다.
    
    하지만 html은 화면의 묘사하는 정적인 언어이며, 시간 순서대로 실행되지 않기 때문에 프로그래밍 언어가 아니다.
    

### 라이브러리

프로그램에 필요한 부품이 되는 소프트웨어가 정리되어 있는 것

- 사용법
    
    다운로드 or CDN 카피 → HEAD에 붙여넣기
    

### 프레임워크

만들고자 하는 프로그램의 종류에 따라서 공통적인 부분을 미리 만들어놓는 것. 필요한 부분만 약간 수정해서 사용 가능

### 이외

- **리액트 네이티브**
    
    자바스크립트 만으로 안드로이드 ios 앱 만듬
    
- **일렉트론**
    
    js, html, css로 데스트탑 앱을 만듬
    

### UI (User Interface)

사용자들이 시스템을 제어하기 위해서 조작하는 장치

### API (Application Programming Interface)

프로그래머들이 사용하는 조작 장치

ex) `alert “hello world”` 도 alertAPI를 사용한 것

## 변수 이름 작성법

- 띄어쓰기 하는 부분 - 대문자
    
    ```jsx
    const veryLongVariableName = 0;
    ```
    
    - 함수 이름에 자주 사용되는 접두어
        - `“show...”` - 무언가를 보여줌
        - `"get…"` – 값을 반환함
        - `"calc…"` – 무언가를 계산함
        - `"create…"` – 무언가를 생성함
        - `"check…"` – 무언가를 확인하고 불린값을 반환함
        
- string만 포함된 변수- 전체 대문자
    
    ```jsx
    const HIDDEN_CLASSNAME = "hidden";
    ```
    

## 자투리

- `alert()` : 알림·경고창 띄움
    - 뜬 순간 브라우저의 모든 행위를 멈춤
    - 값을 반환 X ( `undefined` 반환)
    - 거의 모든 값을 인자로 받을 수 있음
        
        (js에서 문자형으로의 암시적 형 변환 해주기 때문 - symbol 제외)
        
    
- `console.log()` : 콘솔에 내용 출력 /  `log`가 메소드라서 `,`으로도 string 연결 가능

- `console.dir()` : element까지 자세히 보여줌
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/00ca200e-d4bb-44bd-abd8-2eccea361b14.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/00ca200e-d4bb-44bd-abd8-2eccea361b14.png)
    

- `element.remove()` : element 삭제
- 공백 금지에 공백 넣기: [”~ ~”]
- `element.id = id-name` : html 상의 element에 id 넣기

# html - js 연결

### html 안에 js작성

`<script> ~ </script>` script 태그 안에 명령 작성

### 따로 파일 생성

body 속 맨 밑에 `<script scr="파일명.js"></script>` 작성

# Data type

## 원시형

1. **integer** : 숫자 (2)

1. **float :** 소수점 숫자 (1.5)
    
    
    - 숫자 간단 입력
        - 숫자 + e + n (0의 개수) → 숫자 x 10의 n제곱
            
            ex) `7e5` = 700,000
            
        - 숫자 + e + -n (1/10xn) → 숫자에서 n만큼 왼쪽으로 소수점 이동
            
            ex) `1.2e-6` = 0.0000012
            
        - billion(10억) : 1bn = 1e9
        - 16진수 : 0x진수숫자  ex) `0xff` = 255 (f=15)
            
            2진수: 0b진수숫자  ex) `0b111` = 7
            
            8진수: 0o진수숫자
            

1. **string :** 문자, 따옴표 안 `“string”`  `‘string’`
    
    
    - **문자열 합치기**
        - `“string” + “string” +2` = “stringstring2”
        
        - 구버전
            
            `"string " + var-name` = “string var값”
            
        
        - 신버전 (템플릿 리터럴 방식 template literal)
            
            ``string ${var-name}`` = “string var값”
            
            ``string ${var-name} string`` = “string var값 string”
            
            ```jsx
            const username = jiwoo;
            
            "hello" + username;
            `hello ${username}`; // 둘의 값은 같다
            
            let jiwoo = `water
            	* sleep
            	* working 
            	` // 여러줄로도 작성 가능
            ```
            
        
2. **Symbol**
    
    `Symbol()`  /  `Symbol("name")` (S는 대문자)
    
    - 유일성이 보장되는 자료형 → 심볼명이 같아도 다른 심볼
    - 다른 자료형으로 자동 형 변환 X
        
        ex) `alert(symbol("name"))`하면 오류남
        
        이유: alert하면 js 차원에서 인자를 형 변환하는데 symbol은 불가
        

1. **null**
    - 텅빈 상태가 아니고 ’없음’으로 채워진 상태
    - 절대 자연적으로 발생x, 안에 없다는 것을 확실히 하려고 사용
    - 호출 결과가 `null`인 경우, 에러 발생 (`undefined`는 에러x)
    
2. **undefined**
    - 값이 설정되지 않음 (텅빈 상태)
    - 정의되지 않음
    
    ```jsx
    const a = null;
    const b;
    
    console.log(a,b); // = null, undefined
    ```
    
- **NaN** : (Not a Number) 숫자가 아님
    - 데이터 타입이 아닌, 전역 객체의 속성
    - 비교연산자에서 NaN이 피연산자인 경우 항상 false 반환
    - `NaN === NaN;` // false
    

## data type 변경

- `type(value)`  :  value의 type 변경 후, 반환
    
    
    - number(~)
        - `number(null)` = 0
        - `number(undefined)` = NaN
        - `number("  2/n")` =  2  (공백 무시됨)
        
- `toString()` : string으로 변경 후, 반환
    - `num.toString(n)` = n진법으로 num 표현
    
- **parseInt**
    
    `parseInt(~)` string → number로 변환 후, 반환
    
    `parseInt(str, radix)`  radix로 진수를 지정해줄 수도 있음
    
    ```jsx
    const age = parseInt(promt("How old are you?"));
    
    // 두 개의 fnc 사용해서 입력값 받고 num로 type 변경
    ```
    
    - 특징
        - 값의 크기비교 가능 (숫자로 바꾸기 때문)
        - 숫자 아닌 입력값 인지 (**NaN**으로 뜸)
        
    - `number(~)` 와의 차이점
        
        
        - parseInt는 숫자를 찾아내서 반환하는 기능이 있음
            
            (숫자 아닌 형태 발견하면 이미 읽은 숫자까지만 반환)
            
            ex) `parseInt("10회")` = 10
            
            `number("10회")` = NaN
            
            `parseInt("제10회")`  = NaN
            
        - parseInt는 정수만 반환
            
            ex) `parseInt("2.55")` = 2
            
            `number("2.55")` = 2.55
            
            `parseFloat("2.55")` = 2.55  (소수는 parseFloat 사용)
            
        - 입력받는 값을 정수로만 받고 싶다면 앞에 +붙이기
            
            `let number = **+**prompt("숫자 입력","");`
            

## typeof

값의 data type 알아내 반환

- **생성**
    
    `typeof val`
    
    `typeof(val)`  둘 다 가능
    
    ```jsx
    console.log(typeof 1); // "number" 
    console.log(typeof "jw"); // "string"
    ```
    

- **결과값**
    - prompt 같은 입력값은 string이 기본값
        
        → 숫자로 바꾸려면 parseInt() 사용
        
        ![숫자 입력](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/f6431f2b-dce9-4b41-861e-8cc029706cc8.png)
        
        숫자 입력
        
        ![숫자도 string](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/c6128537-87af-4176-9238-08bb5253694c.png)
        
        숫자도 string
        
    
    - `typeof {}` = `typeof []` = object
        
        객체와 배열은 둘 다 객체형에 속함
        
        ∴ 배열은 `arr.isArray()` 로 배열 여부 판별할 것
        
    - 예외
        - `typeof null == "object"` 언어 자체의 오류
        - `typeof function(){} == "function"` 함수는 특별하게 취급됩니다.

## isNaN

NaN(숫자가 아님)을 판별 후, boolean 반환

- NaN은 자신을 포함하여 어떤 값과도 같지 않음
    
    ex) `NaN === NaN` ⇒ false  
    
    그래서 그 자체로 비교하면 안되고 함수가 필요함 → `isNaN`
    

- **생성**
    
    `isNaN(val)` = boolean
    
    - isNaN(number) → **false**
    - isNaN(number X) → **true**
    
    ```jsx
    const age = parseInt(promt("How old are you?"));
    
    console.log(isNaN(age));
    // 입력값에 따라 true or false 뱉어냄
    ```
    
- **주의사항**
    
    초기 버전 함수로 혼란스러운 경우가 있음 (isFinite를 사용할 것)
    
    `isNaN("")`  ⇒ false
    
    `isNaN(null)`  ⇒ false
    
    `isNaN(undefined)`  ⇒ true
    

## isFinite

인수를 숫자로 변환 후, 변환한 숫자가 `NaN/Infinity/-Infinity`
가 아닌 일반 숫자인 경우 `true`를 반환

```jsx
alert( isFinite("15") ); // true
alert( isFinite("str") ); // false, NaN이기 때문입니다.
alert( isFinite(Infinity) ); // false, Infinity이기 때문입니다.
alert( isFinite("") ); // true, 빈 문자열이나 공백은 0으로 취급
```

# 문자열

- `/n`  줄바꿈
- 중간에 따옴표 넣기 : `alert('i\'m jw')` / `alert(`i’m jw`)`
    
    (역슬레시 활용, 하지만 후자를 추천)
    
- `str.length`  (프로퍼티) 문자열 길이 반환
- `str.trim()`  문자열 앞·끝 공백 제거
- `str.repeat(n)` 문자열 n번 반복

## 특정 문자에 접근하기

n번째 문자열 얻기

1. `str[n]`  대괄호 이용
2. `str.charAt(n)` 메서드 호출

```jsx
let str = `coffee`;

// 첫 번째 글자
alert( str[0] ); // c
alert( str.charAt(0) ); // c

// 마지막 글자
alert( str[str.length - 1] ); // e
```

- 차이점
    
    접근하려는 위치에 문자가 없는 경우
    
    str[n] ⇒ `undefined`  /  str.charAt(n) ⇒ `""`  반환
    
- 이 방식으로 문자열 수정 불가
    
    → 완전히 새로운 문자열을 만들고, 그것을 할당해야함
    
    ```jsx
    let str = 'Hi';
    
    str = 'h' + str[1]; // 문자열 전체를 교체함
    
    alert( str ); // hi
    ```
    

## 부분 문자열 찾기

1. **문자열 위치 찾기**
    
    `str.indexOf(substr, pos)` (pos 생략 가능)
    

(문자열 str의 pos에서부터 시작해) 부분 문자열 substr이 어디에 위치하는지를 찾아서 위치 반환, 발견 못하면 -1 반환

- 대소문자 구별함
- 요소 검색시, `===` 를 사용하기 때문에 NaN 찾지 못함
    
    (`NaN === NaN`  ⇒ false)
    
- 배열도 사용 가능
    
    `arr.indexOf(item, from)` 
    
    인덱스 from부터 시작해 item(요소) 찾고 발견 시 해당 요소의 인덱스 반환, 못하면 -1 반환 (lastIndex도)
    
- 역순으로 검색 : `str.lastIndexOf(substr, pos)`

```jsx
let str = 'Widget with id';

alert( str.indexOf('Widget') ); // 0, str은 'Widget'으로 시작함
alert( str.indexOf('widget') ); // -1, indexOf는 대·소문자를 따지므로 원하는 문자열을 찾지 못함

alert( str.indexOf("id") ); // 1, "id"는 첫 번째 위치에서 발견됨 (Widget에서 id)
```

1. **문자열 포함 여부**
    
    `str.includes(substr, pos)` ****(pos 생략 가능)
    
    str 안에 부분 문자열 substr 포함 여부 boolean 반환
    
    - 대소문자 구별함
    - `indexOf` 와 똑같이 검색 시 `===` 사용하지만, NaN를 제대로 찾을 수 있음
    - 배열도 사용 가능 `arr.includes(item,from)`

1. **문자열 시작/끝 여부**
    - `str.starsWith(substr)`
        
        str이 해당 문자열로  시작하는지 여부 boolean 반환
        
    - `str.endsWith(substr)`
        
        str이 해당 문자열로  끝나는지 여부 boolean 반환
        

1. **부분 문자열 추출**
    
    
    | 메서드 | 추출할 부분 문자열 | 음수 허용 여부
    (인수) |
    | --- | --- | --- |
    | slice(start, end) | start부터 end까지
    (end는 미포함) | 음수 허용 |
    | substring(start, end) | start부터 end까지
    (start > end 가능) | 음수는 0으로 취급 |
    | substr(start, length) | start부터 length개의 글자 | 음수 허용 |
    
    - `**str.slice**`
        
        
        - `str.slice(start, end)`
            
            문자열의 start부터 end까지 반환 (end부분 미포함)
            
        - `str.slice(start)`
            
            문자열의 start부터 끝까지
            
        - `str.slice(-start, -end)`
            
            음수라면 끝에서부터 카운팅 시작 (-0이 아니라 -1부터 셈)
            
        
        ```jsx
        let str = "stringify";
        
        alert( str.slice(0, 5) ); // 'strin'
        alert( str.slice(0, 1) ); // 's'
        alert( str.slice(2) ); // 'ringify', 2번째부터 끝까지
        alert( str.slice(-4, -1) ); // 'gif'
        alert( str.slice(-0) ); // 'stringify'
        
        ```
        
    - **`str.substring(start, end)`**
        
        문자열의 start부터 end까지 반환
        
        - `str.slice`와 차이점
            - start가 end 보다 커도 됨
            - 음수 인수 허용X (0으로 처리)
        
        ```jsx
        let str = "stringify";
        alert( str.substring(2, 6) ); // "ring"
        alert( str.slice(2, 6) ); // "ring" 같은 결과
        alert( str.substring(6, 2) ); // "ring"
        alert( str.substring(-1, -4) ); // "" 빈 string 아무것도 반환x
        
        // slice 는 start > end 불가
        alert( str.slice(6, 2) ); // "" (빈 문자열)
        ```
        
    - `**str.substr(start, length)**`
        
        start에서부터 시작해 length개의 글자를 반환
        
        - 음수면 뒤에서부터 카운팅
        
        ```jsx
        let str = "stringify";
        alert( str.substr(2, 4) ); // "ring"
        alert( str.substr(-4, 2) ); // gi, 끝에서 네 번째 위치부터 글자 두 개
        ```
        

## 대·소문자 변경

1. `toLowerCase()`  대문자 → 소문자
2. `toUpperCase()`  소문자 → 대문자

- 문자 하나만 변경하는 것도 가능
    
    `alert(‘cake’[0].toUpperCase())`  // ‘C'  
    

## 문자열끼리 비교

- 유니코드를 베이스로 글자가 숫자 코드와 매칭됨
- 같은 형태일 경우, 사전순(Alphabetically)으로 비교됨
    
    (사전편집(elxciographical) 순이라고도 불림)
    
    ex)  `'a' < 'b'`
    
    `‘15’ < ‘2’`  사전순이므로 앞자리 먼저 보고 판단
    
- 이외의 경우
    - 소문자 > 대문자
    - 발음 구별 기호가 붙은 문자는 알파벳 순서 기준을 따르지 않음
    
- `**str.codePointAt(n)**`
    
    str의 n에 위치한 문자의 코드를 반환
    
    ```jsx
    alert( "z".codePointAt(0) ); // 122
    alert( "Z".codePointAt(0) ); // 90
    ```
    

- **`String.fromCodePoint(code)`**
    
    숫자 형식의 `code`에 대응하는 글자를 만들어줍니다.
    
    ```jsx
    alert( String.fromCodePoint(90) ); // Z
    ```
    

# boolean

(text 아닌 data type)

- **true**
    - truthly
        
        falsey 외의 모든 값 
        

- **false**
    - falsy (거짓같은 값 / boolean 문맥에서 false로 평가됨)
        - false
        - 0 / -0
        - 0n
        - “ ” (빈 string)
        - null
        - undefined
        - NaN

# 연산자

## 산술 연산자

숫자형의 피연산자만 다루고, 숫자형이 아니면 숫자로 변환 (+만 빼고)

- `%` : (`a%b`) a를 b로 나눈 나머지를 정수로 반환
- `**` : 거듭제곱

- `+` : 기본 산술 연산자 / 문자열 연결
    - 피연산자 중 하나가 문자열이면 다른 하나도 문자열로 변환
        
        ex) `alert('1' + 2)`  =  “12”
        
        `alert(2 + 2 + '1')`  =  “41” (연산이 왼→오로 진행되기 때문에, 숫자가 먼저 더해지고 `‘1’`에 의해 string으로 변환되어 `“41”` 완성)
        
        `alert('2' - 1)`  =  1  (+ 빼고 다른 연산자는 숫자 아니면 숫자로 변환)
        
    - `++` / `--` (증감연산자)
        
        피연산자를 1씩 증가 혹은 1씩 감소시킬 때 사용
        
        - `++i` : i+1 먼저 실행
        - `i++` : 다음 줄로 넘어갈 때 i+1 실행
        
    - `+=` (더하기 할당 연산자) : 오른쪽 피연산자의 값을 변수에 더한 결과를 다시 변수에 할당
    
    - `int i = 0;`
        
        `i = i + 1`  ==  `i+= 1`  == `i++`
        
        셋 다 같은 의미
        

## 논리 연산자

1.  **`&&`** : and
    - 모두 true = `true`
    - 하나라도 false = `false`
    - 피연산자가 boolean 아닌 경우 (원래값 반환)
        
        첫 번째 falsy 반환 / (하나도 없다면) 마지막 피연산자
        
    
    ```jsx
    if (age>=18 && age<=50) {명령문};
    
    // 18≤ age ≤50 일 때, 실행 
    ```
    
2.  **`||`** : or
    
    하나라도 true = `true`
    
    - 피연산자가 boolean 아닌 경우 (원래값 반환)
        
        첫 번째 truthy 반환 / (하나도 없다면) 마지막 피연산자
        
    
    ```jsx
    if (isNaN(age) || age < 0) {명령문};
    
    // age가 숫자가 아니거나 or 음수 일 때, 실행
    ```
    

1. `!` : NOT
    
    피연산자를 불린형으로 변환 → 변환된 값의 역을 반환
    
    ```jsx
    alert( !true ); // false
    alert( !0 ); // true
    ```
    
    - 연달아 사용하면 boolean형으로 변환 가능
        
        ```jsx
        alert( !!"non-empty string" ); // true
        alert( !!null ); // false
        ```
        
        `Boolean(~)` 와 같은 결과 도출
        
2. **nullish 병합 연산자 : `??`**
    
    `a ?? b`
    
    - `a`가 `null`도 아니고 `undefined`도 아니면 `a`그 외의 경우는 `b`
    - 여러 피연산자 중 값이 ‘확정 되어있는’ 변수 찾기
    
    ```jsx
    a = null;
    b = "namjun";
    
    const name = a ?? b;
    alert(name);  // "namjun" 출력
    ```
    

## 비교 연산자 **(AND/OR operator)**

`**===**` : ‘같음’ 확인 기호

```jsx
if (age ===100) {명령문}
else (age<100) {명령문};

// age=100 아니라면 아래로 내려감
```

`**!==**` : ‘다름’ 확인 기호 (~가 아니라면 실행)

- `===` & `==` & `=` 차이점
    
    
    - `===` : 값 + data type 비교
    - `==` : 값만 비교 (binaryCode로 비교)
    - `=` : value 할당 (’같음’ 비교 기호 아님)
    
    - 예시
        
        `0 === false` → false (false의 type은 boolean이므로)
        
        `0 == false` → true (false는 이진법으로 0 표기)
        
    
    - **특별 케이스**
        
        ∴ 피연산자에 undefined나 null이 오지 않게 주의할 것
        
        - undefined 와 null 비교
            
            ```jsx
            alert(undefined == null) // true
            alert(undefined === null) // false
            ```
            
            - 동등연산자`==`로 비교하면 특별한 규칙이 적용되어 true가 반환
            - 하지만 `===`로 더 엄격하게 비교하면 false
            
        - 피연산자가 undefined 나 null 일 때, 형변환 X
            
            (<, >, ≤, ≥ 는 숫자형으로 변환)
            
            ```jsx
            alert( null == 0 ); // false
            alert( null > 0 );  // false
            alert( null >= 0 ); // true
            // number(null) = 0 이므로 위 결과 나옴
            ```
            
        
- `object.is`
    
    값을 비교할 때 사용하는 내장 메서드
    
    - `===` 와 다른 결과를 반환하는 경우
        1. NaN을 대상으로 비교할 때: 
            
            `Object.is(NaN, NaN) === true`
            
        2. 0과 0이 다르게 취급되어야 할 때: 
            
            `Object.is(0, -0) === false`
            
            (숫자를 나타내는 비트가 모두 0이더라도 부호를 나타내는 비트는 다르므로)
            

# variable

|  | 재선언 | 재할당 |
| --- | --- | --- |
| const | X | X |
| let | X | O |
| var | O | O |

## **1. const (상수)**

`const name = 값;`

- 값 절대 변경 불가 (변경하려면 let 사용)
    
    

## **2. let (변수)**

`let name = 값;`

- 값 변경
    
    (let 생략 필수)  `name = 값;`
    
    ```jsx
    let myName = "jiwoo";
    myName = "jw";
    
    console.log(myName); // 결과값: jw
    ```
    

## **주의사항**

- 변수 이름
    - number, string 사용 (첫글자에 num 사용불가)
    - 특수기호는 `&`, `_` 만 사용 가능
    
- 기본적으로 const , 필요에 따라 let 사용
    
    const/ let 에 따라 코드 사용의 의도 알 수 있음
    
- var은 거의 사용x
    
    (var은 구버전, 업데이트 무제한 가능해서 오류 가능성 높아짐)
    
- 변수는 값을 복사하는 것 (문자 그대로를 복사x)
    
    ```jsx
    let name = "rap monster";
    const hisName = name;  // hisName에는 "rap monster" 복사
    name = "rm";  // hisName은 변경x
    
    console.log(hisName); // 결과값: rap monster
    ```
    

# array

데이터를 순서대로 정리한 데이터 리스트

숫자형 키를 사용해서 순서가 있게 한 특별한 객체

## 요약

- **요소를 더하거나 지우기**
    - `push(...items)` – 맨 끝에 요소 추가하기
    - `pop()` – 맨 끝 요소 추출하기
    - `shift()` – 첫 요소 추출하기
    - `unshift(...items)` – 맨 앞에 요소 추가하기
    - `splice(pos, deleteCount, ...items)` – `pos`부터 `deleteCount`개의 요소를 지우고, `items` 추가하기
    
- **새로운 배열 만들기**
    - `slice(start, end)` – `start`부터 `end` 바로 앞까지의 요소를 복사해 새로운 배열을 만듦
    - `concat(arg1, arg2..)` – 배열의 모든 요소를 복사하고 `arg`를 추가해 새로운 배열을 만든 후 이를 반환함. `items`가 배열이면 이 배열의 인수를 기존 배열에 더해줌
    
- **원하는 요소 찾기**
    - `indexOf/lastIndexOf(item, pos)` - `pos`부터 원하는 `item`을 찾음. 찾게 되면 해당 요소의 인덱스를, 아니면 `-1`을 반환함
    - `includes(value)` - 배열에 `value`가 있으면 `true`를, 그렇지 않으면 `false`를 반환함
    - `find/filter(func)` – `func`의 반환 값을 `true`로 만드는 첫 번째/전체 요소를 반환함
    - `findIndex`는 `find`와 유사함. 다만 요소 대신 인덱스를 반환함
    
- **배열 전체 순회하기**
    - `forEach(func)` – 모든 요소에 `func`을 호출함. 결과는 반환되지 않음(undefined)
    - `for…of(func)` - 모든 요소에 func 호출. return 사용 가능
    
- **배열 변형하기**
    - `map(func)` – 모든 요소에 `func`을 호출하고, 반환된 결과를 가지고 새로운 배열을 만듦
    - `sort(func)` – 배열을 정렬하고 정렬된 배열을 반환함
    - `reverse()` – 배열을 뒤집어 반환함
    - `split/join` – 문자열을 배열로, 배열을 문자열로 변환함
    - `reduce(func, initial)` – 요소를 차례로 돌면서 `func`을 호출함. 반환값은 다음 함수 호출에 전달함. 최종적으로 하나의 값이 도출됨
    
- 기타
    - `Array.isArray(arr)` – `arr`이 배열인지 여부를 판단함
    

`sort`, `reverse`, `splice`는 기존 배열을 변형시킨다는 점에 주의하시기 바랍니다.

## 입출력

- **선언**
    
    `var arr-name = [~, ~, ~]`
    
    `var arr-name = new Array()` (잘 사용x)
    
    배열 요소의 자료형은 제약 없음 (다 가능)
    
    ```jsx
    // 요소에 여러 가지 자료형이 섞여 있습니다.
    let arr = [ '사과', { name: '이보라' }, true, function() { alert('안녕하세요.'); } ];
    
    // 인덱스가 1인 요소(객체)의 name 프로퍼티를 출력합니다.
    alert( arr[1].name ); // 이보라
    
    // 인덱스가 3인 요소(함수)를 실행합니다.
    arr[3](); // 안녕하세요.
    ```
    

- 출력
    
    `array[n]` (array 중 n번째 값)
    
    인덱스는 0부터 세기 시작한다
    

## **요소를 더하거나 지우기**

- **추가**
    - `array.push()` : 맨 끝에 값 추가
    - `arry.unshift()` : 맨 앞에 값 추가
    - `array[n] = ~;` : 원하는 위치에 값 변경/추가
    
- **제거**
    - `array.pop()` 마지막 요소 제거
    - `array.shift()` 첫번째 요소 제거
    - `delete array[n]` 요소값만 제거
        
        값만 제거하기 때문에 자리는 남아있음
        
        ```jsx
        let arr = ["I", "go", "home"];
        
        delete arr[1]; // "go"를 삭제합니다.
        
        alert( arr[1] ); // undefined
        
        // delete를 써서 요소를 지우고 난 후 배열 --> arr = ["I",  , "home"];
        alert( arr.length ); // 3
        ```
        
    
    - `**splice`** 지정 요소 제거
        
        `array.splice(시작위치 [,제거건수[,추가요소]])`
        
        시작 인덱스부터 제거건수만큼 제거 → 추가요소 추가
        
        - 위치에 음수 인덱스 사용 가능 (맨 뒤에서 첫번째 = `-1`)
        - `array.splice(시작위치,0,추가요소)`
            
            ⇒ 삭제 X , 해당 인덱스 위치에 요소 추가
            
        - 반환값: 제거한 요소를 담은 배열
            
            ```jsx
            let arr = ['a', 'b', 'c', 'd']
            
            arr.splice(2, 1); // index 2 부터 1개의 요소('c')를 제거
            // arr = ['a', 'b', 'd']
            
            arr.splice(1, 0, 'z'); // 제거 안하고 중간에 추가 가능
            // arr = ['a', 'z', 'b', 'd']
            
            alert(arr.splice(1,2));
            // 'z,b' 출력
            
            ```
            

- 자료구조
    - 큐 : 선입선출(First-In-First-Out, FIFO)
    - 스택 : 후입선출(Last-In-First-Out, LIFO)
    - `shift`/ `unshift` 가 `pop` / `push` 보다 느림
        
        ⇒ 앞 요소 제거/추가 후 앞으로 요소 이동해야하기 때문)
        

## 새로운 배열 만들기

- **slice**
    
    `arr.slice([start [, end]])`
    
    start인덱스부터 end인덱스까지의 요소를 복사한 새로운 배열 반환 (end 제외)
    
    ```jsx
    let arr = ["t", "e", "s", "t"];
    
    arr.slice(1, 3); // ["e", "s"]
    
    arr.slice(-2); // ["s", "t"]
    
    arr.slice(); // ["t", "e", "s", "t"]
    ```
    

- **concat**
    
    `arr.concat([arg1[, arg2[, ...]]])`
    
    배열 맨 끝에 새 요소를 추가 → 새로운 배열 반환
    
    (arg에는 값, 배열, 객체 가능 / 개수 제한 X)
    
    - arg = 배열
        
        배열의 모든 요소가 복사·추가
        
        (배열 아닌 단순 값인 경우도 마찬가지)
        
        ```jsx
        let arr = [1, 2];
        
        console.log( arr.concat(3, 4) ); // [1,2,3,4]
        console.log( arr.concat([3, 4]) ); // [1,2,3,4] 위 값과 같음
        console.log( arr.concat([3, 4], 5, 6) ); // [1,2,3,4,5,6]
        ```
        
    
    - arg - 객체
        
        분해되지 않고 통으로 복사·추가
        
        (특수한 prop - symbol 있으면 객체를 배열로 취급해서 객체 전체가 아닌 값만 더해짐 완벽 이해는 못함)
        
        ```jsx
        let arr = [1, 2];
        
        let arrayLike = {
          name: "jw",
        	age: 100
        };
        
        console.log( arr.concat(arrayLike) ); 
        // [1,2,{name: "jw", age: 100}]
        ```
        
    

## 배열 탐색하기

1. **요소 = 단순값**
    
    (문자형에도 사용가능이라 설명 자세히 있음)
    
    - `arr.indexOf(item, from)`
        
        인덱스 from부터 시작해 요소(item) 찾음
        
        발견: 요소의 인덱스 반환 / 발견 X : `-1` 반환
        
    - `arr.lastIndexOf(item, from)`
        
        indexOf와 동일한 기능, 검색을 끝에서부터 시작
        
    - `arr.includes(item, from)`
        
        인덱스 from부터 시작해 요소 존재 여부 boolean 반환
        
2. **요소 = 객체**
    
    (단순값에도 사용 가능, but 위 세 개는 객체 찾기 불가)
    
    - `arr.find(function(item, index, array){…})`
        
        발견: 해당 요소 반환 / 발견X : `undefined` 반환
        
        - 전달되는 인자
        1. item : 처리할 현재 요소
        2. index : 처리할 현재 요소의 인덱스(optional)
        3. array : forEach를 호출한 배열(optional)
            
            
        - 인자 item만 가지고 `item => item.id == 1` 형태의 함수가 실무에 많이 사용됨
    
    ```jsx
    let users = [
      {id: 1, name: "John"},
      {id: 2, name: "Pete"},
      {id: 3, name: "Mary"}
    ];
    
    let user = users.find(item => item.id == 1);
    
    alert(user.name); // John
    ```
    
    - `arr.findIndex(function(item, index, array){…})`
        
        발견 : 요소의 인덱스 반환 / 발견 X : `-1` 반환
        
    - `arr.findIndex(function(item, index, array){…})`
        
        발견 : 요소의 인덱스 반환 / 발견 X : `-1` 반환
        
    - 조건에 맞는 요소가 여러개라면?
        
        `arr.filter(function(item, index, array){…})` 
        
        - 찾은 요소 전체를 담은 배열 반환 / 발견 X : 빈 배열 반환
        - `arr.filter(function, thisArg)`
            
            ⇒ 함수에 this를 넣어줘야 할 때, thisArg자세한 설명 밑에
            
        

## 배열 전체 순회하기

- **for...of 반복문**

`for(var value of iterable){…}`

반복가능한 객체의 속성값에 접근해서 명령어 반복 수행

(for...in 문법은 되도록 사용X)

```jsx
const array1 = ['a', 'b', 'c'];

for (const element of array1) {
  console.log(element);
}

// expected output: "a"
// expected output: "b"
// expected output: "c"

```

- **forEach 메소드**
    
    함수를 배열 요소 각각에 실행 → `undefined` 반환
    
    - 기본형
        
        `arr.forEach(function)`
        
        배열 요소 각각에 fnc 실행 (요소값이 기본 arg)
        
    
    - 매개변수 (당연히 변수명 변경 가능)
        
        `arr.forEach(function(item, index, array){…})`
        
        1. item : 처리할 현재 요소
        2. index : 처리할 현재 요소의 인덱스 (optional)
        3. array : forEach를 호출한 배열 (optional)
            
            
    - undefined를 반환하기 때문에 `break`,  `continue`,  `return` 구문을 사용해서 함수를 벗어날 수 없다.
        
        ```jsx
        ["a", "b", "c"].forEach(alert); // 세 요소 차례대로 출력
        
        ["a", "b", "c"].forEach((item, index, array) => {
          alert(`${item} is at index ${index} in ${array}`);
        });
        
        // a is at index 0 in a,b,c
        // b is at index 1 in a,b,c
        // c is at index 2 in a,b,c  
        ```
        
        - `for…of`와의 차이점
            
            
            |  | forEach | for…of |
            | --- | --- | --- |
            | 종류 | 함수(메소드) | 반복문 |
            | 사용대상 | 배열 | iterable한 객체 |
            | 반환값 | undefined
            (return 사용불가) | return값 |
            
            iterable : 순회 가능한 자료구조
            

## 배열 변형하기

- **map** (중요)
    
    `arr.map(function(item[, index, array]))`
    
    요소 전체를 대상으로 함수 호출, 반환값을 배열로 반환
    
    ```jsx
    let result = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
    console.log(result); // [5,7,6]
    ```
    
    - 반환값 객체로 만들기
        
        `arr.map(item ⇒ ({key: value, key: value, …}))`
        
        = `arr.map(function(item) {`
        
        `let obj = {};`
        
        `obj.key = value;`
        
        `return obj;`
        
        `}`
        
    
    - 활용
        
        `name`을 나타내는 프로퍼티를 가진 객체 `user`가 담긴 배열이 있습니다. `name`의 값만 담은 새로운 배열을 만들어주는 코드를 작성하시오.
        
        ```jsx
        let john = { name: "John", age: 25 };
        let pete = { name: "Pete", age: 30 };
        let mary = { name: "Mary", age: 28 };
        
        let users = [ john, pete, mary ];
        
        let names = users.map(item => item.name);
        
        alert( names ); // John, Pete, Mary
        ```
        

- **sort**
    
    `arr.sort(compareFunction)`
    
    배열의 요소 재정렬/ 재정렬된 배열 반환
    
    (but 이미 배열 자체가 수정되었기에 반환값 잘 사용x)
    
    - compareFunction(정렬 함수) : 정렬 순서를 정의하는 함수
        
        
        - 생략시 `arr.sort()`
            
            ```jsx
            let arr = [ 1, 2, 15 ];
            
            arr.sort(); // arr 내부가 재 정렬됨
            
            alert( arr );  // 1, 15, 2
            ```
            
            요소가 문자열로 취급되어 재정렬됨
            
            → 문자열 비교는 사전편집 순으로 진행
            
            → 2는 15보다 큰 값으로 취급 (`"2" > "15"`)
            
            ∴ 의도대로 정렬되지 않을 수 있음
            
        
        - compare 함수 형식
            - 반드시 인수로 값 두 개를 비교
            - 반환 값 있어야 함
                
                반환값 < 0 ⇒ a가 b보다 앞에 오도록 정렬
                
                반환값 > 0 ⇒ b가 a보다 앞에 오도록 정렬
                
            
            ```jsx
             function compare(a, b) {
              if (a > b) return 1; // 첫 번째 값이 두 번째 값보다 큰 경우
              if (a == b) return 0; // 두 값이 같은 경우
              if (a < b) return -1; //  첫 번째 값이 두 번째 값보다 작은 경우
            }
            
            arr.sort( (a, b) => a - b );
            // 이렇게 단순화도 가능
            ```
            
            - 다양한 언어가 사용된 문자열 arr에는 localeCompare 메소드를 사용
                
                ```jsx
                let countries = ['Österreich', 'Andorra', 'Vietnam'];
                
                alert( countries.sort( (a, b) => a > b ? 1 : -1) ); // Andorra, Vietnam, Österreich (제대로 정렬이 되지 않았습니다.)
                
                alert( countries.sort( (a, b) => a.localeCompare(b) ) ); // Andorra,Österreich,Vietnam (제대로 정렬되었네요!)
                ```
                
- **reverse**
    
    `arr.reverse`
    
    요소를 역순으로 재정렬 (배열 자체를 수정)
    
- **split**
    
    `str.split(separator, limit)`
    
    문자열 → 배열
    
    - separator : 문자열을 끊어야 할 부분을 나타내는 문자열
        - `""` (빈 string) : 각각의 문자가 원소가 됨 (`[s,t,a,r]`)
        - 생략 or 발견X : 원본 str을 유일한 원소로 가진 배열 반환
    - limit : 배열의 최대 요소 갯수
    
    ```jsx
    let names = 'Bilbo, Gandalf, Nazgul';
    
    let arr = names.split(', '); // [Bilbo, Gandalf, Nazgul]
    ```
    

- **join**
    
    `arr.join([separator])`
    
    배열 → 문자열
    
    나눠진 요소를 하나로 합쳐서 문자열로 반환
    
    - `separator`
        
        각 요소를 구분할 문자열 지정
        
        - 입력시, 중간 중간에 껴넣어짐
        - 생략시, 배열의 요소들이 쉼표로 구분됨
        - `''`입력시, 아무 문자도 없이 연결됨
    
    ```jsx
    const elements = ['Fire', 'Air', 'Water'];
    
    console.log(elements.join());
    // expected output: "Fire,Air,Water" 쉼표까지 포함됨
    
    console.log(elements.join(''));
    // expected output: "FireAirWater"
    
    console.log(elements.join('-'));
    // expected output: "Fire-Air-Water"
    ```
    

- **reduce**
    
    `arr.reduce(fucntion(accumulator, item, index, array)` 
    
    `{~}, initial)`
    
    각 요소에 함수 반복 실행, 결과를 누적시켜 하나의 값을 도출
    
    (`reduceRight`는 동일한 기능/ 배열의 오른쪽부터 연산 실행)
    
    - `accmulator` : 이전 함수 호출 결과 (결과값이 누적된 누전기)
    - `initial` : 함수 최초 호출시 사용되는 초깃값
        
        initial(초깃값)은 생략 가능
        
        BUT 배열이 비어있으면 에러 → 쓰는 걸 권장(초깃값 반환)
        
    - `item` : 현재 배열의 요소
    - `index` : 현재 요소의 인덱스
    - `array` : 배열
    
    ```jsx
    let arr = [1, 2, 3, 4, 5];
    
    let result = arr.reduce((sum, current) => sum + current, 0);
    
    alert(result); // 15
    ```
    

## 기타 **메서드**

- **arr.some**
    
    `arr.some(function(item[, index[, array]])`
    
    모든 요소 대상으로 판별fn 호출 → 참인 값 1개라도 있으면 → `true` / 하나도 없다면 `false` 반환
    
- **arr. every**
    
    `arr.some(function(item[, index[, array]])`
    
    some과 동일, but 요소가 모두 참이어야 `true`
    

- **arr.fill**
    
    `arr.fill(value[, start[, end]])`
    
    인덱스(start~end(미포함))에 value를 채워 변형한 배열 반환
    
- **arr.copyWithin**
    
    `arr.copyWithin(target[, start[, end]])`
    
    target(인덱스)에 start ~ end(미포함) 요소 복사 붙여넣기
    
    원 배열 자체를 수정
    
    - `arr.copyWithin(target)`
        
        배열 전체 복사 → target에 붙여넣기 (length에 맞춰 잘림)
        
    - `arr.copyWithin(target, start)`
        
        start부터 끝까지 복사 → target에 붙여넣기
        
- **arr.isArray**
    
    `arr.isArray()`
    
    배열인지 아닌지 판별해서 boolean 반환
    
    (배열은 객체형이기 때문에 typeof()로 판별 불가함)
    
    ```jsx
    alert(Array.isArray({})); // false
    
    alert(Array.isArray([])); // true
    ```
    

- **array.length**
    
    가장 큰 인덱스 값 + 1 (배열 내 요소의 개수 X)
    
    ```jsx
    let fruits = [];
    fruits[123] = "사과";
    
    alert( fruits.length ); // 124
    ```
    
    - 수동으로 감소시킬 수 있음 BUT 잘린 만큼 배열이 날아감
        
        (증가/복구 불가)
        
        ```jsx
        let arr = [1, 2, 3, 4, 5];
        
        arr.length = 2; // 요소 2개만 남기고 잘라봅시다.
        alert( arr ); // [1, 2]
        
        arr.length = 5; // 본래 길이로 되돌려 봅시다.
        alert( arr[3] ); // undefined: 삭제된 기존 요소들이 복구되지 않습니다.
        ```
        

- arr.toString
    
    `array.toString()` ⇒ “value, value, ...”
    
    (`string(array)`)
    
    배열엔 `toString`메서드가 구현되어 있어 호출하면 요소를 쉼표로 구분한 문자열로 반환함
    
    ```jsx
    alert( [] + 1 ); // "1"
    alert( [1] + 1 ); // "11"
    alert( [1,2] + 1 ); // "1,21"
    ```
    

## thisArg

`arr.method(func, thisArg)`

- thisArg를 인자로 넘기면 호출 함수를 실행 시, this로 설정됨
- 선택적으로 사용 가능한 마지막 인수
- 함수를 호출하는 대부분의 배열 메소드가 매개변수로 받을 수 있음(`find`, `filter`, `map` 등/ `sort` 제외)

```jsx
let army = {
  minAge: 18,
  maxAge: 27,
  canJoin(user) {
    return user.age >= this.minAge && user.age < this.maxAge;
  }
};

let users = [
  {age: 16},
  {age: 20},
  {age: 23},
  {age: 30}
];

// army.canJoin 호출 시 참을 반환해주는 user를 찾음
let soldiers = users.filter(army.canJoin, army);
// users.filter(user => army.canJoin(user)) 도 가능하나 위 방식이 이해가 더 쉬움

alert(soldiers.length); // 2
alert(soldiers[0].age); // 20
alert(soldiers[1].age); // 23
```

- thisArg 사용 안 했다면?
    
    `let soldiers = users.filter(army.canJoin)`
    
    : `army.canJoin`은 단독 함수처럼 취급되고, 함수 본문 내 `this`
    는 `undefined`가 되어 에러 발생
    

## 다차원 배열

```jsx
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

alert( matrix[1][1] ); // 5, 중심에 있는 요소
```