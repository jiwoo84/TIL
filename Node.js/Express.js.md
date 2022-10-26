# Express.js

# 웹 프레임워크

웹 서비스에 필요한 기능들을 제공해주는 다양한 도구들의 모음

⇒ 웹 서비스를 빠르게 구성하기 위해 불러와서 사용하는 기능

- 종류
    - **express.js** : 가장 유명한 웹 프레임워크
    - Koa.js : 현대적인 JS를 적극적으로 사용하는 웹 프레임워크
    - Nest.js : TS를 사용하며, 고정된 구조를 제공하는 웹 프레임워크
    - Hapi, Sails.js, Merteor.js 등등 많음

### 프레임워크 vs 라이브러리

![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled.png)

1. **프레임워크**
    
    소프트웨어의 특정 문제를 해결하기 위해서 상호 협력하는 클래스와 인터페이스의 집합
    
    ⇒ 원하는 기능 구현에 집중하여 개발할 수 있도록 일정한 형태와 필요한 기능을 갖추고 있는 골격, 뼈대를 의미
    
2. **라이브러리**
    
    단순 활용이 가능한 도구들의 집합
    
    ⇒ 소프트웨어를 개발할 때 컴퓨터 프로그램이 사용하는 비휘발성 자원의 모임. 즉 특정 기능을 모아둔 코드, 함수들의 집합이며 코드 작성 시 활용 가능한 도구들
    
- **차이점**은 ‘제어 흐름의 권한이 있는 위치’
    - 프레임워크: 프레임워크에게 있음 ⇒ 제어의 역전이 적용
        
        전체적인 흐름을 자체적으로 가지고 있고, 프로그래머가 그 안에 필요한 코드를 작성
        
    - 라이브러리: 프로그래머에게 있음
        
        사용자가 프름에 대해 제어하며, 필요한 상황에 라이브러리를 가져다  씀
        

### 사용 이유

- 웹 서비스를 구성하려면 매우 많은 기능이 필요
- 기능을 직접 만들면 큰 비용 발생
- 웹 서비스는 많은 부분이 정형화되어 있음
- 프레임워클르 사용하면 정형화된 부분을 간단하게 구현 가능
- 필요한 부분만 집중해서 개발 가능

### 기본 제공 기능

웹 프레임워크가 기본적으로 제공하는 웹 서비스의 정형화 된 부분

- **HTTP 요청 처리**
- **HTTP 응답 처리**
- **라우팅**
    
    HTTP 요청을 분기하는 방법 제공
    
    ⇒ HTTP 요청 URL에 해당하는 알맞은 응답의 경로를 미리 설정함
    
    ex) 회사 1층 안내데스크 : 요청으로 오면 안내를 받아 알맞은 위치로 감
    
    ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%201.png)
    
- **HTML Templating**
    
    웹 프레임워크가 SSR을 구현하기 위해 제공하는 방법
    
    SSR에서 응답으로 보낼 HTML을 서버에서 작성하기 위해 HTML Template를 통해 미리 페이지의 뼈대를 작성 가능함
    

# Express.js

node.js로 서버를 구축하는, node.js로 만들어진 **웹 프레임워크**

## 서버 생성

---

### 생성한 서버의 구조

![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%202.png)

### 생성 코드

`app` ⇒ `express()` 인스턴스가 할당된 변수 => 어플리케이션

- 어플리케이션을 통해 기본적인 express 서버 설정이 가능, 라우팅 및 서버요청 대기 상태를 만들 수 있음

```jsx
// terminal
// 디렉터리 생성 or 안으로 이동
$npm init // npm 먼저 설치
$npm i express // express 설치

// index.js 작성
const express = require('express'); // express 모듈 추가
const app = express(); // 어플리케이션 => express 인스턴스

app.get('/', (req, res) => { // 라우팅 추가
  res.send('Hello World!');
})

app.listen(3000, function() { // 서버 시작
	console.log('서버 시작');
}); 

// terminal
npm start // 서버 시작
// localhost:3000 들어가면 볼 수 있음
```

