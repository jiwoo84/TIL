# todo

[→ Open in Slid](https://slid.cc/docs/b7e556ebf51044439e19daccab34cee2)

---

# JSON

- `JSON.stringfy()`

json 객체를 string으로 변환

(arr를 넣으면, “array” 이렇게 자체를 string으로 변환함)

```jsx
const arr = [a, b, c];
const string-arr = JSON.stringfy(arr);

console.log(string-arr)
// "[a, b, c]" (arr 자체를 string으로 변환)
```

- ****`JSON.parse()`

string 객체를 json 객체로 변환

가지고 있는 data type을 벗기고, json 객체로 만들어줌

(“array” (string) → array)

# ToDo-List 만들기

```html
<ul id="todo-list"></ul>
```

## 1. **input 입력 → 비워주기**

```jsx
const toDoForm = document.getElementById("todo-form");
const toDoInput = toDoForm.querySelector("input");
const toDoList = document.getElementById("todo-list");

function handleToDoSubmit(event) {  // submit시, 동작 fnc
  event.preventDefault();           // 기본동작 막고
  const newTodo = toDoInput.value;  // input값 변수에 저장
  toDoInput.value = "";            // input 창 비워줌
}

toDoForm.addEventListener("submit", handleToDoSubmit);
```

- input값 변수에 저장 후, `todoInput.value ="";` 하면 newTodo값 없어짐?
    
    아님. `const newTodo = toDoInput.value;` 은 “input값”을 새로운 변수에 복사하는 것. 이후에 input.value를 아무리 변경해도 newTodo는 변동x
    

## 2. **입력 리스트 화면에 출력**

```jsx
const toDoForm = document.getElementById("todo-form");
const toDoInput = toDoForm.querySelector("input");
const toDoList = document.getElementById("todo-list");

function paintTodo(newTodo) {               // 입력값 인자로 전달받음
  const li = document.createElement("li"); 
  const span = document.createElement("span"); // list 목록 만들기
	span.innerText = newTodo;                   // 목록에 내용(arg) 넣기
  li.appendChild(span);                        // 목록 li 안에 넣기
  toDoList.appendChild(li);                   // ul 안에 li 넣기
}

function handleToDoSubmit(event) {
  event.preventDefault();
  const newTodo = toDoInput.value;
  toDoInput.value = "";
  paintTodo(newTodo);
	// todo-list 화면에 출력하는 fnc호출 (입력값 인자로 전달)
}

toDoForm.addEventListener("submit", handleToDoSubmit);
```

![내용 입력하면, 이렇게 input 밑에 목록 생성됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/801c2aad-6cd9-4e02-92cf-109aba695d20.png)

내용 입력하면, 이렇게 input 밑에 목록 생성됨

## 3. **삭제 버튼 만들기**

span으로 목록 만들기랑 똑같음

```jsx
function paintTodo(newTodo) {
  const li = document.createElement("li");
  const span = document.createElement("span");
  span.innerText = newTodo;
  const button = document.createElement("button"); // btn 생성
  button.innerText = "X";                          // btn 안 내용
  li.appendChild(span);
  li.appendChild(btn);
  toDoList.appendChild(li);
}
```

## 4. 삭제 버튼 활성화

 어떤 botton 클릭한지 알기 위해 `event.target` 활용

### `event.target`

이벤트가 발생한 대상 객체를 가리킴

### **`Node.parentElement`**

node의 부모 element를 가리킴

(삭제 대상) 클릭한 node의 부모= `event.target.parentElement`

```jsx
function deleteTodo(event) {
  const li = event.target.parentElement; // 클릭한 btn의 부모
  li.remove();                           // 부모 삭제
}

function paintTodo(newTodo) {
  const li = document.createElement("li");
  const span = document.createElement("span");
  span.innerText = newTodo;
  const button = document.createElement("button");
  button.innerText = "X";
  button.addEventListener("click", deleteTodo); // btn에 click fnc
  li.appendChild(span);
  li.appendChild(button);
  toDoList.appendChild(li);
}
```

## 3. **입력한 리스트 저장하기**

① 리스트 저장될 array 제작

`const arr-name = **[ ]**;`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/3751f92e-dac2-4207-9487-df654e06e429.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/3751f92e-dac2-4207-9487-df654e06e429.png)

② 값 입력하면 array에 추가되도록 작성 (event fnc에 추가)

`arr-name.**push**(event);`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/88b09b69-31c7-4749-b115-3ebec2db2c02.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/88b09b69-31c7-4749-b115-3ebec2db2c02.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/b93ac647-e5c6-4e1d-a08a-bcb089a5fb88.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/b93ac647-e5c6-4e1d-a08a-bcb089a5fb88.png)

