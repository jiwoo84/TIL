# MongoDB

# DB

- 전기적으로 저장되어 영속성(영구x)을 갖는 데이터 저장소
- 데이터는 프로그래머나 기업에 따라 저장된 구조가 다름
- 파일 **⊂** DB
최종적으로 디스크에 파일로 저장되는건 마찬가지이기 때문에 파일도 DB에 부분 집합에 들어갈 수 있음

### DBMS

(DataBase Management System)

데이터베이스를 운영하고 관리하는 소프트웨어(시스템) (전용 언어(SQL등)를 사용해서 관리함)

- 기능
    - 데이터 정의: 저장하는 데이터의 구조 정의를 생성, 수정, 삭제
    - 데이터 업데이트: 데이터 삽입, 수정, 삭제
    - 데이터 검색(질의): 저장된 데이터를 사용자가 원하는 형태로 가져옴
    - 관리: DBMS 유저 등록/유저 모니터링/데이터 접근 권한 관리/성능 모니터링/무결성 유지(불완전하다면 아예 저장x)/동시성 제어/정보 복구(특정 이벤트, 의도치 않은 시스템 다운 ⇒ 발생 전에 데이터 저장됨)

### DB vs DBMS

- DB: 데이터를 체계적으로 보관하는 저장소의 개념
- DBMS: DB에 저장된 데이터에 체계적으로 접근하도록 하는 시스템

⇒ **통상 DB라고 하면 DBMS의 의미로 사용됨**

## 종류

---

### 관계형 데이터베이스 (Relational DBMS)

- 관계 대수를 기반으로 구현된 데이터베이스 ⇒ 정형 데이터를 관리함
    - 정형 데이터: 틀이 잡혀있는 데이터, 컴퓨터가 이해하기 쉬움 ex) 엑셀형 데이터
    - 비정형 데이터: 컴퓨터가 이해할 수 없는 형태의 데이터 ex) 책의 문장들
- 스프레드시트 형태의 데이터 구조를 가지고 있음
- SQL로 데이터를 검색, 업데이트 가능
- 일반적으로 DB라고 하면 RDBMS를 가르키지만 점점 달라지고 있음

ex) MySQL, Oracle DB, MariaDB, PostgreSQL, SQLite

### NoSQL 데이터베이스 (NoSQL DBMS)

관계형 데이터베이스 이외의 데이터베이스 ⇒ 관계 대수를 엄격하게 따르지 않음

- 제품마다 정형/비정형 데이터를 다룸 ⇒ 저장하는 데이터 구조가 다양함
    - 구조 유형: Document, key-value, Object, Wide Column, Graph
    - MongoDB(Document), Redis(key-value), Cassandra(Wide column), Elasticsearch(Document), Neo4j(Graph)

# MongoDB

문서 기반 DB로 JSON-like(BSON)을 지원하며, 이러한 이유로 JSON 형태의 데이터를 다루는 웹 생태계에서 큰 인기임

- 간단히 말해 따로 데이터를 구조화하지 않고 JSON을 그대로 저장하는 DB
- Aggregation Pipeline 기능을 활용하여 DB단에서 데이터 연산 수행 가능 ⇒ 어플리케이션 코드의 부담을 줄일 수 있음
- 다양한 데이터를 다루는 도메인에 많이 사용되나, 데이터 간의 관계가 중요한 서비스에는 적합x
- 대표적인 NoSQL, Document DB

### **사용 방법**

1. 직접 설치 : 어렵지만 데이터 무제한 사용
    - 모든 데이터베이스 관련 설정을 해야함
    - Sharding or Replication 등의 작업이  필요하다면 운영지식과 노하우가 요구됨
    - 무료로 사용할 수 있는 community version을 제공함
2. cloud 사용: 쉽고 빠르지만, 사용량에 따라 요금 부과됨
    - 모든 데이터베이스 관련 기능을 웹에서 관리 가능
    - 특별한 노하우 없이 데이터베이스 운용 가능
    - 512mb까지는 평생 무료로 사용 가능
- MongoDB Compass
    - database, collection, document 등을 시각화하여 관리할 수 있게 도와주는 도구
    - MySQL을 사용할 때 MySQL Workbench와 유사함
1. 서비스 시작하기
    
    ![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled.png)
    
    오른쪽 마우스 클 → 시작 → 중지할 때는 중지
    

### 관련 툴

- MongoDB shell(mongosh) : CLI로 제어 (터미널)
- MongoDB Compass : GUI로 제어
- mongodump / mongorestore : database 하나를 binary 파일로 추출, 추출된 binary파일을 MongoDB로 복구
- MongoDB driver : 프로그래밍 언어 별로 MongoDB와 연결을 맺어주는 드라이버

