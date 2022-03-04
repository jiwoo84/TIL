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

- `%lt;` : <
- `<br>` : 줄바꿈

- `alert()` : 알림·경고창 띄움
    - 뜬 순간 브라우저의 모든 행위를 멈춤
    - 값을 반환 X ( `undefined` 반환)
    
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

1. **integer** : 숫자 (2)

1. **float :** 소수점 숫자 (1.5)

1. **string :** 문자, 따옴표 안 `“string”`  `‘string’`
    
    
- **문자열 합치기**
    - `“string” + “string” +2` = “stringstring2”
    
    - 구버전
        
        `"string " + var-name` = “string var값”
        
    
    - 신버전 (추천)
        
        ``string ${var-name}`` = “string var값”
        
        ``string ${var-name} string`` = “string var값 string”
        
        ```jsx
        const username = jiwoo;
        
        "hello" + username;
        `hello ${username}`; // 둘의 값은 같다
        ```
        
    
    1. 객체(object)
        - 다양한 데이터를 담을 수 있음
            
            이외는 원시형(primitive type) : 하나의 데이터만 담기 가능
            

## data type 변경

- `type(value)`  :  value의 type 변경 후, 반환
    
    
    - number(~)
        - `number(null)` = 0
        - `number(undefined)` = NaN
        - `number("  2/n")` =  2  (공백 무시됨)
        
- **parseInt**
    
    `parseInt(~);`
    
    string → number로 변환 후, 반환
    
    ```jsx
    const age = parseInt(promt("How old are you?"));
    
    // 두 개의 fnc 사용해서 입력값 받고 num로 type 변경
    ```
    
    - 의의
        - 값의 크기비교 가능 (숫자로 바꾸기 때문)
        - 숫자 아닌 입력값 인지 (**NaN**으로 뜸)
        
    - `number(~)` 와의 차이점
        
        
        - parseInt는 숫자를 찾아내서 반환하는 기능이 있음
            
            ex) `parseInt("10회")` = 10
            
            `number("10회")` = NaN
            
            `parseInt("제10회")`  = NaN  (문자열이 앞에 오는 경우는 X)
            
        - parseInt는 정수만 반환
            
            ex) `parseInt("2.55")` = 2
            
            `number("2.55")` = 2.55
            
            `parseFloat("2.55")` = 2.55  (소수는 parseFloat 사용)
            

## typeof

값의 data type 알아내 반환

- **생성**
    
    `typeof val`
    
    `typeof(val)`  둘 다 가능
    
    ```jsx
    console.log(typeof 1); // number 
    console.log(typeof "jw"); // string
    ```
    

- **결과값**
    - string이 무조건 기본값
        
        → 숫자로 바꾸려면 parseInt() 사용
        
        ![숫자 입력](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/f6431f2b-dce9-4b41-861e-8cc029706cc8.png)
        
        숫자 입력
        
        ![숫자도 string](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/c6128537-87af-4176-9238-08bb5253694c.png)
        
        숫자도 string
        
    - 예외
        - `typeof null == "object"` 언어 자체의 오류
        - `typeof function(){} == "function"` 함수는 특별하게 취급됩니다.

## isNaN

NaN(숫자가 아님)을 판별 후, boolean 반환

