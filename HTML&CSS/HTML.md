# HTML

HyperText Markup Language

웹사이트에서 눈에 보이는 정보나 특정 구역을 설정할 때 사용하는 언어

## 웹 사이트 생성시 주의사항

- 웹 표준 : 웹에서 요구하는 공식 표준이나 기술 규격을 만족하는지 여부
- 웹 접근성 : 장애 여부와 상관없이 모두가 웹 사이트를 이용할 수 있는지 여부
- 크로스 브라우징 : 모든 브라우저와 기기에서 웹사이트가 제대로 작동하는지 여부

# HTML문서의 기본 구조

```html
<!DOCTYPE html> // HTML5라는 신조어로 문서를 선언

<html> // HTML문서의 시작

	<head> // 웹사이트의 간단한 요약정보 (웹사이트에서 노출x)
		<meta charset="UTF-8">
		<title>제목</title>
	</head>

	<body> // 웹사이트에서 노출되는 정보

	</body>

</html> // HTML문서의 끝
```

## head

### **meta**

- **charset**
    
    `<meta charset-"utf-8"/>`
    
    character setting의 약자, 모든 문자를 웹 브라우저에서 깨짐없이 표시하겠다는 의미
    
- **content / name**
    
    `<meta name="description" content="my site" />`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ae96032f-efa0-4dac-9b66-5634ad53b5b3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ae96032f-efa0-4dac-9b66-5634ad53b5b3.png)
    
    ![예시) 구글은 title 과 description 을 가져오기 때문에 검색시에 이렇게 뜬다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/61c97c45-cfe6-41cd-b54b-7878a00088b8.png)
    
    예시) 구글은 title 과 description 을 가져오기 때문에 검색시에 이렇게 뜬다
    
- **property**
    
    `<meta property="or:~" content="~"/>`
    
    카카오톡 공유 시 나오는 내용
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/66b5d8c2-4c8d-4bd6-94d7-4cc7c9d5ebca.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/66b5d8c2-4c8d-4bd6-94d7-4cc7c9d5ebca.png)
    

### title

`<title>tab-name</title>`

웹사이트 탭에 나타나는 제목

### **link**

탭 이미지 설정

- 사이즈가 조정되어 있다면 `sizes` 사용 안해도 됨

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/c1359f5e-3236-465d-b176-d3517dc86549.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/c1359f5e-3236-465d-b176-d3517dc86549.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/7c4323e8-88b2-4e8a-9663-166da11fc23c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/7c4323e8-88b2-4e8a-9663-166da11fc23c.png)

# 구성요소

## 전체 구조

[다운로드.jfif](HTML%206c2a44d79e234c508b10e6dc483a67c5/%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C.jfif)

### DOM

(Document Object Model) HTML 문서를 객체 기반으로 표현한 것, 노드 트리

### **NODE (노드)**

element의 상위 개념, 태그 노드와 텍스트 노드 전체를 가리키는 말

### **element (요소)**

`<tag> ~ </tag>`

ex) `<h1>hello world</h1>`

### **tag (태그)**

html이 갖고 있는 고유 기능 `<열린태그></닫힌태그>`

ex) `<a>`, `<p>`, `<span>`, `<div>`

### **attribute (속성)**

`<tag 속성='속성값'> ~ </tag>`

- 속성: 태그가 갖고 있는 추가 정보
- 속성값 : 어떤 역할을 수행할지 구체적인 명령을 진행
    
    ex) `<img src="#" />` 의 `src=""`
    
- HTML DOM 트리 안에서는 property가 됨 (js에서는 prop)
- 순서 상관없음

---

## **body의 컨테이너**

![Untitled](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled.png)

- `<header>` 상단 헤더 영역
- `<nav>` 네비게이션 바(메뉴) 영역
- `<main>` 웹사이트 본문 내용
    
    explore에서 지원x ⇒ `role="main"` 넣어줄 것
    
    - `<article>` 문서 내의 독립적인 컨텐츠를 위한 공간
    - `<section>` article보다 큰 영역을 나타냄
    - `<aside>` 사이드 영역, 보통 top버튼같이 본문 영역과 별개의 내용 포함
- `<footer>` 하단 영역 ex) 회사주소, 전화번호

### 이외

- `<address>` 가까운 html 요소의 연락처 정보
- `<p>` 문장
- `<span>` 짧은 단어

---

## 태그

### **<h1>**

Heading / 제목으로 숫자가 클수록 사이즈가 작아짐

- h1은 가장 중요한 정보로 보통 1번만 사용됨

### <p>

Paragraph / 본문 내용

### **<ul>**

unordered list (순서없는 리스트)

- <li> : list item/ 하위 리스트

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0462a2ce-62af-4b1c-910a-8d508a479091.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0462a2ce-62af-4b1c-910a-8d508a479091.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/5748bf00-3f06-4acc-b0ce-2cc2c261e9de.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/5748bf00-3f06-4acc-b0ce-2cc2c261e9de.png)

### **<ol>**