## NoSQL

---

SQL처럼 구조화되지 않은 데이터 저장 방식

- 대표적으로 Document DB(Document로 저장)이 있고, 이 외에 key-value, Graph, large collection 등

### SQL

(Structured Query Language)

- DBMS에 데이터를 검색/업데이트(**DML**: Data Manipulation Language), 일련의 데이터 구조를 가진 구조체(테이블)를 생성/수정/삭제(**DDL**: Data Definition Language), 유저 관리(**DCL**: Data Control Language), DB transaction 관리(**TCL**: Transaction Control Language)를 지원하는 프로그래밍 언어
    
    ⇒ SQL을 작성해서 DB에게 명령을 보내는 행위는 사람이 스프레드시트를 만들어서 값을 채워넣고 수정하고 지우는 과정이랑 매우 유사
    
    ⇒ 키보드, 마우스로 하던 것을 코드로 하는 느낌이라고 보면 된다.
    
- 사람이 읽었을 때 이해하기 쉽도록 문법이 구성
- 모든 RDBMS의 SQL는 기본적으로 유사한 문법을 가지고 있음. 다만 독자적으로 가지고 있는 문법들도 있음.

### RDB vs NoSQL

1. **RDB**
    
    관계형 데이터베이스 (엑셀형이라고 생각하면 됨)
    
    - 자료들과의 관계를 주요하게 다룸
    - SQL 질의어를 사용하기 위해 데이터를 구조화해야함
    - 규칙을 지켜서 넣어야 하니 데이터의 정확성, 안정성이 높음
2. **NoSQL**
    
    (Non SQL 또는 Not Only SQL) 구조화된 질의어를 사용하지 않는 데이터베이스
    
    - 자료와의 관계에 초점을 두지 않음
    - 데이터를 구조화하지 않고, 유연하게 저장함
- **NoSQL을 사용하는 이유**
    - SQL을 사용하기 위해서는 데이터를 구조화하는 것이 필수(DDL)
        
        ⇒ 스키마에 정의된 데이터가 아니면 저장할 수 없는 제약이 있음
        
        NoSQL을 사용하면 사전작업 없이 데이터 베이스를 사용 가능
        
        ⇒ 데이터베이스 작업에 크게 관여하지 않고 프로젝트를 빠르게 진행 가능
        
    - RDB보다 속도가 빠름

## 기본 개념

---

Database > Collection > Document

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%201.png)

### Database 🗄

하나 이상의 collection을 가질 수 있는 저장소

- SQL의 database와 유사

### Collection 📂

하나 이상의 Document가 저장되는 공간

- SQL의 table과 유사, 하지만 collection이 document의 구조를 정의하지 않음

### Document 📃

MongoDB에 저장되는 자료

- SQL의 row와 유사하지만 구조제약 없이 유연하게 저장 가능
- JSON과 유사한 BSON을 사용하여 다양한 자료형을 지원함
- ObjectID
    
    각 document의 유일한 키 값
    
    - SQL의 primary key와 유사
    - 하나씩 증가하는 값이 아니라 document를 생성할 때 자동으로 생성됨
    - ObjectID = timestamp + random value + auto increament
- 주의사항
    - 필드명 제한
        - “_id”는 사용할 수 없다. Primary key(고유값)로 예약되어 있는 이름임
        - 필드명은 null 캐릭터(UTF-8 인코딩의 \u0000)를 포함할 수 없다.
        - “$”, “.”을 제한적인 환경에서 포함할 수 있다
    - 문서 사이즈 제한: 최대 16MB
    - id 필드
        - 모든 MongoDB에 저장된 document들은 􃏄id 필드를 가지고 있다. 고유값으로 DB에서의 primary key 역할을 수행한다.
        - 새로운 document를 MongoDB에 생성(삽입)할 때 _id필드를 빼고 하면 MongoDB 드라이버가 알아서 _id필드를 생성해준다.
    - 문서 필드 순서
        - JS의 객체와는 다르게 MongoDB의 document의 필드들은 순서가 보장된다.
        - 순서가 보장되어 있는 만큼 문서에 대한 질의를 할 때는 주의해야한다.
        - MongoDB의 정의에 따라 {a: 1, b: 1}와 {a: 1, b: 1}는 같지만 {a: 1, b: 1}와 {b: 1, a: 1}는 다르다.
        - MongoDB에서 document를 찾을 때는 exact match와 같은 질의(query)는 지양하는게 좋다. 조건문 검색이 좋다.
        - 항상 _id 필드는 첫번째로 배정된다.