- **생성**
    
    `isNaN(val)` = boolean
    
    - isNaN(number) → **false**
    - isNaN(number X) → **true**
    
    ```jsx
    const age = parseInt(promt("How old are you?"));
    
    console.log(isNaN(age));
    // 입력값에 따라 true or false 뱉어냄
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

- **null**
    - 텅빈 상태가 아니고 ’없음’으로 채워진 상태
    - 절대 자연적으로 발생x, 안에 없다는 것을 확실히 하려고 사용
    
- **undefined**
    - 정의되지 않음
    - 값이 설정되지 않음 (텅빈 상태)
    
    ```jsx
    const a = null;
    const b;
    
    console.log(a,b); // = null, undefined
    ```
    
- **Nan** : (Not a Number) 숫자가 아님
    - 비교연산자에서 NaN이 피연산자인 경우 항상 false 반환

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

## 선언

`var arr-name = [~, ~, ~]`

- integer, string, boolean, var 모두 입력 가능

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/f708b986-6575-49e4-891f-9c49426aa228.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/f708b986-6575-49e4-891f-9c49426aa228.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/8e9a210d-0e34-4cfa-95c6-7938ec45c869.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/8e9a210d-0e34-4cfa-95c6-7938ec45c869.png)

## 값 출력

`arr-name[n]` : array 중 n번째 값

- 0부터 세기 시작한다
    
    ```jsx
    const oneWeek = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"];
    
    console.log(oneWeek[4]); // = fri
    ```
    

## **값 추가**

- `arr-name.push(…)` : 맨 끝에 값 추가
- `arr.name[n] = ~;` : 원하는 위치에 값 변경/추가

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/c61adc1d-db3a-447f-bc30-a18959b24232.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/c61adc1d-db3a-447f-bc30-a18959b24232.png)

![밑에 console.log 값은 “sun”이 추가됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/9b0a7480-7ebb-405a-b1af-a6aaec956050.png)

밑에 console.log 값은 “sun”이 추가됨

## 값 삭제

- 첫번째 요소 제거 `arr-name.shift`
- 마지막 요소 제거 `arr-name.pop`
- 지정 요소 제거 `arr-name.splice(시작위치,제거건수)`
    
    ```jsx
    // arr = ['a', 'b', 'e', 'f']
    arr.splice(2, 1); // index 2 부터 1개의 요소('c')를 제거
    
    // arr = ['a', 'f']
    arr.splice(1, 2); // index 1 부터 2개의 요소('b', 'e')를 제거
    ```
    

## **array 길이**

`arr-name.length` = n (길이값 반환)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/ef6f5d94-147a-4928-b518-668987c4e83b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/ef6f5d94-147a-4928-b518-668987c4e83b.png)

# object (객체)

- 서로 연관된 변수와 함수(method)를 그룹핑, 이름 붙인 것
- 개체의 특성에 대해 많은 property 가진 요소
- 순서없이 저장하는 구조

```jsx
const jwName = "jiwoo";
const jwHeight = 160;
const jwBirthday = 0804;
```

## 선언

`var obj-name = {`

`prop:~,` 

`prop:~,`

`};`

```jsx
const jw = {
	name: "jiwoo",
	height: 160,
	birthday: 0804,
}
```

## 호출

`obj-name.prop`

= `obj-name["prop"]`

두 방법 모두 같은 값 호출

```jsx
console.log(jw.name);
console.log(jw.["name"]);

// 둘의 값은 같다
```

## **수정/ 추가**

`object.prop = ~;`

```jsx
const jw = {
	name: "jiwoo",
	height: 160,
	birthday: 0804,
}

console.log(jw.height); // 160

jw.height = 170;

