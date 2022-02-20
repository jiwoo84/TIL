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
    
- string만 포함된 변수- 전체 대문자
    
    ```jsx
    const HIDDEN_CLASSNAME = "hidden";
    ```
    

## 자투리

- `%lt;` : <
- `<br>` : 줄바꿈
- `alert()` : 알림·경고창 띄움
- `console.log()` : 콘솔에 내용 출력 /  `log`가 메소드라서 `,`으로도 string 연결 가능
- `console.dir()` : element까지 자세히 보여줌
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/00ca200e-d4bb-44bd-abd8-2eccea361b14.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/00ca200e-d4bb-44bd-abd8-2eccea361b14.png)
    
- `element.remove()` : element 삭제
- 공백 금지에 공백 넣기: [”~ ~”]

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
        
    
    - 신버전
        
        ``string ${var-name}`` = “string var값”
        
        ``string ${var-name} string`` = “string var값 string”
        
        ```jsx
        const username = jiwoo;
        
        "hello" + username;
        `hello ${username}`; // 둘의 값은 같다
        ```
        
    

# variable

|  | 재선언 | 재할당 |
| --- | --- | --- |
| const | X | X |
| let | X | O |
| var | O | O |

## **1. const**

`const name = 값;`

- 값 절대 변경 불가 (변경하려면 let 사용)
    
    

## **2. let**

`let name = 값;`

- 값 변경
    
    (let 생략)  `name = 값;`
    
    ```jsx
    let myName = "jiwoo";
    myName = "jw";
    
    console.log(myName); // 결과값: jw
    ```
    

## **주의사항**

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
    

# boolean

(text 아닌 data type)

- **true**

- **false**

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

## **선언**

`fuction fnc-name(param) {~;}`

- parameter (매개변수) :  값을 함수 안으로 매개해주는 변수
    - parm 2개 이상 : `fuction fnc-name(param, param, …) {~;}`
    - 다른 data type과 구별해서 작성 (`,` `+` 사용)
    
    ```jsx
    function combine(word) {
    	console.log("I want to eat", word, 2);
    }
    
    function combine(word) {
    	console.log("I want to eat" + word + 2);
    }
    
    // 두 개는 같다
    ```
    

## 실행

`fnc-name(arg);` 

- argument (전달인자, 값 value) :  함수로 전달하는 값

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

## **짧은 fnc 선언**

`(param) ⇒ 명령문`

fnc 이름을 설정할 필요 X , 짧은 fnc일 경우 사용

```jsx
function sayHello(name) {
	console.log("hi " + name);
};

(name) => console.log("hi " + name);

// 두 개는 같다
```

- **method라면**
    
    `obj.prop((param)=> 명령문)`
    
    ```jsx
    jw.sayHello((name) => console.log("hi " + name))
    ```
    

# **return**

함수의 반환값을 내보냄

## **return 없다면**

```jsx
function plus(a, b) {
	alert(a + b);
	};

console.log(plus(2,3));
```

1. fnc 실행

![Untitled](Basic%2081d4a46fb71941bba1534df9909a25ec/Untitled.png)

1. 반환값 없기 때문에 `plus(2,3)` 자리에 5 들어가지 못함
    
    그러므로 console창에 undefined이 출력
    
    ![Untitled](Basic%2081d4a46fb71941bba1534df9909a25ec/Untitled%201.png)
    

∴ fnc은 명령만 시행할 뿐, 값을 바깥으로 내보내지 못함

## return 있다면

```jsx
function plus(a, b) {
	alert(a + b);
	return a + b;  // return
	};

console.log(plus(2,3));

// console창에 5 출력
```

fnc의 값 바깥으로 내보내기 가능

- 무조건 return 값이 호출값(반환값)
    
    ```jsx
    function plus(a, b) {
    	alert(a + b);
    	return hello;
    	};
    
    console.log(plus(2,3));
    
    // console창에 hello 출력
    ```
    

- return 뒤의 명령어는 실행 X
    
    function은 남아있는 것이 아니라, 실행 후 사라지고 결과만 남김
    

# **prompt**

안내 메세지 + 입력 창 띄우고, 입력값 저장

## 생성