```jsx
var mydoc = {
_id: ObjectId{"5099803df3f4948bd2f98391"},
name: {first: "Alan", last: "Turing"},
birth: new Date('Jun 23, 1912'),
death: new Date('Jun 07, 1954'),
contribs: ["Turing machine", "Turing test",
"Turingery"],
views: NumberLong(1250000)
}
```

## CRUD

---

### Create

- `db.collection.insertOne()` : 하나의 document 생성
- `db.collection.insertMany()` : 다수의 document 생성

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%202.png)

```jsx
db.inventory.insertOne( // inventory => collection
{"type": "americano", "orderedBy": "Rachael Clide, "price": 3500 }
)

db.inventory.insertMany([
{"type": "americano", "orderedBy": "Mrs. Shelly Rempel", "price": 18000 },
{"type": "latte", "orderedBy": "Carroll Schumm DDS", "price": 1400 }
])
```

### Read

- `db.collection.find()` : 하나/다수의 document 찾기

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%203.png)

```jsx
// type 필드 값 "americano" && price < 5000 찾기 => and 조건
db.inventory.find({ type: "americano", price: {$lt: 6000}})

// type 필드 값 ice americano or price > 5000 => or 조건
db.inventory.find({$or: [{type: "ice americano"}, {qty: {$gt: 5000}}]})
```

### Update

- `db.collection.updateOne()` : 하나의 document 수정 (맨 처음에 발견되는 하나)
- `db.collection.updateMany()` : 다수의 document 수정

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%204.png)

```jsx
// type 필드 값 americano인 document 중 첫 번째 찾음
// -> orderedBy 필드의 값을 "Anonymous",  price 필드의 값을 0로 변경
db.inventory.updateOne(
	{type: "americano"},
	{$set: {orderedBy : "Anonymous", price: 0 }},
)
// 만약 조건에 해당되는 모든 document를 업데이트하고 싶다면 updateMany를 사용
```

### Delete

- `db.collection.deleteOne()` : 하나의 document 삭제 (맨 처음 발견되는 하나)
- `db.collection.deleteMany()` : 다수의 document 삭제
    - `db.collection.deleteMany({})` ⇒ 전체 document 삭제

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%205.png)

```jsx
// price 필드 값이 5000 이상인 document를 전부 삭제
db.inventory.deleteMany({price: {$gte: 5000}});
```

# MongoDB ODM

 = Mongoose (Object Data Modeling)

데이터를 CRUD할 수 있도록 도와주는 외부 라이브러리/모듈

### 사용이유

- 단순히 CRUD 뿐만 아니라 데이터 검증 + document를 JS 객체화(모델화)까지 해줌
    
    ⇒ 개발자는 이를 이용해 데이터를 객체지향 방식으로 수정 가능
    
- 검증 파트(Schema 모듈 담당) + CRUD & 모델화 (Model 모듈 담당) 파트로 나뉨
- 연결 관리
    
    MongoDB의 기본 Node.js 드라이버는 연결 상태를 관리하기 어려움
    
    ⇒ Mongoose를 사용하면 간단하게 데이터베이스와의 연결상태를 관리해줌
    
- 스키마 관리
    
    스키마를 정의하지 않고 데이터를 사용하는 것은 NoSQL의 장점이지만, 데이터 형식을 미리 정의해야 코드 작성과 프로젝트 관리에 유용함
    
    ⇒ Mongoose는 Code-Level에서 스키마를 정의하고 관리할 수 있게 해줌
    
- Populate
    
    MongoDB는 기본적으로 Join을 제공x → 유사한 기능 쓰려면 aggregate라는 복잡한 쿼리 사용해야함
    
    ⇒ Mongoose의 populate를 사용하여 간단하게 구현 가능
    

### Express.js + Mongoose ODM

정해진 방법은 없지만 주로 사용되는 방법

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%206.png)

- modle 디렉터리: Schema + Model
- app 객체: mongoose.connect
    
    (어플리케이션 시작을 의미하는 부분이므로 데이터베이스 연결을 명시하는 mongoose.connect가 위치함)
    

## 사용 순서

---

![InkedUntitled.jpg](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/InkedUntitled.jpg)

### 1. **스키마 정의**

다양한  형식을 미리 지정하여 생성, 수정 작업 시 데이터 형식을 체크하는 기능 제공

- 스키마(Schema)
    
    한 collection의 document의 구조를 명시화한 객체
    
    - mongoose가 데이터를 CRUD할 때 스키마를 이용해서 데이터 검증(각 필드 별 타입 검증)을 수행함 + 커스텀 함수로 추가적인 검증도 할 수 있음
    - `mongooseSchema` 의 리턴값은 객체
