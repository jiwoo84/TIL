# todo

[→ Open in Slid](https://slid.cc/docs/b7e556ebf51044439e19daccab34cee2)

---

# JSON

- `**JSON.stringfy()**`

json 객체를 string으로 변환

(arr를 넣으면, “array” 이렇게 자체를 string으로 변환함)

```jsx
const arr = [a, b, c];
const string-arr = JSON.stringfy(arr);

console.log(string-arr)
// "[a, b, c]" (arr 자체를 string으로 변환)
```

- `**JSON.parse()**`

string 객체를 json 객체로 변환

가지고 있는 data type을 벗기고, json 객체로 만들어줌

(“array” (string) → array)

# array.prototype.forEach

(`function fnc-name (item) {명령어};`)

`array.forEach(fnc-name);`

= `array.forEach( (item) ⇒ 명령어 );`  (fnc를 아예 포함한 간단 버전)

- array의 각 항목이 fnc의 argument로 전달
- array의 각 항목에 fnc 실행 (순서대로 1번씩 실행)

- 예시
    
    ```jsx
    const arr = [1, 2, 3];
    
    arr.forEach((item) => console.log("This is ", item));
    ```
    
    ![이렇게 한번씩 다 실행된다](todo%2085d0c/Untitled.png)
    
    이렇게 한번씩 다 실행된다
    

# Array.prototype.filter()

`function fnc-name(parameter){ return arg비교조건 };`

`array.filter(fnc-name);`

= `array.filter((arg) => arg비교조건);` (간략)

- 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환
- array의 모든 item에 fnc 실행 후, 반환값
    - true : 항목 유지
    - false: 항목 유지 X
    
     ∴ 통과한 항목으로 array 형성 (=선택옵션)
    
- array 자체를 변화시키지는 않고 새롭게 형성

```jsx
function test(item) {
	return item !== 3
}
[1,2,3,4,5].filter(test);

[1,2,3,4,5].filter((item) => item !== 3);

// 위에 두 코드 모두 [1,2,4,5] 반환
```

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

## 3. **입력값 arry로 저장 → localStorage에 저장**

값 여러개를 한 묶음으로 저장해야 하니까 array 형식으로 저장

```jsx
const toDos = [];  // 1. inpu값 저장할 array 생성

function deleteTodo(event) {
  const li = event.target.parentElement;
  li.remove();
}

function savedToDo() { 
  localStorage.setItem("todos", JSON.stringify(toDos));
	// 4. array를 string으로 변경해 localStorage 저장 (아래 설명)
}

function paintToDo(newTodo) {
  const li = document.createElement("li");
  const span = document.createElement("span");
  span.innerText = newTodo;
  const button = document.createElement("button");
  button.innerText = "X";
  button.addEventListener("click", deleteTodo);
  li.appendChild(span);
  li.appendChild(button);
  toDoList.appendChild(li);
}

function handleToDoSubmit(event) {
  event.preventDefault();
  const newTodo = toDoInput.value;
  toDoInput.value = "";
  toDos.push(newTodo);  // 2. input값 입력시 array에 추가
  paintToDo(newTodo);
  savedToDo();          // 3. array를 localStorage에 저장 fnc 실행
}

toDoForm.addEventListener("submit", handleToDoSubmit);
```

localStorage는 array 자체로 저장 안됨

- ex) 그냥 array 자체로 저장 시
    
    `localStorage.setItem("todos", toDos);`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/f507e91a-e25a-47f1-9f3b-e25b90a64d0e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/f507e91a-e25a-47f1-9f3b-e25b90a64d0e.png)
    
    [a, b, c] → a, b, c / array 없어지고 text로 저장됨
    
- ∴ 다시 array 상태로 꺼내쓰려면 arry 자체를 string으로 바꿔서 저장
    
    `localStorage.setItem("todos", JSON.stringify(toDos));`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ccb055bc-afba-4565-a683-067fd5f6b176.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/ccb055bc-afba-4565-a683-067fd5f6b176.png)
    
    array의 형태로 저장된 value
    
    (엄밀히 말해 array의 형태를 지닌 string이다. array 아님)
    

## 4. **새로고침 후, localStorage에 저장된 값 재출력**

```jsx
const savedToDos = localStorage.getItem(TODOS_KEY);
// localStorage에 저장된 값 불러와서 변수 할당

if (savedToDos !== null) {                // 저장된 값이 있다면 실행
  const parsedToDOs = JSON.parse(savedToDos); //string을 array로 변경
  parsedToDOs.forEach(paintToDo);    // array 각 값 출력하는 fnc 적용
}
```

`if (savedToDos !== null)` = `if (savedToDos)` 까지만 써도 가능

