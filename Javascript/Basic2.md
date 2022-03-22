# Basic2

# object (객체)

- 서로 연관된 변수와 함수(method)를 그룹핑, 이름 붙인 것
- 개체의 특성에 대해 많은 property를 가진 요소
- 순서없이 저장하는 구조
- 다양한 데이터를 담을 수 있음
    
    (↔ 원시형(primitive type) : 하나의 데이터만 담기 가능)
    
- 문자형/ 심볼형

```jsx
const jwName = "jiwoo";
const jwHeight = 160;
const jwBirthday = 0804;
```

## 선언

- **빈 객체 선언**
    1. `var name = new Object();` '객체 생성자' 문법
    2. `var name = {};`  '객체 리터럴' 문법 (주로 씀)

- **객체값 선언**
    
    `var obj-name = {`
    
    `prop: value,` 
    
    `prop: value,`
    
    `};`
    
    - property (key) - 문자형/심볼형(아닌 경우 문자형으로 변형됨)
    - value - 모든 자료형 허용
    
    ```jsx
    const jw = {
    	name: "jiwoo",
    	height: 160,
    	birthday: 0804,
    }
    ```
    
    - 계산된 프로퍼티
        
        `[prop] : value`
        
        프로퍼티 이름을 동적으로 받아옴
        
        ```jsx
        let fruit = prompt("어떤 과일을 구매하시겠습니까?", "apple");
        
        let bag = {
          [fruit]: 5, // 변수 fruit에서 프로퍼티 이름을 동적으로 받아 옵니다.
        };
        
        alert( bag.apple ); // fruit에 "apple"이 할당되었다면, 5가 출력됩니다.
        ```
        
    
- **프로퍼티 값 단축 구문**
    
    (변수 = key = value) `name : name` 단축해서 → `name`
    
    ```jsx
    function makeUser(name, age) {
      return {
        name, // name: name 과 같음
        age,  // age: age 와 같음
        // ...
      };
    }
    ```
    

## 호출

`obj-name.prop`

= `obj-name["prop"]` (조합된 키 이름에 사용)

```jsx
console.log(jw.name);
console.log(jw["my name"]);
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

## prop 존재 여부 확인

1. `obj.key === undefined`
    
    존재하지 않는 프로퍼티 → `undefined` 반환
    
    - 값에 undefined가 할당된 경우에는 정확한 존재여부 확인이 불가능하니 아래 방법 사용
    
2. `"key" in obj-name`  
    
    존재 여부에 따라 boolean 반환
    

```jsx
let user = { name: "John", age: 30, height: undefined, };

alert(user.birth === undefined); // user.birth 존재x -> true 출력
alert(user.height === undefined); // 존재하지만 할당값 일치 -> true 출력

alert("age" in user); // user.age가 존재 -> true 출력
alert("birth" in user); // user.bl 존재x -> false가 출력

```

## 주의사항

- **const는 수정이 불가능하지 않나요?**
    
    const가 아닌 안의 prop의 값을 수정하니까 가능
    
    obj인 player는 아직도 동일하다!
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/c163b785-a18c-4b50-a345-ee59df375625.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/26ad00c849fe490da9cb94bb82907b25/c163b785-a18c-4b50-a345-ee59df375625.png)

![const 인 obj 값 수정 시 → 오류](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/26ad00c849fe490da9cb94bb82907b25/fe8a6cd6-139c-4e13-b9fc-6a566089bc57.png)

const 인 obj 값 수정 시 → 오류

- **참조에 의해 저장·복사됨**
    
    다른 변수에 obj 할당 → 값 저장 X , 참조값(객체 저장된 메모리 주소) 저장
    
    : 원시값(문자열·숫자·불린)은 값 그대로 저장·할당·복사되는데 객체는 저장되어 있는 주소인 ‘참조값’이 저장됨. 고로 값이 저장된 위치는 똑같은데 열어볼 수 있는 키(할당 변수)가 늘어나는 셈.
    
    ![Untitled](Basic2%20c4ee2/Untitled.png)
    
    ```jsx
    let user = { name: 'John' };
    
    let admin = user;
    
    admin.name = 'Pete'; // 'admin' 참조 값에 의해 변경됨
    
    alert(user.name); // 'Pete' 출력
    ```
    

# function

- 반복해서 사용 가능한 코드 조각
- 내부에서 외부 순서로 실행

## **선언 (함수 선언식)**

`fuction fnc-name(param, param, ...) {~;}`

- **parameter (인자, 매개변수)**
    
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
    
    전역 변수(global variable/함수 외부에서 선언)는 함수 내에서도 접근 가능
    
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

- argument (인수, 전달인자, 값 value) :  함수로 전달하는 값

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

`}`

- 단축 구문 (위 구문과 객체 상속에 작은 차이가 있음)
    
    `var obj-name = {`
    
    `prop(param) {~;}` 
    
    `}`
    

(단순한 fnc 선언은 function↔fnc-name 자리 반대)

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

## this

지정 객체에 접근할 때 사용하는 객체

```jsx
let user = {
	name: "jw",
}