- timestamps 옵션을 사용하면 생성, 수정 시간을 자동으로 기록해줌
    
    ![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%207.png)
    
    - createAt, updatedAt으로 날짜, 시간이 데이터에  저장됨
- 스키마의 수정을 쉽지만, 이미 생성된 데이터가 수정되지는 않음

```jsx
const mongoose = require('mongoose');
// 1. 스키마 생성자 함수 불러오기
const { Schema } = require('mongoose');

// 2. 스키마 만들기
const userSchema = new Schema({
  email: { type: String, required: true, unique: true, lowercase: true }, // 문자열, 필수이고, 유일하며, 소문자
  password: { type: String, required: true, trim: true }, // 문자열, 필수, 공백제거
  nickname: String,
  birth: { type: Date, default: Date.now }, // 사용자가 값을 안 넣으면 Date.now 들어감
  point: { type: Number, default: 0, max: 50, index: true }, // 기본값, 최대값, 인덱스 설정(빠르게 찾을 수 있음)
  image: imageSchema, // 스키마 안에 다른 스키마 넣을 수 있음
  likes: [String], // 문자열의 배열 (or [{ type: String }])
  any: [mongoose.Schema.Types.Mixed ],
  id: mongoose.Schema.Types.ObjectId,
});
```

- 타입스크립트 이용
    
    ```jsx
    import { model, Schema } from 'mongoose';
    import { ITodo } from '../../types/todo';
    
    const TodoSchema: Schema = new Schema<ITodo>(
      {
        name: {
          type: String,
          required: true,
        },
    
        description: {
          type: String,
          required: true,
        },
    
        status: {
          type: Boolean,
          required: true,
        },
      },
      { timestamps: true }
    );
    
    export default model<ITodo>('Todo', TodoSchema);
    
    // tpyes/todo.ts
    export interface ITodo {
      name: string;
      description: string;
      status: boolean;
    }
    ```
    

### 2. **모델 만들기**

작성된 스키마를 mongoose에서 사용할 수 있는 모델로 만드는 과정

모델의 이름을 지정하여 Populate 등에서 해당 이름으로 모델 호출 가능

- 모델(Model)
    
    스키마 객체를 사용해서 MongoDB에 있는 document 데이터를 JS 객체 형태로 나타낼 수 있게 해줌
    
    - MongoDB에 있는 모든 document들에 대한 CRUD를 책임짐
    - JS 코드 상에서 실질적으로 다루는 것은 모델
- 모델 생성 : `var Variable = mongoose.model('클래스이름', '스키마')`
    - `mongoose.model`은 모델이 아니라 생성기 ⇒ 리턴값은 class
        - 이를 이용해 새로운 document 객체를 생성해 DB에 저장 가능
        - class의 static 메서드를 사용해서 document CRUD도 가능 (CRUD의 리턴값 = 이 클래스의 객체)
1. 스키마 파일에서 모델로 내보냄
    
    ```jsx
    // ./models/schemas (스키마 생성 파일)
    module.exports = mongoose.model('User', userSchema);
    
    // index.js
    const User = require('./models/schemas');
    ```
    
2. 스키마 파일에서 스키마 내보냄 → 받는 파일에서 모델로 받음
    
    ```jsx
    // ./models/schemas (스키마 생성 파일)
    // 위에서 스키마 생성
    // 내보내기
    module.exports = userSchema;
    
    // ./index.js (모델 생성 파일)
    const mongoose = require('mongoose');
    const userSchema = require("./models/schemas");
    const User = mongoose.model("User", userSchema);
    ```
    

### 3. **데이터 베이스 연결하기**

connect 함수를 이용해서 간단하게 데이터베이스와 연결

mongoose는 자동으로 연결을 관리 ⇒ 직접 연결 상태 체크하지 않아도 모델 사용 시 연결 상태를 확인하여 사용이 가능할 때 작업을 실행

```jsx
const mongoose = require('mongoose');

// 기본 연결 함수
mongoose.connect('mongodb://localhose:27017/myapp');

// 동기로 오류 처리 코드
// 함수로 작성하는 이유: disconnect했을때 재연결해야 하므로 해당 코드를 재사용하기 위해서 함수로 작성
const connect = () => {
    mongoose.connect(db, (err) => {
        if (err) {
            console.error('database connection error', err);
        }
        console.log('connected to database successfully');
    });
}
connect();
mongoose.connection.on('disconnected', connect); // 연결 끊어지면 재연결

// 비동기로 오류 처리
mongoose
  .connect("mongodb://localhost:27017/myLibrary")
  .then(() => main())
  .catch((err) => {
    console.error("오류가 발생했습니다.", err);
  })
  .finally(() => {
    process.exit();
  });
```