console.log(jw.height); // 170 -> 값 변경
```

## 삭제

`delete obj-name.prop`

= `delete obj-name.['prop']`

## 주의사항

- **const는 수정이 불가능하지 않나요?**
    
    const가 아닌 안의 prop의 값을 수정하니까 가능
    
    obj인 player는 아직도 동일하다!
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/c163b785-a18c-4b50-a345-ee59df375625.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/c163b785-a18c-4b50-a345-ee59df375625.png)

![const 인 obj 값 수정 시 → 오류](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/fe8a6cd6-139c-4e13-b9fc-6a566089bc57.png)

const 인 obj 값 수정 시 → 오류

# function

- 반복해서 사용 가능한 코드 조각
- 내부에서 외부 순서로 실행

## **선언 (함수 선언식)**

`fuction fnc-name(param, param, ...) {~;}`

- **parameter (매개변수)**
    
    값을 함수 안으로 매개해주는 변수
    
    - 다른 data type과 구별해서 작성 (`,` `+` 사용)
    - 전달 받지 못하면 `undefined` 할당
        - 기본값 설정 : `(param = 기본값)` (arg 없으면 기본값 할당됨)
        - 중간에 기본값 설정 가능 [클릭](https://ko.javascript.info/function-basics)
    
    ```jsx
    function combine(word) {
    	console.log("I want to eat", word, 2);
    }
    
    function combine(word) {
    	console.log("I want to eat" + word + 2);
    }
    
    // 두 개는 같다
    
    function combine(word = "kimbap") {
    	console.log("I want to eat", word, 2);
    }
    
    combine();  
    // param 기본값 설정했기 때문에
    // "I want to eat kim bap 2" 출력
    ```
    

- 지역 변수(local variable/함수 내에서 선언한 변수)는 함수 안에서만 접근 가능
- 전역 변수(global variable/함수 외부에서 선언)는 함수 내에서도 접근 가능
    
    (함수 내에서 변수 변경 시, 함수를 호출한 후에 값 변경)
    
- **함수 표현식**
    
    `var func-name = function() {명령문;}`
    
    - js는 함수를 값으로 보기 때문에 할당, 복사, 선언 가능
    - 선언식은 어디 함수든 접근할 수 있지만, 표현식은 선언된 이후 함수에만 접근 가능 (js에서 먼저 함수 선언식을 읽고, 코드를 실행하기 때문)
    
    ```jsx
    function sayHi() {
      alert( "Hello" );
    }
    
    let sayHi = function() {
      alert( "Hello" );
    };
    
    // 둘은 같다
    
    let func = sayHi;    // 함수 복사
    
    func(); // Hello     // 복사한 함수를 실행(둘이 같다)
    sayHi(); // Hello
    ```
    

- **콜백 함수**
    
    이미 등록된 상태에서 어떤 이벤트 발생이나 특점 시점에 호출되는 함수 (문법적 특징 X, 호출 방식에 의한 구분)
    
    ```jsx
    function ask(question, yes, no) {
      if (confirm(question)) yes()
      else no();
    }
    
    function showOk() {
      alert( "동의하셨습니다." );
    }
    
    function showCancel() {
      alert( "취소 버튼을 누르셨습니다." );
    }
    
    ask("동의하십니까?", showOk, showCancel);
    // 사용법: 함수 showOk와 showCancel가 ask 함수의 인수로 전달됨
    ```
    

- **익명 함수**
    
    이름 없이 선언한 함수 (해당 줄 바깥에서는 접근 어려움)
    
    ```jsx
    function ask(question, yes, no) {
      if (confirm(question)) yes()
      else no();
    }
    
    ask(
      "동의하십니까?",
      function() { alert("동의하셨습니다."); },
      function() { alert("취소 버튼을 누르셨습니다."); }
    );
    // ask문의 함수 두 개 다 익명함수
    ```
    

## 화살표 함수

- 매개변수 지정 방법
    
    `() ⇒ 명령문`  매개변수 없다면
    
    `(param) ⇒ 명령문`  매개변수 한 개 (소괄호 생략 가능)
    
    `(param, param) ⇒ 명령문`  매개변수 여러 개
    
- 함수 몸체 지정 방법
    
    `x => x * x` 
    
    = `x => {return x * x }`
    
    - 몸체가 한 줄 이면
        
        → 중괄호 생략 가능
        
        → 암묵적으로 return 됨
        
    - 몸체가 여러 줄 이면
        
        중괄호 생략 불가 / return 값 표시해야함
        
    

```jsx
function plus(a, b) {
	return a + b;
};

let plus = (a, b) => a + b;