function sayHi() {
	alert(this.name);
}

user.sayHi();  //jw 출력(동적으로 참조 객체가 user로 정해짐)
```

- 객체가 없는 상태에서 this로 호출한다면?
    
    (엄격 모드ㅇ) `undefined` 할당됨
    
    (엄격 모드 X) `window` 전역 객체 참조
    
- 참조 객체가 호출 시 동적으로 정해짐
    - 화살표 함수는 정적으로 상위 객체를 참조함
        
        ```jsx
        // Good
        let user = {
          firstName: "보라",
          sayHi() {
            let arrow = () => alert(this.firstName);
            arrow();
          }
        };
        
        user.sayHi(); // 보라
        ```
        
        ```jsx
        // bad
        let user = {
          firstName: "보라",
          sayHi() = () => alert(this.firstName);
        };
        
        user.sayHi(); // undefined 
        ```
        
        상위 객체가 없으면 window를 참조하기 때문에 사용시 주의
        

# 생성자 함수 & new 연산자

## 생성자 함수

유사한 객체를 효율적으로 만들기 위한 함수

- 관례
    1. 함수 이름의 첫 글자는 대문자로 시작
    2. 반드시 `new` 연산자를 붙여 실행
    

## new 연산자

`new func-name();` (인수 없다면 괄호 생략 가능)

- 함수로 새 객체를 생성해주는 연산자
- 실행 과정
    1. 빈 객체를 생성
    2. 함수 실행해서 prop 채움
    3. 객체 반환
        - (안해도 되는데)return을 작성했다면
            - 객체를 `return` → `this` 대신 객체가 반환
            - 원시형을 `return` → `return`문이 무시

## 예시

```jsx
function User(name, age) {
  this.name = name;
  this.age = age;
}

let userInfo = new User("재찬", 22);

console.log(userInfo);
/* userInfo {name: '재찬', age: 22}
age: 22
name: "재찬" */
```

1. 빈 객체를 만듬 ( `this`있다면 할당)
2. 함수 본문을 실행
    
    (`this`에 새로운 프로퍼티를 추가해 `this`를 수정)
    
3. `this`를 반환

## new.target

함수가 `new`와 함께 호출되었는지 확인(함수 본문에 작성)

- 맞으면 함수 자체 반환
- 아니면 `undefined` 반환

# 옵셔널 체이닝

`?.`을 사용해 프로퍼티가 없는 중첩 객체를 에러 없이 접근

- **필요한 이유**
    
    ```jsx
    let user = {};
    
    alert(user.address);  // undiefined 반환 (에러x)
    
    alert(user.address.number); // 에러 발생
    
    alert( user && user.address && user.address.number );
    // 이전에 에러를 막기 위해 쓰던 코드
    ```
    
    - obj.prop를 호출하는 것은 값이 없어도 문제 없지만, 중첩 객체부터는 에러가 발생
    - 전에는 에러를 막기 위해 아래같이 코드 작성
        
        `alert( user && user.address && user.address.number );`
        
        : 값 없다면 `undefined` 반환
        

- `?.`은 `?.`'앞’의 평가 대상이 `undefined`나 `null`이면 평가를 멈추고 `undefined`를 반환

```jsx
let obj = {
  age: {
    name: "jiwoo",
  },
};

alert(obj.age?.name); 
```

# **prompt**

안내 메세지 + 입력 창 띄우고, 입력값 저장

## 생성

`prompt("안내 메세지", "기본 입력값(생략가능)")`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/7aec5df6-4b82-456e-8753-5e8ef0c96f5b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/26ad00c849fe490da9cb94bb82907b25/7aec5df6-4b82-456e-8753-5e8ef0c96f5b.png)

- `취소` 클릭 → “null”
- 입력x `확인` 클릭 → 빈 string (`''`)

- 입력값은 string으로 반환됨  ex) ‘12’ (숫자 아님)
- 숫자형 값을 받고 싶다면 앞에 + 붙여줌
    
    ex) `+prompt("숫자를 입력하세요","")`
    
    여기에 숫자 아닌 형태 입력 → `NaN`
    

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

## for...in 반복문

`for (var key in object) {~;}`

- 객체의 열거 가능한 prop을 순회해줌
- 변수를 통해 key에 접근 (value에는 직접 접근 불가)
- 빈 obj일 시, 실행되지 않고 빠져나감
- 일반 객체가 아닌 배열에는 되도록 사용X (느리고 적절하지 않음)
- 객체의 정렬순서는 추가순이 아님
    - 정수 prop - 자동 정렬 ([설명](https://ko.javascript.info/object))
    - 이외 propr - 추가한 순서대로 정렬
    

```jsx
let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for (let key in user) { 
  alert( key );  // name, age, isAdmin 연거푸 실행
  alert( user[key] ); // John, 30, true
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