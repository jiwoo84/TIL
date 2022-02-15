# Login

[→ Open in Slid](https://slid.cc/docs/1ee8946e1ebd4ed0bc1abd974af2bc6c)

---

## **`input.value`**

요소의 입력값 반환

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/1ee8946e1ebd4ed0bc1abd974af2bc6c/7b802605-34a6-40aa-81db-1387a73f2933.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/1ee8946e1ebd4ed0bc1abd974af2bc6c/7b802605-34a6-40aa-81db-1387a73f2933.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/aa6cc629-1a82-4043-b521-54112b614321.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/aa6cc629-1a82-4043-b521-54112b614321.png)

## `obj.length` (prop)

string의 길이(n) 반환

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/d7a352b4-716c-471c-bb51-87fa7c7970dd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/d7a352b4-716c-471c-bb51-87fa7c7970dd.png)

이런식으로 조건문에 활용하기도 한다

## preventDefault (fnc)

`event.preventDefault();`

- 기본 동작의 실행을 막음
- 적용하면 브라우저의 모든 것을 컨트롤할 수 있음

- **기본 동작 종류**
    - `<form>`의 submit(event) : 새로고침, 값 서버에 전송
        - `<input>` 필드에서 enter
        - `<input type="submit">` or `<button>` 클릭
    - `<a>` 를 click : link로 이동

```jsx
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");

function onLoginSubmit(event) {
  event.preventDefault(); // 이렇게 쓰면 input의 값 console된다
  console.log(loginInput.value);
}

loginForm.addEventListener("submit", onLoginSubmit);
```

## **css 이용해서 요소 숨기기**

1. (css) `.hidden {display: none;}`
    - 알아보기 쉽게 classname은 hidden으로 설정
    - 어떤 요소든 class에 hidden 더해주면, 숨게 됨
    
2. 숨어있다가 나온다면
    - (html) 해당 요소에 `class="hidden"` 작성
    - (js) 나오는 fnc에 `obj.classList.remove("hidden");` 작성
    
    나와있다가 숨는다면
    
    - (js) 숨는 fnc에 `obj.classList.add("hidden");` 작성

```jsx
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");
const greeting = document.querySelector(".greeting");

const HIDDEN_CLASSNAME = "hidden";

function onLoginSubmit(event) {
  event.preventDefault();
  loginForm.classList.add(HIDDEN_CLASSNAME);
  const username = loginInput.value;
  greeting.classList.remove(HIDDEN_CLASSNAME);
  greeting.innerText = `Hello {$username}`;
}

loginForm.addEventListener("submit", onLoginSubmit);
```

# LocalStorage

브라우저에 정보 저장 (새로고침해도 남아있음)

text로 저장 (array는 저장X)

## 확인하기

개발자도구 → console → Application → Local Storage

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/74e8c271-539d-498c-a5f1-ef92d9e3dcde.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/74e8c271-539d-498c-a5f1-ef92d9e3dcde.png)

## **method**

- 새로운 항목 세팅
    
    `localStorage.setItem("key", 값)` 
    
- 저장값 불러옴
    
    `localStorage.getItem("key")` 
    
- 저장값 삭제
    
    `localStorage.removeItem("key")`
    

# #4.6

- **LocalStorage 정보 유무 확인**

localStorage 정보 값 없다면

→ `localStorage.**getItem**("key-name");` = null

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/a8adfd23-fb2a-4cf3-9451-d8e5c57df127.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/a8adfd23-fb2a-4cf3-9451-d8e5c57df127.png)

↳ 이를 조건문에 이용해서, 명령문 실행 가능

(`const **savedUsername** = localStorage.getItem("key-name");`)

- **LocalStorage 값에 따라, 명령문 달리하기**

ex) 새로고침 후, LocalStorage 값이 저장되어 아래 상태 유지하기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/64e01644-1ddd-430f-9fa3-3def2c605838.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/64e01644-1ddd-430f-9fa3-3def2c605838.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/093fe49c-c25b-4fb7-a148-3870a89b6a21.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/093fe49c-c25b-4fb7-a148-3870a89b6a21.png)

**①** 모든 el에 `display = none;` 가진 class 추가 (hidden)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/3d1e5593-3417-4350-b206-6bfd9d1e7cc3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/3d1e5593-3417-4350-b206-6bfd9d1e7cc3.png)

**②** 조건문 선언

(localStorage 값 없을 때 → form 숨김 없애고 & event fnc실행)

- `*if** (**localStorage.getItem("key-name") === null**) {`

`form.classList**.remove("hidden")**;`

`form.addEventListener("event", event-fnc); }`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/6465f283-6d61-4c49-9387-9b0997415c23.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/6465f283-6d61-4c49-9387-9b0997415c23.png)

↳ localStorage.getItem(“key-name”)에 var 할당해도 됨

**③** else 조건문 선언

(localStorage 값 있을 때 → 차후 요소 숨김 없애고 & 명령문)

- `*else** { 차후 요소.classList.**remove("hidden")**;`

`차후 요소 명령문; }`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/67da446c-f164-4bc7-b7b2-98643812697a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/67da446c-f164-4bc7-b7b2-98643812697a.png)

↳ **Q**. 새로고침 후, 명령문 출력값에

localStorage.getItem(“key-name”) (savedUsername) 가 아닌

input.value (input에 입력한 값)을 쓰면 안되나요?

**A**. 안돼. input에서 받은 값이 새로고침 전에는 input.value 지만

새로고침 후에는 localStorage.getItem(“key-name”) 에

저장된 값이기 때문이다. input.value을 쓴다면 "" 빈 값이 출력.

+ (event-fnc & else의 fnc 같다면) var 할당해서 코드 줄이기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/e6ebea2e-7c25-444e-b4e1-229900d1c10d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/e6ebea2e-7c25-444e-b4e1-229900d1c10d.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/793f8416-87ee-484a-9e16-d6b53881a2d5.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/793f8416-87ee-484a-9e16-d6b53881a2d5.png)

↳ 이렇게 두줄이 중복된다

input입력 후, 실행되는 명령과

새로고침 후, 실행되는 명령이 같다면 그렇다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/cb2eb76c-e3e0-4dd8-b289-f864d7ff542b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/cb2eb76c-e3e0-4dd8-b289-f864d7ff542b.png)

변수 할당해주고, arr에 알맞는 var 넣어주면 완성!

+ fnc의 arr 넣을 필요 없다면 수정 가능

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/5e664f58-07c3-444c-8ff5-d9f9c3ed7d41.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/5e664f58-07c3-444c-8ff5-d9f9c3ed7d41.png)

↳ paintGreeting의 arr을 넣을 필요가 없음

밑줄 친 부분 고쳐준다

그럼 localStorage.getItem 을 두 번 불러오긴 함

( 니코는 그래서 수정 전을 더 선호 but 난 이게 더 나은듯)