- get 으로 받은 응답을 웹 페이지에 출력하기
    
    ```jsx
    // index.js
    const express = require("express");
    const app = express();
    
    app.get("/", (req, res) => {
      res.send("hello world");
    });
    
    app.listen(3000, () => {
      console.log("SERVER started");
    });
    
    // package.json
    "scripts": {
        "start": "node index.js", // script부분에 이렇게 추가
      }
    ```
    
    - 터미널에서 npm start → 터미널에 `listen()` 콜백 함수 실행
        
        ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%203.png)
        
    - 서버에는 get으로 받은 내용 입력됨
        
        ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%204.png)
        
- 타입스크립트 사용
    
    ```jsx
    import { Response, Request, NextFunction } from 'express';
    // req, res, next의 타입은 express의 내부 모듈에서 받아옴
    
    const getTodos = async (
      req: Request,
      res: Response,
      next: NextFunction
    ): Promise<void> => {
      try {
        res.status(200);
      } catch (error) {
        next(error);
      }
    };
    ```
    

### express-generator 사용하기

express-generator: express가 제공하는 프로젝트 생성기 ⇒ 프로젝트의 기본 구조를 자동으로 생성해줌

- 빠르게 프로젝트를 시작하기 좋은 방법
- 생성된 프로젝트는 `npm start`로 실행 가능

```jsx
// termanal
$npm i -g express-generator // 전역패키지로 제너레이터 추가
$express [디렉터리] // express명령어로 디렉터리 생성
$cd my-web // 해당 디렉터리로 이동
$npm i // express에서 제공하는 의존성 모두 설치
$npm start // 프로젝트 실행
```

- npx를 사용하여 express-generator을 설치하지 않고 바로 사용 가능
    
    ⇒ express-generator은 프로젝트 생성 이후에는 사용 x 
    
    ⇒ npx를 사용하는 것도 좋은 방법
    
    ```jsx
    // terminal
    $npx express-generator my-seb
    $cd my-web
    $npm i
    $npm start
    ```
    
    - 동작 과정
        1. express-generator로 만들어진 프로젝트 디렉터리에 접근
        2. npm start로 Express.js 프로젝트 실행
        3. [localhost:3000](http://localhost:3000)에 접속하여 페이지 확인

## app 객체

---

- express()로 생성되는 app객체(Express.js의 기능을 담은 객체) 확인 가능
- Express.js의 모든 동작은 app 객체에 정의됨
⇒ Epress.js는 app 객체로부터 시작해서 모든 요청 처리

### 주요 기능

- **`app.locals.variable = value`**
    
    app에서 사용할 공통 상수
    Express.js에선 global 변수를 선언하지 않고 이 값 사용 가능
    
- **`app.listen()`**
    
    http서버를 생성해주는 함수
    express-generator를 사용하면 `http.createServer`를 사용하는데 `app.listen` 함수로 대체할 수 있음
    
- `**app.use(['URL',] 미들웨어함수)**`
    
    middleware를 등록하고, URL로 들어온 요청에 미들웨어 실행
    
    - URL을 생략: 모든 요청이 미들웨어를 거쳐감 (주로 페이지 로드될 때 실행시키려고 사용)
    - `URL/~/...` 처럼 경로가 더 붙어도 URL을 통과한 것으로 봐서 미들웨어함수 실행
    - URL의 하위에 미들웨어 함수를 등록하는 것이라서, 계층적 구조로 사용할 수 있음
        - 계층적 구조의 라우터 사용시, 선언에 `Router({ mergeParams: true })`를 사용해야 이전 라우터에서 전달된 path parameter을 사용 가능
        
        ```jsx
        // index.js
        const express = require('express');
        const userRouter = require('./routes/users');
        const app = express();
        app.use('/users', userRouter); // 라우터를 users 파일의 라우터에 연결
        
        // users.js
        const { Router } = require('express'); // express객체 중에서 Router키값만 빼옴
        const petsRouter = require('./pets');
        const router = Router();
        router.use('/:userId/pets', petsRouter); // 또 연결
        module.exports = router;
        
        // pets.js
        const { Router } = require('express');
        const router = Router({ mergeParams: true }); //path parameter 사용 위해 선언
        module.exports = router;
        ```
        

## 라우팅 방식

---

요청을 여러 갈래로 나누어서 올바른 곳으로 이어주는 것

![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%205.png)

### 1. **app 라우팅**

`app.httpMethod('URL',(req, res) => {callbakc});`

app객체에 직접 HTTP method(get/post/put/delete)를 사용하여 라우팅

⇒ URL을 통해 들어온 method 요청에 콜백함수 실행

- URL을 `'/'`로 설정하면 기본 서버 입장시 실행
- URL 별로 따로 작성해야함 (무조건 `'/'` 하나는 작성해야 함)
- 지정한 method 요청만 받음 ex) `app.get()` ⇒ get 요청만 받음
- 정확히 지정한 경로로 들어온 요청만 받음
    - 경로 상관없이 해당 메서드를 사용한 모든 요청받으려면 URL에 `'*'` 쓰기
        
        ex) `app.get('*', (req, res) => {~})` get인 모든 요청 받음
        