// 두 개는 같다
```

- **method라면**
    
    `obj.prop((param)=> 명령문)`
    
    ```jsx
    jw.sayHello((name) => console.log("hi " + name))
    ```
    

## 실행

`fnc-name(arg);` 

- argument (전달인자, 값 value) :  함수로 전달하는 값

## **return**

함수의 반환값을 내보냄

- **return 없다면**
    
    fnc 실행 → (호출 한다면)→ `undefined` 반환
    
    ```jsx
    function plus(a, b) {
    	alert(a + b); 
    	};
    
    console.log(plus(2,3));  
    // aleart로 5가 뜨고, undefined 출력
    ```
    
    ∴ fnc은 명령만 시행할 뿐, 값을 바깥으로 내보내지 못함
    

- **return 있다면**
    
    fnc의 값 바깥으로 내보내기 가능
    
    ```jsx
    function plus(a, b) {
    	alert(a + b);
    	return a + b;  // return
    	};
    
    console.log(plus(2,3));
    
    // console창에 5 출력
    ```
    

- **주의사항**
    - return 뒤의 명령어는 실행 X
    - 무조건 return 값이 반환값
        
        ```jsx
        function plus(a, b) {
        	alert(a + b);
        	return hello;
        	};
        
        console.log(plus(2,3));
        
        // console창에 hello 출력
        ```
        
    - return에 긴 값을 출력하고 싶다면 같은 줄에 쓸 것 (js는 return문 끝에 ;을 자동으로 넣기 때문)
        
        ```jsx
        return
        (something + wrong + f(a))
        // undefined 반환
        
        return (something + wrong + f(a))
        // 의도대로 반환!
        
        return (
        	something + wrong + f(a)
        ) // 이렇게 써도 됨
        ```
        

 

# Method (메소드)

object(객체)에 포함된 function

## 선언

`var obj-name = {`

`prop: function(param) {~;},`

`props: ~; }`

(단순한 fnc 선언에서 function↔fnc-name 자리 반대)

```jsx
const jw = {
	sayHello: function(name) {
		console.log("hi " + name);
	}
};
```

## 추가/수정

`obj-name.prop = function(param) {~;}`

- 명령문 안에서 obj 지정시, obj-name 대신 this 쓰면 리팩토링에 용이

## 실행

`obj-name.prop(arg);`

```jsx
const jw = {
	sayHello: function(name) {
		console.log("hi " + name);
	}
};

jw.sayHello("namjun"); // hi namjun 출력
```

# **prompt**

안내 메세지 + 입력 창 띄우고, 입력값 저장

## 생성

`prompt("안내 메세지", "기본 입력값(생략가능)")`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/7aec5df6-4b82-456e-8753-5e8ef0c96f5b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/7aec5df6-4b82-456e-8753-5e8ef0c96f5b.png)

- `취소` 클릭 → “null”
- 입력x `확인` 클릭 → 빈 string (`’’`)
- 입력값은 string으로 반환 ex) ‘12’ (숫자 아님)

## **특징**

- 입력할 때까지 로딩중 (js를 일시정지 시킴)
- 입력창을 꾸미지 못함 → 요즘은 사용x
- IE에서는 기본값 필수 입력
    
    

# confirm

`confirm(question)`

매개변수로 받은 question(질문)과 확인 및 취소 버튼이 있는 모달 창 실행

사용자가 확인버튼를 누르면 `true`, 그 외의 경우는 `false`를 반환

```jsx
let isBoss = confirm("당신이 주인인가요?");