↳ input에 입력하면, array에 값이 추가됨

③ 입력값(array)를 localStorage에 저장

: localStorage는 array 저장 X (그냥 text로 저장됨)

∵ string으로 바꿔서 저장할 것

`function fnc-name() {`

`localStorage.setItem("key-name", **JSON.stringify**(arr-name)); }`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/7e6b05cb-08de-4644-8b7e-c740ac66d92b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/7e6b05cb-08de-4644-8b7e-c740ac66d92b.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ccb055bc-afba-4565-a683-067fd5f6b176.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ccb055bc-afba-4565-a683-067fd5f6b176.png)

↳ array의 형태로 저장된 value

(엄밀히 말해 array의 형태를 지닌 string이다. array 아님)

+ array 자체를 localStorage에 저장할 시

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/0613d533-6360-4698-82e9-26c399d72d8f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/0613d533-6360-4698-82e9-26c399d72d8f.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/f507e91a-e25a-47f1-9f3b-e25b90a64d0e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/f507e91a-e25a-47f1-9f3b-e25b90a64d0e.png)

↳ arr 형태 없어지고 text(a,b,c…) 로 저장

④ 위 fnc을 event fnc에 추가

(값이 array에 추가되고, 그 후에 저장fnc 실행되야 함)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/6e8f5665-af8a-48ad-85db-c9abf8ef5361.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/6e8f5665-af8a-48ad-85db-c9abf8ef5361.png)

**4. 새로고침 후, 저장된 array의 item들 다시 출력**

① 저장된 값에 var 할당

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/6a741747-c4d5-4194-ab7d-48280134aca1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/6a741747-c4d5-4194-ab7d-48280134aca1.png)

② 조건문 작성: 저장된 값이 있다면, 그거 다시 출력할 것

- localStorage 안 “array” (string) → array로 변환, var 할당
- `*JOSON.parse**(localStorage-value)`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/798678b4-59c5-4298-aa98-fb33fedf6158.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/798678b4-59c5-4298-aa98-fb33fedf6158.png)

↳ 위 조건문은 if (savedToDos) 까지만 써도 가능함

- array 안의 각 item 모두 fnc 실행하게 설정

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/e3ea83eb-2b7f-45c6-85c5-2790a5fe625a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/e3ea83eb-2b7f-45c6-85c5-2790a5fe625a.png)

forEach 사용해서, array의 item마다

paintToDo(출력 fnc)가 실행되게끔 함.

- —————————————————————————————————

# Array.prototype.forEach()

`function fnc-name(item) {명령문}`

`array.**forEach**(fnc-name);`

- array의 각 item → fnc의 argument로 전달
- array의 각 item에 fnc 실행 (순서대로 1번씩 실행)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/062de4a7-944c-4219-82ca-237b0059a880.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/062de4a7-944c-4219-82ca-237b0059a880.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/140a95a7-48ae-4a8e-8e0c-c2dcf8f77629.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/140a95a7-48ae-4a8e-8e0c-c2dcf8f77629.png)

↳ 현재 array 값 = [“a”, “b”, “c” …]

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/f8916236-b492-47d6-86a9-0a879665e9a1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/f8916236-b492-47d6-86a9-0a879665e9a1.png)

↳ 이렇게 한번씩 다 실행된다

**5. 값 입력 후, 새로고침** → **새로운 값 입력 → 이전 값 + 새로운 값**

(새로운 값 입력하고 새로고침하면 이전 값 없어지고

새로운 값만 출력되는 array 덮어쓰기 현상의 해결 방법)

- **문제점**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/a14d401e-201e-4abf-aa8a-651ed839b6c4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/a14d401e-201e-4abf-aa8a-651ed839b6c4.png)

새로고침 후, localStorage에 저장되어있는 이전 값들

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/3f623ec6-5b98-4f10-874e-45e689215232.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/3f623ec6-5b98-4f10-874e-45e689215232.png)

새로운 값을 입력하자, 이전 값이 사라지고

새로운 값만 array 에 입력되어 덮어써짐 ㅠㅠ

- **원인**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/da523e0a-4b36-4b7e-974b-55a5be394fec.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/da523e0a-4b36-4b7e-974b-55a5be394fec.png)

값을 입력(event 발생) → 저장하는 fnc 실행

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/3236b506-72e6-4051-a56c-41aeaeafa655.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/3236b506-72e6-4051-a56c-41aeaeafa655.png)

array를 저장하는데, array 값이 비어있음

이 과정에서 [“a”, “b”, “c”] 로 이전 값이 채워져 있어도