- all 함수를 사용하면 HTTP method에 상관없이 라우팅 가능
- 사실 모든 콜백함수는 미들웨어다 ⇒ 미들웨어 생성법과 같음
- 콜백함수 여러개 쓸 수 있음 ⇒ 순서대로 실행됨

```jsx
// index.js
const express = require('express');
const app = express();

app.get('/',(req, res) => { // 경로로 들어온 get요청에 미들웨어 실행
	res.send('GET /');
});

app.get('*',(req, res) => { // 모든 get요청에 미들웨어 실행
	res.send('GET /');
});

app.all('/all',(req, res) => { // 경로로 들어온 모든 요청에 미들웨어 실행
	res.send('POST /');
});
```

### 2. **Express.Router**

라우터 객체를 불러와서 미드웨어를 연결해서 모듈화(그룹화) 시키는 방법

`Express.Router` = router객체를 반환

→ router객체에 http method 사용해서 미들웨어 연결 ⇒ 모듈화

→ 모듈화된 router 객체를 export함

→ 다른 파일에서 `app.use('경로', 해당router)` 작성해서 사용

```jsx
// index.js
const express = require('express');
const app = express();
const topicRouter = require('./topic'); // topic 모듈 불러오기
app.use('/topic', topicRouter); // '/topic'으로 들어오는 모든 요청은 userRouter로 연결됨

// topic.js => Express.Router를 사용해 라우터 모듈화
const express = require('express'); // express 다시 호출
const router = express.Router(); // = router 객체를 반환
// 다른 작성 방법 (실행 결과는 같음)
// const { Router } = require('express');
// const router = Router();

// /topic/create로 들어오는 요청에 미들웨어 적용 ('/topic'은 생략 가능) 
router.get('/create', (req, res) => {
	res.send('hi');
});

module.exports = router; // 모듈 내보내기
```

## Request Handler

---

라우팅에 적용되는 함수, HTTP 요청과 응답을 다룰 수 있는 함수

⇒ 설정된 라우팅 경로에 해당하는 요청이 들어오면 해당 함수 실행해서 응답을 보냄

- 라우팅 함수(get/ post/ put/ delete 등)에 적용된 미들웨어
- 일반적인 미들웨어와는 다르게 path parameter 사용 가능

### **Request 객체**

HTTP 요청 정보를 가진 객체 ⇒ 요청의 path parameter, query parameterm, body, header등을 확인 가능

- **req.params**
    
    path parameter를 이용해 URL을 객체로 받기 (이를 사용하면 주소의 일부를 변수처럼 사용 가능)
    
    ```jsx
    app/get('/path/:id', (req, res) => { // path parameter = '/path/:id'
    	res.send(req.params);
    }
    
    app.listen(3000);
    
    // localhost:3000/path/hi로 접속 -> req.params = {"id": "hi"}
    // '/path/:id/:name' 이렇게 더 길게도 가능
    // '/messages/:from-:to' -> /message/123-456 접속 -> {"from":"120", "to":"456"
    
    ```
    