- Mongoose ODM 커넥션 이벤트
    
    Express.js 어플리케이션은 종료되지 않고 동작하기 때문에 데이터베이스가 정상적으로 동작하는지 파악하기 위해 동작 중에 발생하는 데이터베이스 연결 관련 이벤트에 대한 처리를 하는 것이 좋음
    
    - `connected`: 연결 완료
    - `disconnected`: 연결 끊김
    - `reconnected`: 재연결 완료
    - `reconnectFailed`: 재연결 시도 횟수 초과
    
    ```jsx
    mongoose.connect('~');
    mongoose.connection.on('connectionEvent내용', () => {~})
    ```
    
- 타입스크립트
    
    ```jsx
    import { Response, Request, NextFunction } from 'express';
    import mongoose from 'mongoose';
    
    export const db = async (req: Request, res: Response, next: NextFunction) => {
      const DB_URL =
        process.env.MONGODB_URL ||
        'MongoDB 서버 주소가 설정되지 않았습니다.\n./db/index.ts 파일을 확인해 주세요. \n.env 파일도 필요합니다.\n';
    
      await mongoose.connect(DB_URL);
      const db = mongoose.connection;
    
      db.on('connected', () =>
        console.log('정상적으로 MongoDB 서버에 연결되었습니다.  ' + DB_URL)
      );
      db.on('error', (error) =>
        console.error(
          '\nMongoDB 연결에 실패하였습니다...\n' + DB_URL + '\n' + error
        )
      );
      next();
    };
    ```
    
    - process.env.MONGODB_URL을 사용했습니다. 프로젝트를 적용할 때 반드시 외부에 노출되어서는 안되는 정보는 .env에서 별도로 관리해야함
        - 만약 외부 노출 되었을 시, 해커가 리소스를 갉아 먹을 수 있고 소중한 정보 노출

### 4. 모델 사용하기

작성된 모델을 이용하여 CRUD를 수행 가능

- 모델에 직접 CRUD하면 됨

```jsx
// routers/todo-router.ts

import { Router } from 'express';
import {
  getTodos,
  addTodo,
  updateTodo,
  deleteTodo,
} from '../controllers/todo-controller';

const todoRouter: Router = Router();

// localhost:3000/todos

todoRouter.get('/todos', getTodos);
todoRouter.post('/todos', addTodo);
todoRouter.put('/todos/:id', updateTodo);
todoRouter.delete('/todos/:id', deleteTodo);

export { todoRouter };
```

## CRUD

---

### **CREATE**

- `create()` : Document 생성 & 반환
    - create(Document Object) ⇒ 단일 Document 생성
    - create(Document Object 배열) ⇒ 복수 Document 생성
- `save()` : 매번 document의 데이터 검증을 수행함
- `inservMany()` : 여러 개의 데이터 삽입

```jsx
// 새로운 커피 생성 : Create
const coffee = new Coffee({ type: "Americano", orderedBy: "John Doe" });
await coffee.save(); //  collection에 document를 insert하기 전에 데이터가 스키마에 맞게 구성되어있는 지 검증을 진행

// 다른 방법의 새로운 커피 생성 : Create
await Coffee.create([{ type: "Latte", orderedBy: "Someone" }, {type: "Cappuccino", orderedBy: "Stephan Dahl" }]);
```

- 타입스크립트
    
    ```jsx
    // todo-model.ts
    import Todo from '../schemas/todo-schema';
    import { ITodo, TodoInfo } from '../../types/todo';
    
    async create(userInfo: TodoInfo): Promise<ITodo> { // 비동기 처리되어 전달
        const createdTodo = await Todo.create(userInfo);
        return createdTodo;
      }
    
    // tpyes/todo.ts
    
    export interface ITodo {
      name: string;
      description: string;
      status: boolean;
    }
    
    export interface TodoInfo {
      name: string;
      description: string;
      status: boolean;
    }
    ```
    

### **READ**

query를 사용하여 검색 (findById는 ObjectID로 검색)

1. `Users.find(조건, 프로젝션, 콜백함수(err, result))` 조건에 해당하는 모든 것
2. `Users.findOne(조건, 프로젝션, 콜백함수(err, result))` 조건에 해당하는 첫 번째 것
3. `Users.findById(아이디, 프로젝션, 콜백함수(err, result))`
- 콜백 함수는 넣어주면 콜백 형식으로 결과를 받고,넣어주지 않으면 프로미스로 받음 ⇒ 비동기 처리 가능
- ObjectID 값으로 검색 : data에 `_id` 속성값으로 저장되어 있음
- id로 찾을 때 숫자로 변환 후, 검색할 것
- find + And 함수
    
    find와 Delete, Update를 함께 수행 가능
    
    - `findByIdAndUpdate` / `findoneAndUpdate` : 검색된 Document에 업데이트를 반영하여 반환
        - 반환값 : 수정 전 모델
            
            수정 후 반환받고 싶다면 ⇒ 마지막 인자로 `{new: true}`전달
            