ordered list (순서 매긴 리스트)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3f73d7b3-7628-4b31-8c5c-a357dd687085.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3f73d7b3-7628-4b31-8c5c-a357dd687085.png)

### **<a>**

anchor(닻) / 연결, 링크 (이걸로 감싸면 링크로 이동)

- `href="URL"` (필수) : 링크 주소로 이동
- `target="_self"` 기본값/ 탭에서 바로 이동
    
    `target="_blank"` 새탭에서 열기
    

### **<img/>**

- `src="이미지주소"or"폴더/이름.확장자"/>`
- `alt="text"` 이미지 출력 실패or시각장애인 프로그램 실행시, 대체될 텍스트

### <table>

- <thead> / <tbody> / <tfoot> : 레이아웃에 영향을 주지 않지만 표의 요소를 나눌 수 있음
- <tr> : 테이블의 행
    - <th> : 테이블의 헤더부분 (쓰면 글씨 bold, 안쓰면 일반 글씨체)
    - **<**td> : 테이블의 열
- <caption> : 표의 제목, 설명
    
    ![Untitled](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled%201.png)
    

## <**input>**

입력하는 칸, 다양한 툴 모양 만들 수 있음

- input의 크기 설정시, 부모의 크기 설정 들어가야 함
- input의 유효성 검사하려면 <form> 안에 있어야 함 (안 그러면 required 등 작동 안됨)
    
    하지만 form 안에 있으면 자동 submit(event)되니 유의
    

![초록색이 input의 padding](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled%202.png)

초록색이 input의 padding

### **attributes**

- **`type="text"`** 내용 입력할 수 있는 빈칸 생성
- `**type="password"**` 입력이 *로 표시됨
- **`type="email / url / ..."`** 해당 형식만 입력 가능
- **`type="range"`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2b9e869a-080d-4f74-a13e-299754d9493e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2b9e869a-080d-4f74-a13e-299754d9493e.png)
    
- **`type="date"`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2bf5befc-cfa6-4b38-9a13-e6db48b11fcb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2bf5befc-cfa6-4b38-9a13-e6db48b11fcb.png)
    
- **`placeholder=”~”`** 빈칸에 써있는 문구
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/1af07a78-74c7-4b6f-8c9b-a8ea7187504f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/1af07a78-74c7-4b6f-8c9b-a8ea7187504f.png)
    
- **`text="submit"`** 자동으로 데이터를 전송할 수 있는 버튼이 생성
    - 버튼 클릭 시, 지정된 URL로 입력된 값이 'action' 속성으로 지정 서버 페이지로 전송 (새로고침됨)
    - `value="~"`  버튼명 변경
    - <button>과의 차이
        - type 속성을 명시하지 않아도 기본적으로 submit 기능 수행
        - 디자인이 input보다 자유로워 자주 사용됨
        - 속성값
            - `type="submit"` : 폼의 전송 기능을 담당한다.
            - `type="reset"` : 폼 작성 내용을 초기화하는데 사용한다.
            - `type="button"` : 흔히 자바스크립트를 이용한 기능 구현에 많이 사용한다.

- **`disabled`** 뭐든지 disable 붙이면 기능하지 않음 (위 버튼 클릭불가)
- **`required`** 반드시 기입해야 함
    - <form>안에 input이 있어야 유효성 검사 가능
- `**minlength="n"` / `maxlength = “n”`** 입력값의 최대길이 , 최소길이 설정
- **`type="file"`**파일선택 버튼 생성
    - **`type="file" acept="확장자"`** 지정 확장자 파일만 선택 가능
        
        ex) `type="file" acept="image/*"` : 이미지 다 가능
        
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/4e0e4a0c-9471-4137-a024-e461042a119a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/4e0e4a0c-9471-4137-a024-e461042a119a.png)
    

## **label**

사용자 인터페이스 항목의 설명

- input과 함께 쓰임 (클릭하면 인풋창에 커서)
- `<label for="input-id-name">label-content</label>`
    
    input의 id가 for에 들어가야 연결됨
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/94eef806-7166-4f7e-af40-f4bded5fa469.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/94eef806-7166-4f7e-af40-f4bded5fa469.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/58c4d135-d5fa-4f7b-a40e-7fb4629712ef.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/58c4d135-d5fa-4f7b-a40e-7fb4629712ef.png)
    

---

## 선택자

## **id**

`id="id-name"`

- 모든 tag에 들어갈 수 있음
- id 값은 고유해야 함

## class

`class="class-name class-name ..."`

- id와 달리 여러 태그에 중복 사용 가능
- 한 태그가 여러 class 가질 수 있음
- BEM(Block Element Modifier) **:** class 만드는 효율적 방법 ([설명](https://nykim.work/15))
    
    `block--(modifier)__element`
    

# **주석**

### html 주석

```html
<!-- content -->

<!--
개행된 내용도 모두 주석 처리!
-->
```

### css 주석

```css
/* 주석 */

/*
여러줄
*/
```

- `<br>` : 줄바꿈