- **req.query**
    
    쿼리 파라미터(URL 파라미터) : URL에서 ? 이후의 문자열을 객체로 가져옴
    
    ex) `https://www.beusable.net/blog/?p=3798` ⇒ ‘p=3798’
    
    ⇒ req.query = `{ p :'3798'}`
    
- **req.body**
    
    일반적으로 POST 요청의 요청 데이터를 담고 있음
    
- **req.get('')**
    
    HTTP Request의 헤더값이 key-value로 묶어진 객체 반환
    
    `req.get('Authorization')`등으로 값을 가져옴 
    

### **Response 객체**

HTTP 응답을 처리하는 객체 ⇒ 응답의 데이터를 전송 or 응답 상태 및 헤더 설정 가능

- **`res.send()`** : text 형식의 HTTP 응답을 전송함
    - 데이터를 한 번 전송하고 종료해줌
        
        ⇒ http 모듈의 `end('content')` or `write('content') + end()`역할
        
- **`res.json()`** : json 형식의 HTTP 응답을 전송함
    - 보내는 데이터 형식이 json인 경우 `send()`보다 `json()`사용할 것
        
        ⇒ `res.json()`의 로직이 실행과정이 짧아서 효율적임
        
- **`res.status()`** : HTTP 응답의 상태값을 설정함
- **`res.render()`** : HTML Template을 사용하여 화면을 전송함
- **`res.set()`** : HTTP 응답의 헤더를 설정
- `**req.method**` : 요청 종류에 따라 ‘GET’, ‘POST’ 등 반환
- `**res.on('event', callback)**` : 이벤트 발생시 콜백함수 실행
    
    ex) `res.on('error', (err) => console.error(err.stack))`
    
    ⇒ 에러 발생시 오류 메시지와 스택 트레이스 출력
    
    - form 데이터 받기
        
        `res.on('data', function(data) {~}` : form으로 들어온 데이터를 콜백함수의 인자값(data)로 조각내서 넣어줌
        
        ⇒ 값을 계속 저장하려면 `let body = ‘’` 선언 후, `body += data` 이런식으로 저장해야함
        
- `**res.redirect('url')**` : 처리가 완료되면 해당 url로 이동
    
    ⇒ 항상 get 요청으로 넘어감
    
- http 서버 생성시 주로 쓰이는 메서드
    - `**res.writeHead(상태코드, {'Content-Type':'text/html'})**`
        
        해더 정보 내보내기
        
        - 상태코드: 웹서버로 들어오는 요청이 정상적으로 실행될 때 사용하는 http 상태코드
        - `{'Content-Type' : 'text/html'}` : 응답으로 반송하는 콘텐츠의 종류를 나타내는 헤더 정보, 이것이 표준 텍스트라는 것을 클라이언트에 전달
    - `**res.write('content')`** : 바디 부분 콘텐츠 내보내기
        - 여러번 호출 가능, 계속해서 추가됨
    - `**res.end('추가컨텐츠')**` : 컨텐츠 출력 완료(응답 종료)
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
                
    - `**res.statusCode = 200**` : 응답 상태값 설정

```jsx
app.get('/:follow', (req, res) => {
    res.set({
     "Content-Type": "text/json",
     ETag: "10000",
    })
		.status(201)
		.json(req.params); // 체이닝 가능
})
```

## Middleware

---

![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%206.png)

요청과 응답 중간에 목적에 맞춰 거쳐가는 함수들 (남이 만든, 내가 만든 함수를 가져와서 사용)

- HTTP 요청이 들어오는 순간부터 실행 시작
- HTTP 요청과 응답 객체를 처리 or 다음 미들웨어를 실행 가능
    
    ⇒ HTTP 응답이 마무리될 때까지 미들웨어 동작 사이클이 진행되고, 사이클을 끝낼 수 있음
    

### 기본 형태

`function(req, res, next) {~; next() }`

인자로 req, res, next를 가진 함수를 작성하면 해당 함수는 미들웨어도 동작