```jsx
// 모든 커피를 가져오기 : Read
const coffees = await Coffee.find();
// 하나의 커피를 가져오기 : Read
const coffee = await Coffee.findById("<some-coffee-id>");

// 라우터에 검색 넣기 => 동기
router.get('/', (req, res) => {
    Book.find( (err, books) => { // 
        res.json(books);
    });
});

// 비동기로 처리
router.get('/', async(req, res) => {
	try {
		const data = await Book.find({});
		res.json(data);
	}
	catch(e) { // 에러처리가 가능해짐!
		console.log(e)
	}
})

// ObjectID 값을 path parameter로 받아서 찾기
router.get('/:book_id', async(req, res) => {
    const id = req.params.book_id;
    try {
        const data = Book.findOne({_id: id});
        res.json(data);
    }
    catch(e) {
        console.log(e);
    }
})
```

- **query**
    
    SQL의 where과 유사한 조건절, BSON형식으로 기본 문법 그대로 사용함
    
    - {key: value} 형식
    - 범위 지정: `$lt`(less than), `$lte`(less than equal), `$gt`(grater than), `$gte`(grater than equal) …
    - 다중값 검색: `$in`
        - 쿼리 값으로 배열이 주어지면 자동으로 `$in` 쿼리 생성해줌
            
            ```jsx
            Person.find({ name: ['elece', 'bob'] });
            // { name: { $in: ['elice', 'bob'] } }
            ```
            
    - 다중 조건 검색: `$or`
    - 속성 존재 유무 체크: `{ status: { $exists: false } }`
    
    ```jsx
    Person.find({
    	name: 'kyubum', // name이 kyubum과 같으면 찾음
    	age: {
    		$lt: 20, 
    		$gte: 10, // 10 <= age < 20 찾기
    	},
    	Languages: {
    		Sin: ['ko', 'en'], // 'ko' or 'en' 둘 중 하나 가지고 있으면 찾음
    	},
    	$or: [
            {category: {$exists: false}}, // 카테고리 값이 없거나
            {category: 'notice'}, // notice이면 찾음
        ]
    });
    ```
    

### **UPDATE**

1. `updateOne(조건, 변경된내용)` : 첫 발견한 한 개의 Document 수정 
2. `updateMany(조건, 변경된내용)` :  조건과 일치하는 전체 Document 수정
- 기본적으로 `$set operator`를 사용하여 Document를 통째로 변경x
    
    ⇒ 있는 속성은 수정, 없다면 추가
    
1. `prototype.save()` :  objectId를 이용하여 중복되는 document가 있다면 update를 수행하고 없으면 insert를 수행

```jsx
// 하나의 커피를 업데이트 : UpdateOne
await Coffee.updateOne({ _id: "<some-coffee-id>"}, {orderedBy: "Max Doe" });
// 다수의 커피를 업데이트 : UpdateMany
await Coffee.updateMany({ type: "Americano" }, { type: "Latte" });

// 비동기 처리
router.post('/', async(req, res) => {
    try {
        const data = await Book.updateOne({title: req.body.title}, {author: req.body.author}, {category: req.body.category} );
        res.json(data);
    }
    catch(e) {
        console.log(e);
    }
});
```

### **DELETE**

1. `deleteOne` / `deleteMany` : Document 삭제
2. `findByIdAndDelete` `findOneAndDelete` : 검색된 Document 반환함

```jsx
// 하나의 커피를 삭제 : Delete
await Coffee.deleteOne({ _id: "<some-coffee-id>" });
// 다수의 커피를 삭제 : Delete
await Coffee.deleteMany({ type: "Americano" });
```

## populate

---

RDB의 join과 유사한 기능을 제공하는 mongoose 자체 함수

Document안에 참조하는 ObjectID를 저장하고, 사용할 때 populate하여 하위 Document처럼 사용할 수 있게 해줌

```jsx
// 참조값 저장하는 스키마 작성
const Post = new Schema ({
	...
	user: {
		type: Schema.Types.ObjectId,
		ref: 'User'
	},
	comments: [{
		type: Schema.Types.ObjectId,
		ref: 'Comment',
	}],
});

// populate 수행
// 함수.populate('속성') // 여러개면 배열
const post = await Post
	.find().populate(['user', 'comments']); // => populate 한 값 찾음
```

## API 예시

---