- **문제점**
    
    새로고침 후, 새로운 값을 입력하면 이전 값이 localStorage에서 사라짐
    
    ![새로고침 후, localStorage에 저장되어있는 이전 값들](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/a14d401e-201e-4abf-aa8a-651ed839b6c4.png)
    
    새로고침 후, localStorage에 저장되어있는 이전 값들
    
    ![새로운 값을 입력하자, 이전 값이 사라지고 새로운 값만 입력되어 덮어써짐](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b7e556ebf51044439e19daccab34cee2/3f623ec6-5b98-4f10-874e-45e689215232.png)
    
    새로운 값을 입력하자, 이전 값이 사라지고 새로운 값만 입력되어 덮어써짐
    

- **원인**
    
    input 입력시 실행되는 fnc
    
    ```jsx
    const toDos = [];  // 빈 상태
    
    function handleToDoSubmit(event) {  // input 입력시 실행되는 fnc
      event.preventDefault();
      const newTodo = toDoInput.value;
      toDoInput.value = "";
      toDos.push(newTodo);  // ① 여기서 toDos(array)가 초기화 됨
      paintToDo(newTodo);
      savedToDo(); // ② 그대로 localStorage에 저장
    }
    ```
    
    새로고침하고 새로운 입력이 없다면 localStorage 속 값이 그대로 있지만 input 하는 순간, ①toDos(array)가 비어있는 상태에서 값 추가되고 ②그대로 localStorage에 저장된다
    
    이 과정에서 [“a”, “b”, “c”] 로 이전 값이 채워져 있어도 다시 입력하면 []에서 추가되니까 [“d”, “e”, “f” …]가 됨
    
- **해결**

```jsx
let toDos = [];  // const → let 추후 변경 가능하게 함

if (savedToDos !== null) {
  const parsedToDOs = JSON.parse(savedToDos);
  toDos = parsedToDOs;  // toDos에 저장되어 있던 값 넣어줌
  parsedToDOs.forEach(paintToDo);
}
```

## **6. btn 눌러 삭제** → **localStorage에서도 삭제**

- **입력값을 단순 text 아닌 obj (`{id:~, text: ~}`) 형식으로 저장**
    
    삭제btn “click” 하면 어떤 el 삭제해야하는지 알 수 있지만 저장된 array 중, 어떤 항목을 삭제해야 하는지는 알 수 없기 때문에 id도 함께 생성하고 html에도 넣어준다 (`element.id = id-name`)
    
    ```jsx
    function paintToDo(newTodo) {
      const li = document.createElement("li");
      li.id = newTodo.id; // delete fnc을 위해 li에 id 생성
      const span = document.createElement("span");
      span.innerText = newTodo.text; // text 값을 출력함
      const button = document.createElement("button");
      button.innerText = "X";
      button.addEventListener("click", deleteTodo);
      li.appendChild(span);
      li.appendChild(button);
      toDoList.appendChild(li);
    }
    
    function handleToDoSubmit(event) {
      event.preventDefault();
      const newTodo = toDoInput.value;
      toDoInput.value = "";
      const newTodoObj = {  // 1. id 포함할 obj 형성
        text: newTodo,
        id: Date.now(),   // 2. id는 랜덤한 수면 되니까 편하게 date 활용
      };
      toDos.push(newTodoObj); // 3. array에도 obj 자체로 넣어줌
      paintToDo(newTodoObj); 
    // 4. localStorage에 obj로 저장되고, 새로고침 후 불러와서 출력할테니
    //    paintToDo도 변경해야함
      savedToDo();
    }
    ```
    
    - `Date.now()`
        
        밀리초(1/1000초)를 제공하는 함수
        
        편하게 랜덤한 숫자 얻을 수 있다
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/fc693684-d732-469e-aa85-ab77c714c901.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b7e556ebf51044439e19daccab34cee2/fc693684-d732-469e-aa85-ab77c714c901.png)
        

- **btn delete fnc 수정**
    
    filter 이용해서 삭제 요소 빼고 새로운 array 만들어 저장
    
    ```jsx
    let toDos = [];
    const TODOS_KEY = "todos";
    
    function deleteTodo(event) {
      const li = event.target.parentElement;
      toDos = toDos.filter((toDO) => toDO.id !== parseInt(li.id));
    	// 삭제요소 id를 이용해서 새로운 배열 만들어 저장
      li.remove();
      savedToDo();  // 바뀐 배열 locasStorage에 저장
    }
    
    function savedToDo() {
      localStorage.setItem(TODOS_KEY, JSON.stringify(toDos));
    }
    ```
    
    - parseInt 사용 이유
        
        `toDos = toDos.filter((toDO) => toDO.id !== li.id);` 하면 실행 안됨.
        
        왜냐면 `typeof toDo.id = **number**` / `typeof li.id = **string**`
        
        toDo.id는 배열 안에 저장된 숫자/ li.id는 html DOM 상에서 id 값을 가져온것 (DOM의 id는 문자열로 인식됨)
        
        ∴ `parseInt(li.id)`해서 num로 바꾼 후에 toDos.id와 비교해야 한다
        
    - `toDos = toDos.filter((toDO) => toDO.id != li.id);` 이것도 가능
        
        `!==` → `!=` 으로 바꿔서 값만 비교되게 해도 된다
        
        (니꼬 의견은 아니고 댓글에서 발견)