- **req** : HTTP 요청 처리 객체
- **res** : HTTP 응답 처리 객체
- **next** : 다음 미들웨어 실행 함수
    
    next 함수가 호출 X ⇒ 미들웨어 사이클이 멈춤
    
    - `res.send()` or `res.json()` 같이 데이터를 보내는 경우, 생략 가능

### 1. 어플리케이션 미들웨어

`use` or `http method` 사용해서 미들웨어 연결

- 미들웨어를 모든 요청에 공통적으로 적용하기 위한 방법
- HTTP 요청이 들어온 순간부터 적용된 순서대로 동작함
- use vs http method
    - `app.use()` : 지정된 경로라면 모든 종류의 요청을 받음 / 경로 뒤에 주소가 추가되도 포함됨
    - `app.method()` : 지정한 method 요청만 받음 / 정확히 지정한 경로로 들어온 요청만 받음

```jsx
app.use((req, res, next) => {
	console.log(`Request ${req.path}`);
	next(); // 1
});

app.use(auth); // 2

app.get('/', (req, res, next) =>
	res.send('Hello Express'); // 3
});
```

### 2. 라우터 미들웨이

router 객체에 미들웨어를 적용 (문법은 어플리케이션 방식과 동일)

- 특정 경로의 라우팅에만 미들웨어 적용하기 위한 방법
- app 객체에 라우터를 먼저 적용하고 이후 순서대로 작동함

```jsx
router.use(auth); // 3

router.get('/', (req, res, next) => {
	res.send('Hello Router');
}); // 4

app.use((req, res, next) => {
	console.log(`Request ${req.path}`);
	next(); // 1
});

app.use('/admin', router); // 2
```

### 3. 미들웨어 서브스택

use or http method에 여러 개의 미들웨어를 동시에 적용하는 방식

- 주로 한 개의 경로를 특정해서 미들웨어를 적용하기 위해 사용
- 전달된 순서 순으로 동작

```jsx
app.use(middleware1, middlware2, ...);
app.use('/admin', auth, adminRouter);
app.get('/', Logger, (req, res, next) => {
	res.send('Hello Express');
});
```

### 4. 오류처리 미들웨어

`app.use((err, req, res, next) => {~})`

오류를 처리하는 미들웨어

- 인자: err, req, res, next (하나라도 생략 X)
- 앞선 미들웨어에서 next 함수에 인자가 전달 → 중간 미들웨어 뛰어넘음 → 오류처리 미들웨어 실행
    - middleware/handler가 동기 함수 ⇒ `next(error)` & `throw(error)`로도 오류처리 미들웨어로 넘길 수 있음
    - middleware/handler가 비동기 함수 ⇒ try-catch로 error 잡아서 `next(error)`로 전달해야함
        
        (프로미스 안에서 발생한 에러는 catch가 없다면 잡지 못함)
        
        ```jsx
        app.get('/person', async(req, res, next) => {
        	try {
        		const promise = new Promise((resolve, reject) => {
        			// do something
        			resolve();
        		});
        	} catch(error) {
        			next(error)
        	}
        }
        ```
        
- 보통 가장 마지막에 위치 ⇒ 모든 라우팅에 공통적인 오류처리 로직 적용 가능
- 오류 처리 미들웨어가 여러개라면 그 안에서도 `next()`를 써줘야 다음 오류처리 미들웨어로 넘어감

```jsx
app.use((req, res, next) => {
	if (!isAdmin(req)) {
		next(new Error('Not Authorized')); // 1: next에 인자 전달
		return;
	}
	next();
});

app.get('/', (req, res, next) => { // 뛰어넘음
	res.send('Hello Express');
});

app.use((err, req, res, next) => { // 2
    res.status(500); // 상태코드 처리
    res.json({
        result: 'fail',
        error: err.message, // 에러 객체의 메세지 넣기
    });
});
```