다시 입력하면 []에서 추가되니까 [“d”, “e”, “f” …]가 됨

- **해결**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/c6fd04dc-2765-4936-8d33-72e2d758a262.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/c6fd04dc-2765-4936-8d33-72e2d758a262.png)

const → let 으로 변경 가능하게 설정

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/c8b7de09-77ed-4c26-9ae0-42009831894e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/c8b7de09-77ed-4c26-9ae0-42009831894e.png)

(저장값을 array로 변환하고 나서)

array를 저장값으로 복원

**6. btn 눌러 삭제** → **localStorage에서도 삭제**

(localStorage에 id 저장하기)

- html의 관점에서, 삭제btn “click” 하면

어떤 el 삭제해야하는지 알 수 있지만

저장된 array 중, 어떤 text를 삭제해야 하는지는 알 수 없음

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b7e556ebf51044439e19daccab34cee2/12785306-4d0f-4cfb-b50f-97abfb43b7a2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b7e556ebf51044439e19daccab34cee2/12785306-4d0f-4cfb-b50f-97abfb43b7a2.png)

① 입력한 값을 array에 obj 형식으로 저장할 것

ex) `[ { **text**: 입력값, **id**: 랜덤 숫자} , { **text**: 입력값, **id**: 랜덤 숫자} …]`

↳ 입력값은 text, localStorage에서 특정할 id 부여함

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/1866f573-5898-4bda-bd42-7666ba741f02.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/1866f573-5898-4bda-bd42-7666ba741f02.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/3d2f25c7-98bb-4b3f-be78-9e9a4d6b0ae2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/3d2f25c7-98bb-4b3f-be78-9e9a4d6b0ae2.png)

↳ hello 라고 입력하면, 이렇게 저장됨

+ `Date.now()`

밀리초(1/1000초)를 제공하는 함수

편하게 랜덤한 숫자 얻을 수 있다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/fc693684-d732-469e-aa85-ab77c714c901.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/fc693684-d732-469e-aa85-ab77c714c901.png)

② obj의 id를 html에 넣기

- 출력fnc에도 obj 형태로 넣기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/b3ba6fb3-b8ed-4fa3-96ef-b6e156cf772d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/b3ba6fb3-b8ed-4fa3-96ef-b6e156cf772d.png)

- span에 입력되는 값, 수정 (.text 붙임)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ae0530ed-1f34-4fd4-a9cb-7d0635e67742.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ae0530ed-1f34-4fd4-a9cb-7d0635e67742.png)

- li 에 id 부여

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/421424c8-6096-4f27-aaf2-886a82ce8d22.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/421424c8-6096-4f27-aaf2-886a82ce8d22.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/bc2bbd54-75d9-4a38-a773-bd8704331d36.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/bc2bbd54-75d9-4a38-a773-bd8704331d36.png)

↳ html 속, li에 id가 부여된다

- —————————————————————————————————

# Array.prototype.filter()

`function fnc-name(argument){ **return** **arg비교조건** };`

`array.**filter**(fnc-name);`

= `array.**filter**((arg) **=>** arg비교조건);`(간략)

: array의 모든 item에 fnc 실행

→ return - true : 값 유지

- false: 값 유지X

→ 남은 값 모아서 새로운 array 형성 (∵ 선택옵션)

+ array 자체를 변화시키지는 않음

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/78d98027-cf38-4713-a197-a2197b42ddb3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/78d98027-cf38-4713-a197-a2197b42ddb3.png)

↳ `3(item) !== 3` = false 니까 array에서 빠짐

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ae5c376d-a8e6-4dad-be52-9314523b0a32.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ae5c376d-a8e6-4dad-be52-9314523b0a32.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/7f41488a-d657-4f8d-8a53-2399b904acda.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/7f41488a-d657-4f8d-8a53-2399b904acda.png)

7. btn 눌러 삭제한 값, 새로고침 후에도 유지하기

: 삭제fnc에 filter 이용해서 삭제 후 array 만들고, 저장

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/10562559-a19e-46a5-8ed2-732b8232fe0c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/10562559-a19e-46a5-8ed2-732b8232fe0c.png)

① array-item.id = li.id (삭제btn 클릭된)면 새 array에서 제외

★`typeof li.id` = string

li.id 의 타입을 보면 숫자가 아닌 string이라서 비교 불가

숫자로 바꿔준 뒤, item.id 와 비교한다

**왜인지는 모르겠음 질문후 다시 글 쓸 예정**

② 저장fnc 잊지 말아야함. 그래야 localStorage에 삭제되고

새로운 array가 업데이트 된다.