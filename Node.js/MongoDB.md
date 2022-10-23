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

### 관련 툴

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
    
    관계형 데이터베이스
    
    - 자료들과의 관계를 주요하게 다룸
    - SQL 질의어를 사용하기 위해 데이터를 구조화해야함
2. **NoSQL**
    
    (Non SQL 또는 Not Only SQL) 구조화된 질의어를 사용하지 않는 데이터베이스
    
    - 자료와의 관계에 초점을 두지 않음
    - 데이터를 구조화하지 않고, 유연하게 저장함
- **NoSQL을 사용하는 이유**
    
    SQL을 사용하기 위해서는 데이터를 구조화하는 것이 필수(DDL)
    
    ⇒ 스키마에 정의된 데이터가 아니면 저장할 수 없는 제약이 있음
    
    NoSQL을 사용하면 사전작업 없이 데이터 베이스를 사용 가능
    
    ⇒ 데이터베이스 작업에 크게 관여하지 않고 프로젝트를 빠르게 진행 가능
    

## 기본 개념

---

Database > Collection > Document

### Database

하나 이상의 collection을 가질 수 있는 저장소

- SQL의 database와 유사

### Collection

하나 이상의 Document가 저장되는 공간

- SQL의 table과 유사, 하지만 collection이 document의 구조를 정의하지 않음

### Document

MongoDB에 저장되는 자료

- SQL의 row와 유사하지만 구조제약 없이 유연하게 저장 가능
- JSON과 유사한 BSON을 사용하여 다양한 자료형을 지원함
- ObjectID
    
    각 document의 유일한 키 값
    
    - SQL의 primary key와 유사
    - 하나씩 증가하는 값이 아니라 document를 생성할 때 자동으로 생성됨
    - ObjectID = timestamp + random value + auto increament

# MongoDB ODM

(Object Data Modeling)

MongoDB의 Collection에 집중하여 관리하도록 도와주는 패키지

Collection을 모델화하여 관련 기능들을 쉽게 사용할 수 있도록 도와줌

### 사용이유

- 연결 관리
    
    MongoDB의 기본 Node.js 드라이버는 연결 상태를 관리하기 어려움
    
    ⇒ Mongoose를 사용하면 간단하게 데이터베이스와의 연결상태를 관리해줌
    
- 스키마 관리
    
    스키마를 정의하지 않고 데이터를 사용하는 것은 NoSQL의 장점이지만, 데이터 형식을 미리 정의해야 코드 작성과 프로젝트 관리에 유용함
    
    ⇒ Mongoose는 Code-Level에서 스키마를 정의하고 관리할 수 있게 해줌
    
- Populate
    
    MongoDB는 기본적으로 Join을 제공x → 유사한 기능 쓰려면 aggregate라는 복잡한 쿼리 사용해야함
    
    ⇒ Mongoose의 populate를 사용하여 간단하게 구현 가능
    

## 사용 순서

---

### 1. **스키마 정의**

다양한  형식을 미리 지정하여 생성, 수정 작업 시 데이터 형식을 체크하는 기능 제공

- timestamps 옵션을 사용하면 생성, 수정 시간을 자동으로 기록해줌

```jsx
// ./models/schemas/board.js
const { Schema } = require('mongoose');
const PostSchema = new Schema({
	title: String,
	content: String,
}, {
	timestamps: true,
});

module.exports = PostSchema;
```

### 2. **모델 만들기**

작성된 스키마를 mongoose에서 사용할 수 있는 모델로 만드는 과정

모델의 이름을 지정하여 Populate 등에서 해당 이름으로 모델 호출 가능

```jsx
// ./models/index.js
const moongoose = require('mongoose');
const PostSchema = require('./schemas/board');
exports.Post = mongoose.model('Post', PostSchema);
```

### 3. **데이터 베이스 연결하기**

connect 함수를 이용해서 간단하게 데이터베이스와 연결

mongoose는 자동으로 연결을 관리 ⇒ 직접 연결 상태 체크하지 않아도 모델 사용 시 연결 상태를 확인하여 사용이 가능할 때 작업을 실행

```jsx
// index.js
const mongoose = require('mongoose');
const { Post } = require('./models');
mongoose.connect('mongodb://localhose:27017/myapp');
// Post 바로 사용 가능
```

### 4. 모델 사용하기

작성된 모델을 이용하여 CRUD를 수행 가능

## CRUD

---

### **CREATE**

- `create` : Document 생성 & 반환
    - create(Document Object) ⇒ 단일 Document 생성
    - create(Document Object 배열) ⇒ 복수 Document 생성

```jsx
// index.js
const { Post } = require('./models');

async function main() {
	const created = await Post.create({ // Document Object 전달
		title: 'first title',
		content: 'second title',
	});
	const multpleCreated = await Post.create([
		item1,
		item2
	_]);
}
```

### **READ**

`find` `findById` `findOne`

query를 사용하여 검색 (findById는 ObjectID로 검색)

```jsx
const { Post } = require('./models');

async function main() {
	const listPost = await Post.find(query);
	const ondPost = await Post.findOne(query);
	const postById = await Post.findById(id);
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
    		{ status: 'ACTIVE' }, // 둘 중 하나 가지고 있으면 찾음
    		{ isFresh: true }, 
    	],
    });
    ```
    

### **UPDATE**

1. `updateOne` `updateMany` : Document 수정
2. `findByIdAndUpdate` `findoneAndUpdate` : 검색된 Document에 업데이트를 반영하여 반환
- 기본적으로 `$set operator`를 사용하여 Document를 통째로 변경x
    
    ⇒ 있는 속성은 수정, 없다면 추가
    

```jsx
async function main() {
	const updateResult = await Post.updateOne (query, {
		...
	});
	const updateResults = await Post.updateMany (query, {
		...
	});
	const postById = await Post.findByIdAndUpdate(id, {
		...
	});
	const onePost = await Post.findOneAndUpdate(query, {
		...
	});
}
```

### **DELETE**

1. `deleteone` `deleteMany` : Document 삭제
2. `findByIdAndDelete` `findOneAndDelete` : 검색된 Document 반환함

```jsx
async function main() {
	const deleteResult = await Post.deleteOne (query);
	const deleteResults = await Post.deleteMany (query);
	const onePost = await Post.findOneAndDelete (query);
	const postById await Post. findByIdAndDelete (query);
}
```

## populate

---

RDB의 join과 유사한 기능을 제공하는 mongoose 자체 함수

Document안에 참조하는 ObjectID를 저장하고, 사용할 때 populate하여 하위 Document처럼 사용할 수 있게 해줌

```jsx
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
const post = await Post
	.find().populate(['user', 'comments']);
// post.user.name, post.comments[0].content
```