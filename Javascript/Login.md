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

`obj.preventDefault();`

- 기본 행동이 발생하는 것은 막음
- 내가 브라우저의 모든 것을 컨트롤하게 함
- 기본 동작 종류

① form(submit) : 새로고침

②  (click) : link로 이동

# #4.4

- **css 이용해서 요소 숨기기**

(css) `.class-name { **display: none;** }` 추가

→ 어떤 요소든 class에 hidden 더해주면, 숨기게 됨

- **form 입력하면, 숨기고 입력값 출력하기**

① (html) form & 입력하고 나올 요소추가

(내용 없이/ `class="**hidden**"`포함)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/cb9da114-198e-40c1-b160-e7c09975e760.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/cb9da114-198e-40c1-b160-e7c09975e760.png)

② (css) `.hidden { **display: none;** }` 추가

③ (js) “click” event fnc 작성

- form 기본 동작 막고 `event.preventDefault();`
- form의 class에 hidden 추가 `.classList.add("hidden");`
- input 값에 var 할당 `const username = input-name.value;`
- 차후 요소 명령문 (아래선 obj.innerText = ~; )
- 차후 요소 “hidden” 삭제 `obj.classList.remove("hidden");`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/28e76452-fd08-448a-85cb-ad3f38bf28c1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/28e76452-fd08-448a-85cb-ad3f38bf28c1.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/94af37dd-c511-430d-bc07-6c0c00f47e80.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/94af37dd-c511-430d-bc07-6c0c00f47e80.png)

↳ 중복되는 부분이 있다면, var 할당하는 것이 좋다!

+ string만 포함된 var는 대문자로 표기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/72abfd04-3ea5-42b7-87e1-4c6237fdb4df.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/72abfd04-3ea5-42b7-87e1-4c6237fdb4df.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/dfff1d95-bacc-46d9-9c7f-9ca5fb4f5d8b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/dfff1d95-bacc-46d9-9c7f-9ca5fb4f5d8b.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/64e01644-1ddd-430f-9fa3-3def2c605838.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/64e01644-1ddd-430f-9fa3-3def2c605838.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/093fe49c-c25b-4fb7-a148-3870a89b6a21.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/093fe49c-c25b-4fb7-a148-3870a89b6a21.png)

↳ string이 잘 합쳐져서 출력됨

- —————————————————————————————————

# **#4.5**

# LocalStorage

브라우저에 정보 저장하는 기능 (새로고침해도 남아있는)

array는 저장되지 않는다 → text로 저장됨 (a,b,c…)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/f3be0839-935b-4bba-a648-e64f8b9ed85f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/f3be0839-935b-4bba-a648-e64f8b9ed85f.png)

- 이미 존재하고, 정의되어 있음

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/74e8c271-539d-498c-a5f1-ef92d9e3dcde.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/74e8c271-539d-498c-a5f1-ef92d9e3dcde.png)

- 개발자도구 → console → Application → Local Storage에서 확인
- **method**
- `localStorage.**setItem**("key-name", var)` 새로운 항목 세팅
- `localStorage.**getItem**("key-name")` 위의 set값 불러옴
- `localStorage.**removeItem**("key-name")` 저장된 값 지우기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/9cb56671-9ff8-40ac-9f95-a8e7f2cf8a11.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/9cb56671-9ff8-40ac-9f95-a8e7f2cf8a11.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/dfc17bcc-e3e2-4654-a3eb-c4dbaaca78f2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/dfc17bcc-e3e2-4654-a3eb-c4dbaaca78f2.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/05f84fca-8c10-4efb-bb29-ee08596892bc.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/05f84fca-8c10-4efb-bb29-ee08596892bc.png)

- —————————————————————————————————

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