- 여러 파일에서 에러를 넘겨받아 최종으로 app객체에서 오류 처리하기
    
    ```jsx
    // index.js
    app.use('/authors', authorRouter); // author 경로 미들웨어
    
    app.use((err, req, res, next) => { // 에러처리 함수
        res.status(500);
        res.json({
            result: 'fail',
            error: err.message,
        });
    });
    
    // note.js => 사용할 함수 제공 (여기서 첫번째 에러 넘어옴)
    exports.findByAuthor = (author) => {
        const filtered = notes.filter(note => note.author === author);
        if(filtered.length < 1) {
            throw new Error(`${author} has no note`)
        }
        return filtered; 
    }
    
    // author.js
    router.get('/:author/notes', (req, res, next) => {
        const { author } = req.params;
        try {
            const notes = Note.findByAuthor(author); // 여기서 에러나면 catch로 넘어감
            res.json(notes);
        } catch(e) { // 에러나서 다음 미들웨어x, 오류처리 미들웨어로 넘어감
            next(e); // app.js의 에러처리 함수에서 처리됨
        }
    })
    ```
    

### 5. 함수형 미들웨어

- 미들웨어를 항상 실행하는 것이 아니라 작동 모드를 선택하고 싶은 경우
- 동일한 로직에 설정값만 다르게 하고 싶은 경우

```jsx
const auth= (type) => {
	return (req, res, next) => { // 미들웨어 함수 반환
		if (type !== 'admin') { // 인자에 따라 동작 결정됨
			next(new Error('no approach'));
			return;
		}
		next();
	}
}

// 관리자면 인자로 admin을 넘겨줘서 접근 가능하게 함
app.use('/admin', auth('admin'), adminRouter); 
app.use('/users', auth(), userRouter); // 관리자가 아니니 인자x
```

### 6. third-party middleware

외부 라이브러리의 미들웨어를 가져와서 사용

![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%207.png)

```jsx
// terminal
// body-parser 사용해보기
$npm install body-parser --save

// index.js
const bodyParser = requier('body-parser');
// 이후는 각 라이브러리의 API 문서 참고해서 적용
```

- third-party middleware 종류와 사용법
    
    ## body-parser
    
    ---
    
    req.body 값을 받아올 수 있는 도구
    
    ### 사용 이유
    
    ```jsx
    // POST request를 통해 전달한 req.body
    {
      userID : "jiwoo",
      password : "1234"
    }
    
    // 실행한 코드
    app.post('/profile', function(req, res) => {
      console.log(req.body) // undefined
    })
    ```
    
    req.body 값을 전달해도 기본값인 undefined로 받아와짐
    
    ⇒ body parser를 이용해서 값 받아와야함
    
    ### 사용법
    
    ```jsx
    const bodyParser = require('body parser');
    
    app.use(bodyParser.json()); // JSON 형식으로 데이터 전달
    app.use(bodyParser.urlencoded({extended: false})); // URL로 받으면 객체로 데이터 전달
    // 두 줄 모두 작성해야함
    ```
    
    - bodyParser.urlencoded({extended: false})
        
        `age=20&name=뽀뽀뽀&hobby=캠핑`로 값을 전달 →  `{'age':20, 'name':'뽀뽀뽀', 'hobby':'캠핑'}` 형태로 request의 body에 추가
        
        - {extended:false}
            - true : Express에 기본 내장된 querystring 모듈을 사용
            - false : querystring 모듈의 기능이 좀 더 확장된 qs 모듈을 사용 (qs 모듈 별도 설치 필요)
        - querystring 모듈
            
            url 주소 뒤에 붙어서 넘어오는 파라미터인 querystring을 쉽게 조작할 수 있는 기능을 제공하는 모듈이다.
            

# Rest API

![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%208.png)

REST를 준수해서 만든 HTTP API

- HTTP API
    
    HTTP를 사용하여 프로그램끼리 소통하는 API
    
    (HTTP API에 여러 가지 제약 조건을 지킨 것이 REST API)
    
    - HTTP 사용하지 않는 API도 있음
        
        ex) 미세먼지를 측정해서 창문을 닫는 IoT어플리케이션
        
        → 저사양/저전력 환경에 적합한 MQTT, CoAP 프로토콜 사용
        

⇒ 요청 메서드의 의미, URI 설계, 클라이언트의 상태에 대한 동작 정의