- Create 메서드 만들어보기
    - 먼저 To do 데이터를 저장하는 API를 함께 만들어보겠습니다.
    - 클라이언트가 서버에게 API 요청을 한다면, app.ts에 있는 코드들이 순차적으로 진행될 것입니다.
    
    ```jsx
    import cors from 'cors';
    import express from 'express';
    import { todoRouter } from './routers';
    import { errorLogger, errorHandler } from './middlewares';
    import morgan from 'morgan';
    import * as dotenv from 'dotenv';
    import { db } from './db/config';
    
    dotenv.config();
    
    const app = express();
    
    // CORS 에러 방지
    app.use(cors());
    
    // 로그 출력
    app.use(morgan('dev'));
    
    // Content-Type: application/json 형태의 데이터를 인식하고 핸들링할 수 있게 함.
    app.use(express.json());
    
    // Content-Type: application/x-www-form-urlencoded 형태의 데이터를 인식하고 핸들링할 수 있게 함.
    app.use(express.urlencoded({ extended: false }));
    
    // DB 연결
    app.use(db);
    
    // api 라우팅
    app.use('/api', todoRouter);
    
    // 미들웨어 (에러를 error.log 파일에 기록 및, 에러를 프론트엔드에 전달)
    app.use(errorLogger);
    app.use(errorHandler);
    
    export { app };
    ```
    
    - 이 때 app.use('/api', todoRouter) 미들웨어를 실행하면서 todoRouters를 실행합니다.
- routers
    
    ```jsx
    // routers
    import { Router } from 'express';
    import {
      addTodo,
    } from '../controllers/todo-controller';
    
    const todoRouter: Router = Router();
    
    todoRouter.post('/todos', addTodo);
    
    export { todoRouter };
    ```
    
    - todoRouter에는 express의 Router() 객체가 값으로 할당되어 있습니다.
    - todoRouter의 post 메서드를 실행시켜서 인자값으로 /todos와 콜백 함수로 addTodo를 넣었습니다.
    - todoRouter.post('/todos', addTodo)의 역할은 URL 중 todos라는 곳으로 사용자가 post 방식으로 요청했을 때 addTodo라는 콜백함수를 전달한다라는 뜻입니다.
    - 그럼 addTodo는 어떻게 구성되어 있는지 살펴보겠습니다.
    
- controllers
    
    ```jsx
    // controllers
    const addTodo = async (
      req: Request,
      res: Response,
      next: NextFunction
    ): Promise<void> => {
      try {
        if (is.emptyObject(req.body)) {
          throw new Error(
            'headers의 Content-Type을 application/json으로 설정해주세요'
          );
        }
    
        const { name, description, status } = req.body as Pick<
          ITodo,
          'name' | 'description' | 'status'
        >;
    
        const newTodo: ITodo | null = await todoService.addTodo({
          name,
          description,
          status,
        });
        const allTodos: ITodo[] = await todoService.getTodos();
    
        res
          .status(201) -> 201은 데이터를 생성했다는 상태코드. 응답코드. 
          .json({ message: 'Todo added', todo: newTodo, todos: allTodos });
      } catch (error) {
        next(error);
      }
    };
    
    export { addTodo };
    ```
    
    - addTodo는 컨트롤러에 존재하는 함수입니다.
    
    ```jsx
      if (is.emptyObject(req.body)) {
          throw new Error(
            'headers의 Content-Type을 application/json으로 설정해주세요'
          );
        }
    ```
    
    - 위 코드는, 만약 req 요청 객체의 body 값이 빈 객체면 에러를 throw(던진다) 라는 뜻입니다.
    
    ```jsx
    		 const { name, description, status } = req.body as Pick<
          ITodo,
          'name' | 'description' | 'status'
        >;
    ```
    
    - 위 코드는 req.body 객체에서 구조분해할당을 통해 데이터를 가져오고 있습니다.
    - 여기서 타입스크립트의 Pick 타입을 사용했습니다.
    - Pick 타입은 단어의 뜻 그대로 ITodo라는 인터페이스의 타입에서 특정 타입만 뽑아온다는 뜻입니다.
    
    ```jsx
    const newTodo: ITodo | null = await todoService.addTodo({
          name,
          description,
          status,
        });
    ```
    
    - newTodo에서는 todoService.addTodo 메서드를 통해 값을 할당받고 있습니다.
    - newTodo의 타입은 ITodo 혹은 null으로, 만약 데이터가 제대로 저장됐다면 ITodo 타입이 지정될 것이고, 제대로 지정되지 않는다면 null 타입을 받는 다는 뜻입니다.
    
    ```jsx
    const allTodos: ITodo[] = await todoService.getTodos();
    ```
    
    - 우리가 저장하려고 한 데이터가 제대로 저장됐는지 확인하기 위해 DB에 저장된 모든 데이터를 가져오는 로직을 allTodos에 추가했습니다.
    
    ```jsx
    res
          .status(201)
          .json({ message: 'Todo added', todo: newTodo, todos: allTodos });
    ```
    
    - 데이터를 모두 처리했다면, express의 response 객체를 통해 클라이언트에게 서버의 응답을 전달합니다.
    - status를 통해 서버의 상태 코드를 전달하고, json을 통해 데이터를 json 객체로 전달합니다.
    - 이렇게 controller 코드를 살펴봤습니다. 여기서 중요한 점이 있습니다.
    - controller 코드에서 중요하게 살펴볼 것은, controller에서는 데이터베이스를 직접적으로 다루는 로직이 없다는 것입니다.
    - 데이터베이스를 다루는 로직은 service 계층의 메서드를 통해 받아오고 있습니다.
    - controller 코드에서는 클라이언트로부터 받은 요청을 서비스 계층으로 전달하고, 서비스 계층에서 코드를 처리하면, 사용자에게 응답을 전달하는 로직을 작성합니다.
    - 그럼 controller 코드까지 살펴봤다면, 서비스 코드를 마저 살펴보겠습니다.