`prompt("안내 메세지", "기본 입력값(생략가능)")`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/7aec5df6-4b82-456e-8753-5e8ef0c96f5b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/7aec5df6-4b82-456e-8753-5e8ef0c96f5b.png)

- `취소` 클릭 → “null”
- 입력x `확인` 클릭 → 빈 string (`’’`)
    
    

## **특징**

- 입력할 때까지 로딩중 (js를 일시정지 시킴)
- 입력창을 꾸미지 못함 → 요즘은 사용x

# typeof

값의 data type 알아내 반환

## 생성

`typeof val`

```jsx
console.log(typeof 1); // number 
console.log(typeof "jw"); // string
```

## 결과값

- string이 무조건 기본값
- 숫자로 바꾸려면 parseInt() 사용

![숫자 입력](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/f6431f2b-dce9-4b41-861e-8cc029706cc8.png)

숫자 입력

![숫자도 string](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/c6128537-87af-4176-9238-08bb5253694c.png)

숫자도 string

# **parseInt**

string → number로 type 변환 후, 반환

## 생성

`parseInt(val);`

![입력창에 15 입력 시](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/ab76e7a0-c4ad-4c6d-b8a1-be6e1b87565b.png)

입력창에 15 입력 시

![age = string / parseInt(age) = number](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/c6e70f59-296b-4dcc-aeef-ff952a7d23f2.png)

age = string / parseInt(age) = number

## **의의**

- 값의 크기비교 가능 (숫자로 바꾸기 때문)
- 숫자 아닌 입력값 인지 (**NaN**으로 뜸)

```jsx
const age = parseInt(promt("How old are you?"));

// 두 개의 fnc 사용해서 입력값 받고 num로 type 변경
```

# isNaN

NaN(숫자가 아님)을 판별 후, boolean 반환

## 생성

`isNaN(val)` = boolean

- number → **false**
- number X → **true**

```jsx
const age = parseInt(promt("How old are you?"));

console.log(isNaN(age));
// 입력값에 따라 true or false 뱉어냄
```

# condition

## 생성

condition=boolean 일 것

- **조건 1개**
    
    `if (condition) {명령어}`
    
    condition=false : 조건문 빠져나옴
    
- **조건 2개**
    
    `if (condition) {명령어} else {명령어}`
    
- **조건 여러 개** (else 생략 가능)
    
    `if (condition) {명령어;}`
    
    `else if (condition) {명령어;}`
    
    `else if (condition) {명령어;}`
    
    `…`
    
    `else {명령어;}`
    

![false가 나오면 아래 조건문으로 점진적으로 내려감](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/3fcf5957-353b-4ecf-bca3-2020f56f7f7c.png)

false가 나오면 아래 조건문으로 점진적으로 내려감

## **조건문 연결 (AND/OR operator)**

1.  **`&&`** : and
    - 모두 true = `true`
    - 하나라도 false = `false`
    
    ```jsx
    if (age>=18 && age<=50) {명령문};
    
    // 18≤ age ≤50 일 때, 실행 
    ```
    
2.  **`||`** : or
    
    하나라도 true = `true`
    
    ```jsx
    if (isNaN(age) || age<0) {명령문};
    
    // age가 숫자가 아니거나 or 음수 일 때, 실행
    ```
    

1.  `**===**` : ‘같음’ 확인 기호
    
    ```jsx
    if (age ===100) {명령문}
    else (age<100) {명령문};
    
    // age=100 아니라면 아래로 내려감
    ```
    
    - `===` & `==` & `=` 차이점
        
        
        - `===` : 값 + data type 비교
        - `==` : 값만 비교 (binaryCode로 비교)
        - `=` : value 할당 (’같음’ 비교 기호 아님)
        
        - 예시
            
            `0 === false` → false (false의 type은 boolean이므로)
            
            `0 == false` → true (false는 이진법으로 0 표기)
            
        
2. `**!==**` : ‘다름’ 확인 기호 (~가 아니라면 실행)

- <음주 가능 나이 계산기> 예시

![else 안써도 된다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/53b6ff6f-7514-4e43-8910-a2c5a1f64af4.png)

else 안써도 된다

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