- REST
    
    HTTP를 잘 활용하기 위해 만들어진 **네트워크 아키텍처 스타일**(네크워크 자원을 정의&처리하는 방법)
    
    ⇒ HTTP의 요청 메서드에 응하는 서버 API와 클라이언트 간 통신의 구조가 지켜야 할 좋은 방법을 명시한 것
    
    - URI로 자원(리소스)을 표현
    - 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현
- API
    
    애플리케이션이 어떤 프로그램이 제공하는 기능을 사용할 수 있게 만든 매개체
    
    컴퓨터와 인간을 연결시키는 사용자 인터페이스(UI)와 반대로, API는 컴퓨터나 소프트웨어를 서로 연결함
    
    - 서버는 자신이 제공하고자 하는 데이터나 기능을 제어할 수 있는 API 만들어서 제공
- RESTful API
    
    최대한 REST 제약조건을 지켜가면서 만든 API
    
    완벽 REST API를 만들기 힘드니까 이렇게 표현함ㅋㅋ 
    

### 기본 규칙

1. **HTTP method의 사용**
    
    API의 동작을 HTTP method + 명사형 URL로 표현
    
2. **URL 표현법**
    - URL의 자원은 복수형으로 표현
    - 특정 자원에 대한 접근은 복수형 + 아이디를 통해 이루어짐
    
    ex) `/posts/1` ⇒ `/posts` (게시글 전체) + `/1` (1번 게시물)
    
3. **계층적 자원**
    
    URL을 통해 자원을 계층적으로 표현함
    
    ex) `/users/1/posts` ⇒ 1번 유저의 게시글 전체
    

### CRUD & HTTP method

| CRUD | 요청의 뜻 | 메소드 |
| --- | --- | --- |
| Create | 올려줘 | POST |
| Read | 불러와줘 | GET |
| Update | 바꿔줘 | PUT(전체)/PATCH(일부) |
| Delete | 지워줘 | DELETE |

```bash
router.post('/createTodo', addTodo) // x 의미의 중첩, post만 봐도 의도 알수 있음
router.post('/todo', addTodo) // 이렇게만 쓰면 됨
```

## JSON

---

JS에서 객체를 표현하는 표현식 

⇒ 데이터를 표현하는 방법이 단순하고 이해하기 쉬움

**∴** 웹 API에서도 데이터를 전송할 때 표현식으로 사용됨

### 사용 이유

웹 API는 기본적으로 데이터를 문자열로 전송

⇒ 객체를 웹 API를 통해 문자열로 전달하기 위해 사용

## Express.js로 JSON API 구현

---

### MVC 패턴

- 웹 서비스의 가장 대표적인 구성 패턴
- 프로텍트의 기능의 분리 방법에 대한 방법론
- Model - View - Controller를 구분하여 프로젝트 구조를 구성하는 것
    - **Model** : 데이터에 접근하는 기능 or 데이터 그 자체
    데이터의 읽기/쓰기는 Model를 통해서만 이루어져야함
    - **View** : 데이터를 표현하는 기능
    주로 Controller에 의해 데이터를 전달받고, 전달받은 데이터를 화면에 표시해주는 기능 담당
    - **Controller** : Model을 통해 데이터에 접근하여 처리 결과를 View로 전달하는 기능을 수행
    웹 서비스에서는 주로 라우팅 함수가 해당 기능을 수행함
        - 요청을 받아 데이터를 처리하고 응답하는 코드
        - 데이터에 직접 접근 x

### 구현 예시

- JS의 Array 함수 사용하여 데이터 처리 구현
- router과 route handler 사용하여 HTTP 요청, 응답 처리 구현
- 오류처리 미들웨어를 사용하여 오류 처리 구현
- 정의되지 않은 라우팅에 대해 404 오류 처리 구현
1. **메모 목록 구현**
    
    ![2022-10-20 16;57;01.PNG](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/2022-10-20_165701.png)
    
2. **메모 상세 구현**
    
    ![2022-10-20 16;57;13.PNG](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/2022-10-20_165713.png)
    
3. **메모 작성 구현**
    
    ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%209.png)
    