- service
    
    ```jsx
    // service
    import { todoModel, TodoModel } from '../db';
    import { ITodo, TodoInfo, TodoInfoById } from '../types/todo';
    
    class TodoService {
      constructor(private todoModel: TodoModel) {}
    
      async getTodos(): Promise<ITodo[]> {
        const model = this.todoModel.findAll();
        return model;
      }
    
    	async addTodo(userInfo: TodoInfo): Promise<ITodo> {
        return this.todoModel.create(userInfo);
      }
    }
    
    const todoService = new TodoService(todoModel);
    
    export { todoService };
    ```
    
    - service 계층의 코드는 비즈니스 로직을 작성하는 계층입니다.
    - service 계층에는 현재 addTodo와 getTodos라는 메서드가 존재합니다.
    - addTodo 메서드를 활용해서 데이터를 저장하고, getTodos 메서드를 활용해서 데이터를 조회합니다.
    - addTodo 메서드를 보면, todoModel.create 메서드를 활용해서 데이터 값을 model이라는 변수에 할당하고 있습니다.
    - getTodos 메서드는 todoModel.findAll 메서드를 활용하여 데이터를 조회하고 있습니다.
    - 그럼 빠르게 model 부분으로 넘어가겠습니다.
- model
    
    ```jsx
    // model
    
    import { ITodo, TodoInfo, TodoInfoById } from '../../types/todo';
    import Todo from '../schemas/todo-schema';
    
    export class TodoModel {
      async create(userInfo: TodoInfo): Promise<ITodo> {
        const createdTodo = await Todo.create(userInfo);
        return createdTodo;
      }
    }
    
    const todoModel = new TodoModel();
    
    export { todoModel };
    ```
    
    - model 클래스에는 create 메서드가 존재합니다.
    - 여러분들은 MVC라는 개념을 배우셨을겁니다. 여기서 M을 뜻하는 model을 관리하는 코드를 model 클래스에서 다루고 있다고 보시면 됩니다.
    - 우리는 데이터를 생성하는 API를 만들고 있기 때문에 create 메서드만 먼저 살펴보겠습니다.
    - create 메서드를 실행하면, createdTodo 변수에 await Todo.create(userInfo); 의 값이 할당됩니다.
    - 이는 Todo DB에 create, 즉 데이터를 생성한다라는 의미의 mongoose 메서드입니다.
    - 메서드가 성공적으로 실행된다면 리턴값으로 인터페이스인 ITodo 값이 서비스 계층으로 전달될 것입니다.

# Sequelize ORM

MySQL, PostgreSQL 등의 RDBMS를 이용하는 간단한 방법

- ORM (Object-Relational Mapping)
    
    테이블 관계와 쿼리 등의 기능을 더욱 단순화하는 용도로 주로 사용
    (ODM은 단순히 모델에 집중하여 관리)
    

### 장점

- 데이터베이스에 직접 DDL하지 않고 JS 코드로 테이블, 관계 관리 가능
- RDB의 어려운 부분인 join을 간단하게 사용 가능

## 사용

---

### 디비 연결

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%208.png)

### 스키마 작성

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%209.png)

### 관계 정의

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%2010.png)

## 쿼리

---

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%2011.png)

## Synchronization

---

![Untitled](MongoDB%20b2eb3ea6bc734fb391054b9ab49f48f9/Untitled%2012.png)