alert( isBoss ); // 확인 버튼을 눌렀다면 true가 출력/ 취소는 false
```

# condition

## 생성

condition=boolean 을 반환

(비어있지 않은 문자열은 모두 true를 반환 ex) “0” )

- **조건 1개**
    
    `if (condition) {명령어}`
    
    condition=false : 조건문 빠져나옴
    
- **조건 2개**
    
    `if (condition) {명령어} else {명령어}`
    
- **조건 여러 개** (맨 끝 else 생략 가능)
    
    `if (condition) {명령어;}`
    
    `else if (condition) {명령어;}`
    
    `else if (condition) {명령어;}`
    
    `…`
    
    `else {명령어;}`
    
    ![false가 나오면 아래 조건문으로 점진적으로 내려감](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/3fcf5957-353b-4ecf-bca3-2020f56f7f7c.png)
    
    false가 나오면 아래 조건문으로 점진적으로 내려감
    

- <음주 가능 나이 계산기> 예시
    
    ![else 안써도 된다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/53b6ff6f-7514-4e43-8910-a2c5a1f64af4.png)
    
    else 안써도 된다
    

- **조건부 연산자**  `?` **사용**
    
    `condition ? value1 : value2;`
    
    condition 만족 시 → value1 반환 / 불만족 → value2 반환
    
    - 다중 사용
        
        `condition ? value1 :` 
        
        `condition ? value2 :`
        
        `value 3;`
        
    
    - 조건에 따라 반환값을 달리하려는 목적으로 만들어짐
        
        간단한 줄 아니고서는 if 사용이 나음
        
    
    ```jsx
    let result;
    
    if (a + b < 4) {
      result = '미만';
    } else {
      result = '이상';
    }
    
    //
    
    let result = (a + b < 4) ? '미만' : '이상';
    
    // 두 개의 코드는 같은 결과
    ```
    

## 주의사항

- **순서의 중요성**
    
    범위가 작은 순서대로 작성할 것
    
    예시)
    
    ```jsx
    if (age>80) {
    	console.log("you are old");
    } else (age===100) {
    	console.log("you are 100");
    }
    ```
    
    이렇게 하면 age=100일 때 아래 코드가 수행 안됨
    
    이미 age>80 에서 true 라서 코드가 실행되기 때문
    
    ```jsx
    if (age===100) {
    	console.log("you are 100");
    } else (age>80) {
    	console.log("you are old");
    }
    ```
    
    순서를 바꿔주면 의도한대로 작동
    

# switch

복수의 if 조건문은 switch문으로 변환 가능

## 생성

```jsx
switch(value) {

	case value1 : 명령문; //value = value1 이면 실행
	break;
	
	case value2 : 명령문;  //value = value2 면 실행
	break;
	…
	default : 명령문; //위에 해당 안되면 실행 (생략가능)

}
```

- case문 안에 `break` 없으면 조건에 상관없이 다음 case문 실행
- case문 묶기 가능
    
    ex) `case value 1 :`
    
    `case value 2 : 명령문;`
    
- case 옆 value에 자료형 정확히 기재해야 실행됨

# loop (반복문)

## while

`while(boolean) { ~ }`

- (조건)이 true라면 중괄호 안의 코드 실행
- false가 될 때까지 반복 실행
    
    ```jsx
    let i = 0;
    
    while (i < 3) {
      alert(i);
    	i++
    }
    ```
    
- **do...while**
    
    `do{명령문} while (condition)`
    
    - 명령 실행 → 조건 만족시, 명령 재실행 → 반복
    - 조건에 상관없이 최소한 1번은 실행

## for

`for (선언; 조건; 증감) {명령문}`

선언된 상태 → 조건 확인 → 명령 실행 → 증감 실행 → 조건 확인 → 명령 실행 (반복)

- 구성요소 생략 가능(모두 생략시, 무한 반복)

```jsx
for(let i = 0; i <3; i++){
	alert(i);
}
```

## 반복문 빠져나오기

`break`

- 속한 명령문이 즉시 종료되고 다음 문으로 프로그램 제어를 넘김
- 반복문의 시작 지점이나 끝 지점에서 조건을 확인하는 것이 아니라 본문 가운데 혹은 본문 여러 곳에서 조건을 확인해야 하는 경우, '무한 반복문 + `break`' 조합을 사용

```jsx
let i = 0;

while (i < 6) {
  if (i === 3) {
    break;  // = if ( i ===3 ) break;
  }
  i = i + 1;
}

console.log(i);  // 3 출력
```

## 다음 반복으로 넘어가기

`continue`

반복문을 아예 빠져나가는 것이 아니라, 실행중이던 루프를 빠져나가 다음 반복문을 실행

```jsx
for(let i = 0; i < 5; i++ ) {
	if (i === 3) continue; // 3에서 멈추고 4로 넘어감
	alert(i);
}
// 0, 1, 2, 4 출력
```

- ? 오른쪽에는 `break` / `continue` 사용 불가

## 반복문 label 설정

`labelName : 반복문{~}`

- 반복문에 이름을 부여
- 중첩 반복문에서 `break` / `continue` 사용해서 빠져나올 때 사용 가능

```jsx
outer: for (let i = 0; i < 3; i++) {

  for (let j = 0; j < 3; j++) {

    let input = prompt(`(${i},${j})의 값`, '');

    // 사용자가 아무것도 입력하지 않거나 Cancel 버튼을 누르면 두 반복문 모두를 빠져나옵니다.
    if (!input) break outer; // (*)
  }
}
alert('완료!');
```