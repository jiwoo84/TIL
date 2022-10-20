# Node.js

[HTTP 설명](https://www.notion.so/Network-8d8ba76c01434103bc82a474fdf61677)

- 노드 터미널 다루기
    - `node '파일명’`  : 서버에 코드 전송
    - `localhost:포트번호` (브라우저 주소창에 입력)
        
        해당 포트번호 서버에 들어가기
        
    - 터미널에 ctrl+C 하면 종료

# Axio

(Asynchronous JavaScript and XML)

웹 브라우저와 Node.js를 위한 HTTP 비동기 통신 라이브러리 

⇒ 백엔드와 프론트엔드 간 통신을 쉽게 하기 위해 사용되는 것

- Ajax와 유사하며 API를 이용한 통신에 주로 사용
    
    Ajax는 브라우저가 가지고 있는 XMLHttpRequest 객체를 이용하여 화면 전체를 새로 고침 하지 않고 변경된 일부 데이터만 로드하는 비동기 처리가 가능
    
- 비동기 통신 라이브러리 사용하는 이유
    
    동기적으로 실행된다면 모든 코드가 순차적으로 처리되야 하기 때문에 순서를 신경써서 작성해야함 → 코드가 복잡해짐
    

## Axios 사용법

---

### 1. 모듈 설치

index.html에 두 가지 스크립트 추가하면 라이브러리 사용 가능

```jsx
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

### 2. 데이터 요청

`axios.get(url[,option])`

- option : 요청 메서드 커스텀 가능
    
    ```jsx
    axios(url, {
      method: "get", // 다른 옵션도 가능합니다 (post, put, delete, etc.)
      headers: {},
      data: {},
    	responseType: "json" // 기본 데이터타입 설정 + 'arraybuffer', 'document', 'blob', 'text', 'stream'
    });
    ```
    
- HTTP 메서드 붙여서 실행 가능 ex) `axios.get(url[,option])`
- 프라미스

### fetch와의 차이점

1. **응답 데이터 타입**: 기본으로 **JSON** (fetch - `json()`으로 변환 필요)
2. POST로 데이터 전송:  자동으로 **데이터를 문자열로 변환**함 
    
    (fetch - `JSON.stringify()`으로 변환 필요)
    
3. 별도의 import나 설치 필요 (fetch - JS에 내장되어 있어 불필요)
4. 브라우저 호환성 뛰어남 (fetch - 일부 IE에서 지원하지 않을 수 있음)

## 에러 처리

---

### HTTP 에러

axios는 상태코드가 2xx 범위를 넘어가면 거부(reject)함

에러 객체에 응답(response) or 요청(request) 프로퍼티가 포함되어 있는지 확인하여 에러에 대한 자세한 정보를 확인 가능

- `error.response` :  클라이언트가 2xx 범위를 벗어나는 상태 코드를 가진 에러 응답을 받았음을 나타냄
- `error.request` : 요청이 수행되었지만 클라이언트가 응답을 받지 못했음을 나타냄
- 요청 또는 응답 속성이 모두 없는 경우 ⇒ 네트워크 요청을 설정하는 동안 오류가 발생한 경우

```jsx
.catch((err) => {
// 에러 처리
	if (err.response) {
	// 요청이 이루어졌고 서버가 응답했을 경우
	//  404, 500

    const { status, config } = err.response;

    if (status === 404) {
      console.log(`${config.url} not found`);
    }
    if (status === 500) {
      console.log("Server error");
    }

  } else if (err.request) {
    // 요청이 이루어졌으나 서버에서 응답이 없었을 경우
    console.log("Error", err.message);
  } else {
    // 그 외 다른 에러
    console.log("Error", err.message);
  }
});
```

### 응답 시간 초과 / 요청 취소

내부적으로 제공되는 `timeout`속성을 사용하여 요청 종료까지의 시간 지정

```jsx
const url = "https://jsonplaceholder.typicode.com/todos";

axios
  .get(url, {
    timeout: 4000, // 기본 설정은 '0'입니다 (타임아웃 없음)
  })
  .then((response) => console.log(response.data))
  .catch((err) => { // 응답시간이 4000ms이 넘으면 catch로 넘어옴
    console.log(err.message);
  });
```

# Node.js

JS를 브라우저 이외 환경에서 실행 가능하게 해주는 플랫폼

- V8으로 빌드 된 이벤트 기반 자바스크립트 런타임
- 내장 HTTP 서버 라이브러리를 포함하고 있어 웹서버에서 아파치 등의 별도의 소프트웨어 없이 동작 가능

### 브라우저 vs Node.js

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled.png)

- 목적 : 웹페이지의 정보를 화면에 렌더링 / 브라우저 외부에서 JS 실행 환경 제공
- Wep API 사용하여 비동기 가능 / Web API 제공하지 않고 따로 Node의 API 존재
- html 요소를 객관화한 DOM을 직접 다룸 / 직접적으로 os, 파일, 프로세서에 접근 가능하기 때문에 브라우저보다 더 많은 기능 수행

### 라이브러리 vs 패키지 vs 모듈

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%201.png)

1. **라이브러리** : 패키지와 모듈의 묶음
    
    (표준 라이브러리 : 미리 만들어진 라이브러리, 바로 사용 가능)
    
2. **패키지** : 여러 모듈의 묶음, 특정 기능과 관련된 모듈이 묶여 패키지가 됨
    
    (npm = node package manager)
    
3. **모듈** : 변수와 함수로 구성된 소스코드 파일 (export, import로 재사용 가능)
- **노드는 프레임워크일까? ⇒ X (**노드는 단순히 자바스크립트 실행환경임)
    
    (프레임워크: 일종의 기본 템플릿)
    

### Node.js로 할 수 있는 것들

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%202.png)

## 특징

---

1. 자바스크립트 런타임 환경 (V8)
2. 싱글 스레드
3. non-blocking I/O (비동기)
4. Event-Driven

### 싱글 스레드

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%203.png)

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%204.png)

- 단점: 쓰레드 기반의 작업들의 효율이 떨어짐 ex) CPU 연산 작업
- 장점: 동작의 완료를 기다리지 않아도 되고 쓰레드가 늘어나지 않음 → 리소스 관리에 효율적

### 논블로킹

- blocking(동기) : I/O 할 때 완료될 때까지 실행 중지
- non-blocking(비동기) : I/O를 기다리지 않고 callback으로 넘긴 후 다음줄 실행

### Event-Driven

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%205.png)

이벤트를 통해서 등록한 콜백을 호출(브라우저 이벤트 처리와 동일) ⇒ 비동기 동작의 완료를 처리하는 방법

- 특정 동작을 실행 → 완료되면 실행할 함수 미리 등록 → 전혀 신경쓰지 않음 → 완료되면 미리 등록한 함수 실행

### 내부 구조

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%206.png)

- **V8** : memory heap, call stack, garbage collector로 구성
- Node.js Standard Library(모듈) : setTimeOut, fs, http 등의 표준 라이브러리 지원
- llhttp : HTTP 요청, 응답 구문 분석등에 사용
- c-ares : dns 모듈에서 사용되는 비동기 DNS 요청
- open-ssl : ssl, crypto 모듈에 사용되는 암호화
- zlib : 비동기 및 스트리밍으로 압축 및 압축 해제
- **Libuv** : Event Loop, Event Queue ⇒ 비동기 처리하는 곳
    - 노드는 싱글 스레드인데 어떻게 멀티 스레드처럼 비동기 동작을 처리할까?
        
        ⇒ c언어로 개발된 libuv는 시스템 커널을 이용하는데, 커널은 멀티 스레드를 이용
        
        - 이벤트 처리 과정
            1. node.js로 요청이 들어오면 들어온 요청은 event queue에 추가됩니다. 
            2. node.js의 이벤트 루프는 event queue를 살펴 들어온 요청이 있다면 선착순(first come first served) 요청이 처리됩니다.
            3. 요청은 internal C++ Thread Pool로 보내집니다. 이것은 libuv에서 개발된 이벤트 루프의 일부로 여러 요청을 수행할 수 있습니다. 동시에 이벤트 루프는 event queue에 요청이 있는지 계속해서 확인하면서 요청이 있다면 thread pool로 가져옵니다. 
            4. thread pool은 db 또는 file 또는 다른 서버 등에 보낸 요청을 수행합니다. 
            5. 수행을 마치면 콜백 함수를 실행시켜 이벤트 루프로 응답을 전달합니다. 
            6. 이벤트 루프는 응답을 클라이언트에 보냅니다. 
    
    <aside>
    📌 깊게 들어가서 libuv의 구조를 보면 멀티 스레드지만, 상위 레벨에서 추상화 된 JS는 싱글 스레드가 맞음
    
    </aside>
    
    ![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%207.png)
    

### V8 내부 구조

1. **Call Stack** : 작성된 함수가 등록되는 LIFO 스택
2. **Message Queue** : `setTimeout`같은 지연실행 함수를 등록하는 FIFO 큐. 콜스택이 비어있을 경우 등록된 함수를 콜스택에 추가
3. **Job Queue** : Promise에 등록된 콜백을 등록하는 FIFO 큐. 상위 함수가 종료되기 전에 (콜스택이 비어있지 않아도) 잡큐에 등록된 콜백을 콜스택에 추가
- 메시지큐의 작동 순서
    
    ![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%208.png)
    
    블럭 안에 있어도 맨 끝까지 모두 실행 후, 작동함
    
- 잡큐의 작동 순서
    
    ![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%209.png)
    
    상위 함수가 종료되기 전에 실행됨
    

# CommonJS

JS를 브라우저 외부에서 사용하기 위해 만들어진 **Node.js** 내장 모듈 시스템

### 모듈 시스템 있기 전에는…

즉시 실행 함수(IIFE)를 이용해 스코프를 정리했음

```jsx
// 즉시 실행 함수 생성
var adder = (function () {
  return {
    addOne: function (num) {
      return num + 1;
    },
    addTwo: function (num) {
      return num + 2;
    },
    addNumbers: function (nums) {
      return nums.reduce((agg, cur) => agg + cur, 0);
    },
  };
})();

// 이 파일을 다른 파일에서 <script>로 불러와서, 함수 그대로 사용
```

- 즉시 실행 함수
    1. 필요없는 전역 변수의 생성을 줄일 수 있음
    2. private한 변수를 만들 수 있음

## module 조작

---

### module

현재 모듈의 정보가 담긴 객체 

- 각 모듈마다 있는 private 지역변수 ⇒ module로만 접근 가능
- **module.exports**
    
    `require()` 호출하면 받는 값 ⇒ 객체 참조 변수 (현재 모듈 객체의 주소값)
    
    - 초기에 빈 객체로 생성
    - 전역 실행 컨텍스트 this에 참조됨

### 모듈 내보내기

<aside>
📌 **exports vs module.exports**

exports = module.exports의 참조값 = module.exports ⇒ `{}` (초기값)

</aside>

1. **exports**
    
    `exports.모듈이름 = 모듈`
    
    - `exports = {}`을 하면 맨 처음 생성된 module.exports와 다른 객체로 참조됨
2. **module.exports**
    
    `moduel.exports.모듈이름 = 모듈`
    
    - 모듈 여러 개 : `moduel.exports = { 모듈이름 : 모듈 , ... }`
        
        (아예 새로운 객체를 할당하는 것)
        

### 모듈 사용하기

1. **모듈 불러오기**
    
    `var var-name= require("파일경로")` 
    
2. **모듈 사용하기**
    
     `var-name.모듈이름()`
    
    내보낸 모듈 개수 상관없이 메서드로 호출
    

## ES modules (JS)

---

자바스크립트의 모듈 시스템

- 브라우저, 프레임워크(React, Vue.js)에서 사용
- node의 모듈 시스템이 먼저 생기고, 이에 영향을 받아 JS에 생김
- `<script>`로 파일을 여러 개 받아올 때 변수 충돌 등의 문제가 생겨 도입

### 모듈 사용

- 불러오기 : 선언 앞에 `export` 붙이기
- 받아오기 : `import {모듈이름, 모듈이름, ...} from '파일이름'`

### ES modules vs CommontJS

- ES6문법 / Node.js의 CommonJS 모듈
- 비동기 / 동기 (네트워크 필요없이 파일들로 로컬에 저장되서 비동기 필요 x)
- 파일의 맨 위에서만 호출 가능 / 프로그램의 어느지점에서나 호출 가능
- 프로그램에서 두 키워드 동시 사용 불가
- 일반적으로 `import()`는 필요한 모듈만 선택해서 불러올 수 있고, 성능이 우수하며 메모리를 절약해서 선호함
- 아직은 과도기이고, 아직 Node.js를 사용한 많은 모듈들이 CommonJS로 개발되어있음 ⇒ 둘 다 할 줄 알아야함…ㅠㅠ
- 긴 시간이 지나면 ES modules로 통합되지 않을까 싶음
- 여담: 타입스크립트는 기본적으로 import/export문을 사용하는데 이는 엄밀히 말하면 ES module이 아님. tsconfig에 어떻게 설정하느냐에 따라 ES module이 될 수도 있고 CommonJS가 될 수도 있다. TypeScript는 transpile된 JS의 관점으로 생각해야한다는 것을 잊지말자

## 모듈 종류

---

<aside>
📌 사용 전에 모듈 불러올 것
`const moduel-name= require("파일경로")`

</aside>

- **절대 경로** vs **상대 경로**
    - 절대 경로 : 루트 디렉토리(c:\ d:\)가 기준점 (URL에서는 http://를 포함)
        - 컴퓨터 어디서나 이용해서 파일 연결 가능
        - 서버의 주소가 달라지면 절대경로로 설정된 주소들 모두 수정 필요함
        - 로딩속도는 상대경로에 비해 느림
    - 상대 경로: 현재 참조하고 있는 문서가 기준
        - `../` 상위폴더 / `./` 현재폴더 / `폴더명/파일명` 하위폴더
        - 해당 문서를 기준으로 상위, 하위 또는 현재 디렉토리(폴더)에 연결
        - 서버주소가 달라져도 이전 서버와 디렉토리 구조만 같다면 경로수정 불필요
- **경로 제공 키워드**
    - `__dirname` : 현재 실행 중인 파일 경로 = `./`
    - `__filename` : 파일 이름
    - `path.sep` : 경로 구분자 (운영체제에 따라 자동 출력)
        
        mac, linux - `/` /  window - `\`
        

### OS

운영체제와 시스템의 정보를 가져올 수 있는 모듈

⇒ CPU나 메모리, 디스크 용량 확인시 사용

```jsx
const os = require('os');

//운영체제의 개행 문자
console.log(os.EOL === '\n'); // Mac
console.log(os.EOL === '\r\n'); //Window

console.log('hostname= ', os.hostname()); // 호스트 이름(컴퓨터 이름)
console.log('homedir= ', os.homedir()); // 운영체제 홈 디렉토리

console.log('type= ', os.type()); // 운영체제 이름
console.log('platform= ', os.platform()); // 운영체제 플랫폼

console.log('totalmem= ', os.totalmem()); // 시스템의 총 메모리
console.log('freemem= ', os.freemem()); // 시스템의 가용 메모리

console.log('cpus= ', os.cpus()); // CPU의 정보
console.log('userInfo= ', os.userInfo()); // 운영체제 사용자 정보
```

### process

현재 동작하고 있는 node 프로세스 정보 얻을 수 있음

- 글로벌 객체이기 때문에 `require`을 하지 않아도 사용 가능

| 속성 혹은 메소드 | 설명 |
| --- | --- |

| process.execPath | 프로세스 현재 위치 |
| process.pid | 프로세스 아이디 |
| process.ppid | 프로세스 부모의 아이디 |
| process.cwd() | 프로세스 현재 경로 |
| process.nextTick() | 이벤트 루프가 다른 콜백 함수들보다 nextTick의 콜백 함수를 우선적으로 처리함
• 너무 남용하면 다른 콜백 함수들 실행이 늦어짐
• 비슷한 경우로 promise가 있음(nextTick처럼 우선순위가 높음) |

```jsx
console.log(process.arch) // x64
```

### console 모듈

- `console.time("타이머이름")` ~ `console.timeend("타이머이름")`

사이에 실행이 얼마나 걸리는지 console에 걸린 시간(`타이머이름: ~s`) 반환

### path 모듈

운영체제별로 경로 구분자가 달라 생기는 문제를 쉽게 해결하기 위해 등장

```jsx
console.log(path.parse(__filename)); // 전체 경로 오브젝트

console.log(path.basename(__filename)); // 현재 파일이름.확장자
console.log(path.basename(__filename, '.js')); // 현재 파일이름
console.log(path.dirname(__filename)); // 디렉토리 이름
console.log(path.extname(__filename)); // 확장자

const curPath = path.parse(__filename);
console.log(curPath.base); // 현재 파일이름.확장자
console.log(curPath.name); // 현재 파일이름
console.log(curPath.dir); // 디렉토리 이름
console.log(curPath.ext); // 확장자
console.log('=========');
const str = path.format(curPath);
console.log(str);
console.log('=========');
// 절대경로인지 체크 => boolean 반환
console.log('isAbsolute?', path.isAbsolute(__dirname));
console.log('isAbsolute?', path.isAbsolute('../' + curPath.dir));

const logoImg = 'logo.png';
console.log(__dirname + '\\' + logoImg); // 안좋은 방식 (맥인지 윈도우인지 모르니까)
console.log(__dirname + path.sep + logoImg);
console.log(path.join(__dirname, logoImg));
```

## fs 모듈

---

(file system) 파일과 관련된 처리, 작업할 때 사용

### 파일 읽기 (비동기)

`fs.readFile( '파일경로', 'encoding', (err,data) => {~} )`

전체 파일을 버퍼로 읽고, 인코딩함

- 파일경로: 읽을 파일의 이름, 다른 위치에 저장된 경우 전체 경로
- encoding: 파일의 인코딩, 기본값은 ‘utf8’
- callback: 파일을 읽은 후 호출되는 콜백 함수 (비동기 방식이라 필요함)
    - err: 작업에 실패하면 반환되는 오류
    - data: 파일의 내용
    
    오류 우선 콜백패턴(error-first callback) : 콜백의 첫번째 매개변수에 에러 객체를 쓰는 것 ⇒ 에러 먼저 처리하고, 다음 실행 코드 작성 권장
    
- 프라미스 객체 반환 ⇒ then, catch 로 에러 처리 가능

```jsx
fs.readFile(fname, function(err, data) {
  if(err) return console.error(`error reading file ${fname}: ${err.message}`);
  console.log(`${fname} contents: ${data}`);
});

// 반환된 프라미스 이용해서 에러 처리
fs.readFile(curPath, 'utf8')
	.then((data) => console.log(data))
	.catch((err) => console.log(err));
```

### 파일 읽기 (동기)

`fs.readFileSync('경로'[, option])` 

파일을 동기적으로 읽고 결과를 문자열로 반환

```jsx
var text = fs.readFileSync("text.txt", "utf-8");
```

### 파일명 변경 (비동기 처리)

`fs.rename('경로', '바꾼후경로', callback)`

- callback으로 에러 처리
    
    ```jsx
    fs.rename('./05week1/test.txt', './05week1/test222.txt', (error) => {
    	error ? console.log(error) : console.log('이름 변경 완료');
    });
    ```
    
- promise로 에처 처리
    
    ```jsx
    fs.promises
    	.rename('./05week1/test.txt', './05week1/test222.txt')
    	.then(() => console.log('이름 변경 완료'))
    	.catch((err) => console.log(err));
    ```
    

### 파일명 변경 (동기)

`fs.renameSync('경로', '바꾼후경로')`

- try, catch를 사용해서 에러 처리 (동기적 실행이니까 프라미스 반환x)

### 이외

- `fs.appendFile('경로', '추가할내용')` : 파일에 내용 추가
- `fs.copyFile('복사될파일경로', '복사할파일경로')` : 파일 복사
- `fs.mkdir('파일명')` : 파일 만들기
- `fs.readdir('경로')` :  해당 경로의 파일들 읽기
    
    ```jsx
    // 두 코드의 반환값이 같음
    fs.readdir("./").then(console.log).catch(console.error); // 1
    
    fs.readdir(__dirname + "/") // 2
      .then(console.log)
      .catch(console.error);
    ```
    

### 비동기 처리 주의사항

- 비동기 처리는 순서가 없어서 먼저 완료된 것부터 반환됨
    
    → 의도된 순서대로 작동하지 않음
    
    ex) append 전에 copy 먼저 될 수 있음 ⇒ 해결하기 위해 then, catch 사용
    
    ```jsx
    // appendFile이 더 오래 걸려서 copy 먼저 실행됨
    // -> appendFile로 추가한 내용이 copy 되지 않음
    fs.appendFile(curPath, "\n박연미").catch(console.log);
    fs.copyFile(curPath, __dirname + "/copied.txt").catch(console.error);
    
    // 해결방법: then으로 프라미스 반환 받고 그 다음에 실행
    fs.appendFile(curPath, "\n박연미")
      .then(() => {
        fs.copyFile(curPath, __dirname + "/copied2.txt").catch(console.error);
      })
      .catch(console.error);
    
    // async, await 이용
    async function appendAndCopy() {
    	try {
    		await fs.appendFile(curPath, "\n박연미");
    		await fs.copyFile(curPath, __dirname + "/copied.txt");
    	}
    	catch { console.error } 
    }
    ```
    

# 서버

## 버퍼 / 스트림

---

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%2010.png)

- 버퍼 : 임시로 데이터를 저장하는 메모리 공간 & 조각난 데이터 그 자체
- 스트리밍 : 조각난 데이터를 버퍼 공간에 채우는 과정
- 버퍼링 : 버퍼에 데이터를 저장하는 과정

## 서버 생성 → 실행 요청

---

### 서버 생성

```jsx
const http = require('http');

// 1
const server = http.createServer((request, response) => {
  // 여기서 작업이 진행됩니다!
});

// 2
server.on('request', (request, response) => {
  // 여기서 작업이 진행됩니다!
});
```

createServer의 콜백 함수 or on메서드를 이용해서 실행 코드 전달

(둘 다 요청 발생시 실행되기 때문에 실행되는 과정은 같음)

- 바로 뒤에 `listen()` 붙일 수도 있음

### 서버 대기

`server.listen(포트번호[, 호스트이름[, 콜백]])`

서버가 대기 상태 → 클라이언트에 요청이 있으면 받아서 처리 가능

- 요청을 처리하려면 server객체에서 listen() 호출하고, 포트번호를 전달

```jsx
app.listen(8080, function() {
	console.log('listening on 8080');
}
```

```jsx
const http = require("http") // 노드 모듈을 가져온다

const hostname = "127.0.0.1" // 사용할 서버 호스트네임
const port = 3000 // 사용할 서버 포트

// 서버를 만든다
const server = http.createServer((req, res) => {
  // 요청이 오면 실행되는 콜백 함수
  res.statusCode = 200 // 응답 상태값 설정
  res.setHeader("Content-Type", "text/plain") // 응답 헤더 중 Content-Type 설정
  res.end("Hello, World!\n") // 응답 데이터 전송
})

// 서버를 요청 대기 상태로 만든다
server.listen(port, hostname, () => {
  // 요청 대기가 완료되면 실행되는 콜백 함수
  // 터미널에 로그를 기록한다
  console.log(`Server running at http://${hostname}:${port}/`)
})
```

### 요청 처리 함수

`createServer()` or `server.on()`로 전달하는 요청 함수

- `res.writeHead(상태코드, {'Content-Type':'text/html'});`
    
    해더 정보 내보내기
    
    - 상태코드: 웹서버로 들어오는 요청이 정상적으로 실행될 때 사용하는 http 상태코드
    - `{'Content-Type' : 'text/html'}` : 응답으로 반송하는 콘텐츠의 종류를 나타내는 헤더 정보, 이것이 표준 텍스트라는 것을 클라이언트에 전달
- `res.write('content')` : 바디 부분 콘텐츠 내보내기
    - 여러번 호출 가능, 계속해서 추가됨
- `res.end('추가컨텐츠')` : 컨텐츠 출력 완료(응답 종료)
    - 인자로 내보낼 값 추가로 작성 가능 (내보내고 종료됨)
    - 요청 마지막에 반드시 작성해야함
        - 비동기 코드가 있다면, 해당 함수 내부에 작성해야 함
            
            ⇒ 비동기 동작이 아니라서 전체 코드의 마지막에 쓰면 먼저 실행됨
            
            ```jsx
            var http = require('http');
            var fs = require('fs');
            
            function onRequest(request, response) {
            
              response.writeHead(200, { 'Content-Type': 'text/html' });
            
              fs.readFile('index.html', 'utf-8', (err, data) => {
                if (err) {
                  response.writeHead(404);
                  response.write('file not found');
                  response.end(); // 이렇게 비동기 함수 안에 넣을 것
                }
                response.write(data);
                response.end(); // 이렇게!
              });
              
            	response.end() // 만약 여기에만 있다면 fs.readFile보다 먼저 실행됨
            }
            
            http.createServer(onRequest).listen(8080);
            ```
            
- `res.statusCode = 200` : 응답 상태값 설정

### 예시

- fs로 파일 가져와서 브라우저에 출력
    
    ```jsx
    var http = require('http');
    //1. 파일 입출력을 위한 fs 모듈을 import하세요.
    var fs = require('fs');
    
    function onRequest(request, response) {
      //응답의 콘텐츠 형식이 HTML인 파일을 가져옵니다.
      response.writeHead(200, { 'Content-Type': 'text/html' });
    
      //2. 서버생성시 index.html 파일을 읽어오는 코드
      fs.readFile('index.html', 'utf-8', (err, data) => {
        if (err) {
          response.writeHead(404);
          response.write('file not found');
          response.end();
        }
        response.write(data);
        response.end();
      });
    }
    
    http.createServer(onRequest).listen(8080);
    ```
    

# npm

Node.js 프로젝트를 관리하는 필수적인 도구 ⇒ 온라인 저장소 + 커맨드라인 도구

- 수많은 오픈소스 라이브러리와 도구들이 업로드되는 저장소
- 필요한 라이브러리나 도구를 손쉽게 검색 가능

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%2011.png)

## 저장소에서 라이브러리, 도구 설치

---

`$npm init` / `npm init --yes` (자동으로 내용 채우기)

(축약형) `$npm i`

프로젝트 디렉터리 안에서 사용 → 몇 번의 질문을 통해 package.json을 생성 → 이 디렉터리는 Node.js 프로젝트가 됨

### **package.json**

현재 프로젝트의 모든 라이브러리에 대한 정보 파일

- 자세한 설명
    
    현재 프로젝트에 대한 메타데이터 및 npm script 그리고 사용(의존)하고 있는 외부(서드 파티) 모듈을 정리한 파일
    

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%2012.png)

### **package-lock.json**

package.json의 내용(프로젝트가 사용하고 있는 외부 모듈들의 상세한 스펙)을 snapshot 형태로 저장한 파일

- 프로젝트에 의존성 추가될 때마다 package-lock.json 파일 생성
⇒ npm이 이 파일을 이용해서 현재 프로젝트의 정확한 버전과 모듈 종류, 의존 모듈의 버전까지 알고 install 가능
- 이게 없다면 프로젝트를 클론 받고 npm install 진행시 프로젝트 팀원과 다른 버전의 모듈들을 설치될 수도 있음

## 프로젝트 의존성(라이브러리) 관리

---

프로젝트 내에서 사용하는 라이브러리를 관리하는 방법

### **프로젝트에 의존성 추가**

`$npm install [package-name]`

필요한 패키지 프로젝트에 추가

- **dependencies** (의존성): 어플리케이션 코드에 직접적으로 사용되는 모듈들
⇒ 프로젝트가 실행되기 위해 라이브러리에 의존하기 때문에 라이브러리를 의존성(dependency) 이라고 함
- 추가된 패키지는 packgae.json의 dependencies 안에 추가 & node_modules 디렉터리에 저장됨
- 설치된 의존성 모두 지우려면 `rmdir node_modules`로 파일 삭제

### **개발용 의존성 추가**

`$npm install [package-name] --save-dev`

- **devDependencies** (개발용 의존성): 배포 전까지만 사용하는 의존성, 간단히 말하면 서포트 툴 ex) 유닛 테스트 라이브러리
- 추가된 의존성은 packgae.json의 devDependencies 안에 추가됨

### **프로젝트에 의존성 내려받기**

`$npm install`

아무 옵션 없이 입력하면 package.json에 정의된 dependenties & devDependencies를 node_modules 디렉터리에 내려받음

- 보통 node_modules 디렉터리는 코드 관리나 배포시에 업로드 x
(의존성이 많아지면 용량이 크고, 운영체제별로 실행되는 코드가 다른 경우가 존재하기 때문에)

### **개발용 의존성을 제외하고 내려받기**

`$npm install --production`

package.json의 dependencies만 node_modeules에 내려받음

- 프로젝트를 배포할 때에는 개발용 의존성을 포함할 필요 X

### 의존성 삭제

`$npm remove [package-name]`

package.json의 dependencies, devDependencies에서 삭제 & node_modules에서도 삭제

### 이외

- 의존성 버전 지정해서 설치
    
    `$npm install [package-name]@[version]`
    
    - `~1.13.0` : 1.13.x 버전설치
    - `^1.13.0` : 1.x.x 버전 설치
    - `0.13.0` : 정확히 0.13.0 버전만 설치
- 전역 패키지 디렉터리에 패키지 내려받음
    
    `$npm install [apckage-name] --global`
    
    커맨드라인 도구들을 주로 전역 패키지로 추가해서 사용 ex) express-generator, pm2
    
    - 로컬 패키지: package.json에 선언 & node_modules에 저장된 패키지
    - 전역 패키지: `npm install -g`를 통해 내려받아, 전역 패키지 저장소에 저장된 패키지
    
    전역 패키지도 프로젝트에서 사용 가능, but 프로젝트의 의존성이 package.json 내에 명시적으로 선언되어 있는 것이 프로젝트 관리에 좋은 방향임
    

## 스크립트 실행

---

`$npm run [script-name]`

package.json의 script에 선언된 스크립트의 간단한 동작 실행

- 사용하는 이유 : npm script 내에서는 의존성 패키지를 사용 가능

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%2013.png)

### 사용 가능한 주요 스크립

(run 대신 그 자리에서 사용) 사용 가능하지만 npm 내부적으로 제공하는 코드X

- `test` : 코드 유닛 테스트 등에 사용
- `start` : 프로젝트 실행
- `stop` : 프로젝트 종료

### node.js에서 ESmodules 사용하기

package.json의 최상위에 `"type" : "module"` 추가

- 터미널 조작
    
    cat 파일명,
    

# Server

- 트렌젝션 : 요청과 요청 처리 응답까지의 과정
- 백엔드 프로그래밍(aka 서버 개발) : 요청과 응답 사이에 (비즈니스)로직을 더하는 행위

### 장점

- 다수의 사용자의 데이터를 중앙에서 처리하여 데이터의 일관성(정확성)을 유지하기 용이
- 다수의 사용자의 데이터를 중앙에 저장함으로서 데이터 관리가 용이
- 상대적으로 빠른 연산이 필요한 작업들을 성능이 좋은 중앙 서버에 위임 가능
클라이언트 머신의 성능은 크게 중요하지 않음 ⇒ 비동기 작업 가능
- 클라이언트로부터 중요한 비즈니스 로직 코드를 숨길수 있음
클라이언트가 브라우저일 경우 작정하면 코드 볼 수 있는데 서버에 중요한 코드를 넣어놓으면 그런 위험 감소
- 주의: 중앙 = 하나의 서버는 아님

### 단점

- Single point of failure(SPOF) : 서버가 다운되면 클라이언트는 속 아무것도 할 수 없음.
- 요청이 많을수록 서버가 감당하기 힘듬
⇒ 해결방법: 서버 수직 확장(Scale up: 컴퓨터 성능 업그레이드) / 수평 확장(Scale out: 성능이 같거나 이하인 컴퓨터 여러대로 늘림)
⇒ 비용이 많이 드는 것이 단점
- 중앙에서 데이터를 관리 ⇒ 공격에 놓이기 쉬움
- 서버 유지보수 비용 발생

## 서버 종류

---

### 웹 서버

정적 컨텐츠를 제공하기 위한 서버(HTML, JS, CSS, 이미지, 비디오, 파일 등)

- 주로 HTTP 요청을 다루도록 설계됨
- 고객(클라이언트)는 주로 브라우저
- 정적 데이터를 제공하기 때문에 사용자에 따라 데이터를 바꿔가며 제공 불가
ex) 손님: 메뉴판 주세요 → 웨이터: 메뉴판 갖다줌

### 웹 어플리케이션 서버

(=WAS) 클라이언트에게 정적 컨텐츠가 아닌 동적 데이터인 서비스(비즈니스 로직)를 제공할 수 있는 서버 ex) SNS, e-commerce

- 템플릿 형식의 페이지에 데이터를 주입해서 완성된 페이지를 만들기 가능해짐
- 주로 웹 개발 분야에서 백엔드 개발은 WAS 코드 개발을 말함

## 서버와의 통신 규약

---

### 프로토콜

- HTTP/HTTPS: 문서라고 쓰고 Hypertext라고 읽자.
- SSH: 원격 머신에 접속 및 제어
- FTP/SFTP: 파일 전송 􃏇 rsync는?!
- WebSocket: Full-duplex(전이) 통신 (쌍방으로 상대방의 요청, 처리 고려하지 않고 막 통신할 수 있음 ex) 통화 )
- DNS: human-readable 도메인을 IP􃏖machine friendly address􃏗로 변환.
- SMTP & IMAP/POP3: 메일 전송, 메일 서버 복사, 메일 서버 동기화
- DHCP: 네트워크에 연결된 머신들에게 IP를 할당.
- MQTT: 경량 machine􃎼to􃎼machine􃏖M2M􃏗 통신, 메시지큐􃏖브로커, 클라이언트􃏗 형식으로 통신이
가능(Diagram)

## API

---

애플리케이션이 어떤 프로그램이 제공하는 기능을 사용할 수 있게 만든 매개체

컴퓨터와 인간을 연결시키는 사용자 인터페이스(UI)와 반대로, API는 컴퓨터나 소프트웨어를 서로 연결함

- 서버는 자신이 제공하고자 하는 데이터나 기능을 제어할 수 있는 API 만들어서 제공

### HTTP API

HTTP를  사용하여 프로그램끼리 소통하는 API

- HTTP 사용하지 않는 API도 있음
    
    ex) 미세먼지를 측정해서 창문을 닫는 IoT어플리케이션
    
    → 저사양/저전력 환경에 적합한 MQTT, CoAP 프로토콜 사용
    

### REST API

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%2014.png)

REST를 준수해서 만든 API

⇒ 요청 메서드의 의미, URI 설계, 클라이언트의 상태에 대한 동작 정의

- 좋은 REST API 설계 예시
    - URI는 동사보다 명사를, 대문자보다 소문자를 사용
    - 마지막에 슬래스(/)를 포함x
    - 언더바 대신 하이픈 사용
    - 파일확장자는 URI에 포함x
    - 행위를 포함x
- 요청 메서드의 의미 종류 (CRUD)
    - GET : 리소스 정보를 얻음
    - POST : 리소스를 생성
    - PUT : 리소스를 생성하거나 업데이트
    - DELETE : 리소스를 제거
- REST
    
    HTTP를 잘 활용하기 위해 만들어진 **네트워크 아키텍처 스타일**(네크워크 자원을 정의&처리하는 방법)
    
    ⇒ HTTP의 요청 메서드에 응하는 서버 API와 클라이언트 간 통신의 구조가 지켜야 할 좋은 방법을 명시한 것
    
    - URI로 자원(리소스)을 표현
    - 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현

## CRUD

---

![Untitled](Node%20js%204e3012c9276848d0b2a0fc54360f4af6/Untitled%2015.png)

### post

`axios.post('url', data 객체)`

(C) 생성

### get

`axios.get('url')`

(R) 데이터 받아오기

### put

`axios.put('url', data 객체)` 

(U) 데이터 전체 수정

- `axios.patch('url', data 객체)` : 일부만 수정

```jsx
// 전체 데이터 객체 = {name: 'jiwoo', age: 10}

// put => 전달하지 않은 prop의 값은 null이 됨
axios.put('url', {name: 'john'})
	.then(res => console.log(res)) // {name: 'john', age: null}

// patch => 전달한 prop의 값만 수정됨
axios.patch('url', {name: 'john'})
	.then(res => console.log(res)) // {name: 'john', age: 10}
```

- 주의사항: 대부분의 오픈API는 PUT 요청을 지원하지 않음 (함부로 아무나 수정하면 안되므로) ⇒ 직접 API를 만들 때 주로 사용

### Delete

`axios.delete(url)`

(D) 데이터 전체 삭제

- 주의사항 : 대부분의 오픈API는 Delete 요청을 지원하지 않음

### 데이터 처리하기

CRUD에 성공 → then으로 처리

```jsx
axios.post('url', 데이터 객체)
	.then(res => console.log(res));
```

- `res.status` : 해당 브라우저의 HTTP status를 반환

# express

node.js로 서버를 구축하는 프레임워크

## 생성

```jsx
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(포트번호, 띄운 후 실행할 함수);
app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```