4. **메모 수정 구현**
    
    ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%2010.png)
    
5. **메모 삭제 구현**
    
    ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%2011.png)
    
6. **JSON 데이터 처리 미들웨어 사용**
    
    ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%2012.png)
    
    express.js는 기본적으로 HTTP body에 전달되는 JSON 데이터를 처리 못함 ⇒ express에서 기본 제공되는 `express.json()` 미들웨어를 사용해야 JSON 데이터 사용 가능
    
7. **오류 처리 미들웨어 구현**
    
    가장 마지막 미들웨어로 오류 처리 미들웨어 구현 ⇒ 모든 라우팅에 공통적인 오류처리 로직 적용 가능
    
    ![Untitled](Express%20js%205e0f84d1b917473bb9c51a91fc4ce299/Untitled%2013.png)
    

# 다른 라이브러리

## dotenv

---

환경변수를 `.env`파일에 저장하고 `process.env`로 로드하는 의존성 모듈

- **환경변수** : 프로세스가 컴퓨터에서 동작하는 방식에 영향을 미치는 동적인 값들의 모임 (OS입장에서 해당 프로세스를 실행시키기 위하여 참조하는 변수)

⇒ 환경변수는 민감한 정보라서 오픈 소스로 공개되면 위험함

⇒ dotenv 패키지를 이용하여 환경변수 파일을 외부에 만들어 접근할 수 있게 하고, 개발 초기 단계에서 세팅 가능함

```jsx
npm install dotenv
```

```jsx
DB_HOST=localhost
DB_USER=root
DB_PASS=thisispassword
ELICE=DREAM
```

```jsx
const dotenv = require("dotenv")
dotenv.config();
// = require("dotenv").config() 이것만 이렇게도 사용 가능

// env.js에서 설정해놓은 변수를 process.env.variable로 가져와서 사용
console.log("DB_HOST:", process.env.DB_HOST);
console.log("DB_USER:", process.env.DB_USER);
console.log("DB_PASS:", process.env.DB_PASS);
console.log("DB_PASS:", process.env.ELICE);
```

# 로깅

에러를 파악하려면 console.log로는 역부족이기 때문에 다른 프레임워크를 이용함 (console.log는 로깅에 부적합하기에 프로덕션 환경에는 절대 사용되지 않음)

## winston

---

process.env의 NODE_ENV에서 제공하는 서버 환경이 어떠한지에 따라 로그 관리의 레벨을 info와 silly로 관리하고 있음

```jsx
// middlewares/error-logger.ts

import { Request, Response, NextFunction } from 'express';
import fs from 'fs';
import winston from 'winston';

const logger = winston.createLogger({
  transports: [
    new winston.transports.Console({
      level: process.env.NODE_ENV === 'production' ? 'info' : 'silly',
      format: winston.format.combine(winston.format.timestamp()),
    }),
  ],
});

if (process.env.NODE_ENV !== 'production') {
  logger.add(
    new winston.transports.Console({
      format: winston.format.combine(
        winston.format.colorize(), // 색깔 넣어서 출력
        winston.format.simple() // `${info.level}: ${info.message} JSON.stringify({ ...rest })` 포맷으로 출력
      ),
    })
  );
}

function errorLogger(
  error: Error,
  req: Request,
  res: Response,
  next: NextFunction
) {
  const current_datetime = new Date();

  const dateFormatted =
    current_datetime.getFullYear() +
    '-' +
    (current_datetime.getMonth() + 1) +
    '-' +
    current_datetime.getDate() +
    ' ' +
    current_datetime.getHours() +
    ':' +
    current_datetime.getMinutes() +
    ':' +
    current_datetime.getSeconds();

  const method = req.method;
  const url = req.url;
  const errorContent = error.stack;

  logger.error(`[${dateFormatted}] ${method}:${url}\n${errorContent}\n\n`);
  const errorLog = `[${dateFormatted}] ${method}:${url}\n${errorContent}\n\n`;

  fs.appendFile('error.log', errorLog, (err) => {
    if (err) {
      console.log(err);
    }
  });

  next(error);
}

export { errorLogger };
```