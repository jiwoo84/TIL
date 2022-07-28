# HTML

# 생성 **규칙**

### **파일명 지정**

`index.html`

대부분의 웹서버가 디폴트로 위 제목의 파일을 찾음

```html
<!DOCTYPE html> //시작시 무조건!

<html> //html 열고

	<head>//웹사이트 환경설정(안보임)

	</head>

	<body> //출력되는 내용(보임)

	</body>

</html> //html 닫고
```

### **기본적인 html  구문**

`<tag attrname=”attrvalue”> ~ </tag>`

# 구성요소

[다운로드.jfif](HTML%206c2a44d79e234c508b10e6dc483a67c5/%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C.jfif)

- DOM [돔이란?](https://velog.io/@yejineee/DOM%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-DOM-Node%EC%99%80-Element%EC%9D%98-%EC%B0%A8%EC%9D%B4)

- **NODE (노드)**
    
    element의 상위 개념
    
    태그 노드와 텍스트 노드 전체를 가리키는 말
    

- **element (요소)**
    
    `<tag> ~ </tag>`
    
    ex) `<h1>hello world</h1>`
    
- **tag (태그)**
    
    `<tag>`
    
    ex) `<a>`, `<p>`, `<span>`, `<div>`
    
- **attribute (속성)**
    
    <tag att=”~”> ~ </tag>
    
    ex) `<img src="#" />` 의 `src=""`
    
    - HTML 요소의 추가적인 정보를 전달함
    - HTML DOM 트리 안에서는 property가 됨 (js에서는 prop)
    - 순서 상관없음
    

# <**head> - <tag>**

### **title (탭 이름)**

**`<title>tab-name</title>`**

![Untitled](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled.png)

### **meta**

- **content / name**
    
    **`<meta name="description" content="my site" />`**
    
    - self-closing tag (끝에 / 안써도 됌)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ae96032f-efa0-4dac-9b66-5634ad53b5b3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ae96032f-efa0-4dac-9b66-5634ad53b5b3.png)
    
    ![예시) 구글은 title 과 description 을 가져오기 때문에 검색시에 이렇게 뜬다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/61c97c45-cfe6-41cd-b54b-7878a00088b8.png)
    
    예시) 구글은 title 과 description 을 가져오기 때문에 검색시에 이렇게 뜬다
    

- **charset** (self-closing)
    
    **`<meta charset-"utf-8"/>`**
    
    브라우저가 문자를 이해하고, 깨지지 않게 함
    
- **property**
    
    **`<meta property="or:~" content="~"/>`**
    
    카카오톡 공유 시 나오는 내용
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/66b5d8c2-4c8d-4bd6-94d7-4cc7c9d5ebca.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/66b5d8c2-4c8d-4bd6-94d7-4cc7c9d5ebca.png)
    

### **link**

탭 이미지 설정

- 사이즈가 조정되어 있다면 `sizes` 사용 안해도 됨

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/c1359f5e-3236-465d-b176-d3517dc86549.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/c1359f5e-3236-465d-b176-d3517dc86549.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/7c4323e8-88b2-4e8a-9663-166da11fc23c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/7c4323e8-88b2-4e8a-9663-166da11fc23c.png)

# <**body> - <tag>**

### **<h1> : 글씨 두껍고 크게**

- </h1>: 태그 끝내기 (/)
- <h2,3...6> : 숫자 커질수록 글씨 크기 점점 작아짐

### **<ul> : unordered list (순서없는 리스트)**

- <li> : list item/ 하위 리스트

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0462a2ce-62af-4b1c-910a-8d508a479091.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0462a2ce-62af-4b1c-910a-8d508a479091.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/5748bf00-3f06-4acc-b0ce-2cc2c261e9de.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/5748bf00-3f06-4acc-b0ce-2cc2c261e9de.png)

### **<ol> : ordered list (순서 매긴 리스트)**

 위 코드에서 ul ->ol 로 바꾸면 된다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3f73d7b3-7628-4b31-8c5c-a357dd687085.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3f73d7b3-7628-4b31-8c5c-a357dd687085.png)

### **<a> : anchor (닻) / 연결, 링크**

****attributes(속성)이 필요

- **href : HTTP reference & hyperlink reference 링크 주소입력**
    
    `<a href="http://google.com"> Go to google.com </a>`
    

- **target="_self" 기본값/ 탭에서 바로 이동**
    
    target="_blank" 새탭에서 열기
    
    `<a href="http://google.com" target="_self"> go to google </a>`
    

### **<img> : 이미지**

 self closing tag (</img> 존재x)

- 이미지 주소로 넣기
    
    `<img src="이미지 주소"/>` (★링크주소 아니라 이미지주소)
    
- 저장한 이미지 넣기
    
    `<img src="폴더/이름.확장자">`
    

## table (표)

- **<table>** : 테이블을 만듬
    - <thead> / <tbody> / <tfoot> : 레이아웃에 영향을 주지 않지만 표의 요소를 나눌 수 있음
    - **<tr>** : 테이블의 행
        - <th> : 테이블의 헤더부분 (쓰면 글씨 bold, 안쓰면 일반 글씨체)
        - **<td>** : 테이블의 열
    - <caption> : 표의 제목, 설명
        
        ![Untitled](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled%201.png)
        

---

## **input**

- 입력하는 칸, 다양한 툴 모양 만들 수 있음
- input의 크기 설정시, 부모의 크기 설정 들어가야 함
- input의 유효성 검사하려면 <form> 안에 있어야 함 (안 그러면 required 등 작동 안됨)
    
    하지만 form 안에 있으면 자동 submit(event)되니 유의
    

![초록색이 input의 padding](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled%202.png)

초록색이 input의 padding

### **attributes**

- **`type="text"`**
    
    내용 입력할 수 있는 빈칸 생성
    
- `**type="password"**`
    
    ![Untitled](HTML%206c2a44d79e234c508b10e6dc483a67c5/Untitled%203.png)
    
- **`type="email / url / ..."`** 해당 형식만 입력 가능
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ba354fcb-23f2-41be-8c27-4fef6a1ce346.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ba354fcb-23f2-41be-8c27-4fef6a1ce346.png)
    

- **`type="range"`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2b9e869a-080d-4f74-a13e-299754d9493e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2b9e869a-080d-4f74-a13e-299754d9493e.png)
    

- **`type="date"`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2bf5befc-cfa6-4b38-9a13-e6db48b11fcb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2bf5befc-cfa6-4b38-9a13-e6db48b11fcb.png)
    

- **`placeholder=”~”`**
    
    빈칸에 써있는 문구
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/92627613-36a8-48b5-8006-e05f601affc6.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/92627613-36a8-48b5-8006-e05f601affc6.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/1af07a78-74c7-4b6f-8c9b-a8ea7187504f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/1af07a78-74c7-4b6f-8c9b-a8ea7187504f.png)
    

- **`text="submit"`**
    - 자동으로 데이터를 전송할 수 있는 버튼이 생성
    - 버튼 클릭 시, 지정된 URL로 입력된 값이 'action' 속성으로 지정 서버 페이지로 전송 (새로고침됨)
    - `value="~"`  버튼명 변경
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/bc625734-86e5-4ca7-89a9-ffca129c5284.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/bc625734-86e5-4ca7-89a9-ffca129c5284.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/23fd886f-2834-400c-b788-a5d03dde5544.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/23fd886f-2834-400c-b788-a5d03dde5544.png)
    
    - <button>과의 차이
        - type 속성을 명시하지 않아도 기본적으로 submit 기능 수행
        - 디자인이 input보다 자유로워 자주 사용됨
        - 속성값
            - `type="submit"` : 폼의 전송 기능을 담당한다.
            - `type="reset"` : 폼 작성 내용을 초기화하는데 사용한다.
            - `type="button"` : 흔히 자바스크립트를 이용한 기능 구현에 많이 사용한다.

- **`disabled`**

뭐든지 disable 붙이면 기능하지 않음 (위 버튼 클릭불가)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/7fc880ac-529a-4fbe-85b0-0d3bab416521.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/7fc880ac-529a-4fbe-85b0-0d3bab416521.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/80c162fb-3cb6-4957-af32-30bf86da4999.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/80c162fb-3cb6-4957-af32-30bf86da4999.png)

- **`required`**
    
    반드시 기입해야 함
    
    (<form>안에 input이 있어야 유효성 검사 가능)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/d83881be-d732-4c74-a97e-6eb2bd952a71.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/d83881be-d732-4c74-a97e-6eb2bd952a71.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/e3d0d4a2-1474-40e4-a75c-4f848d9b1fc4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/e3d0d4a2-1474-40e4-a75c-4f848d9b1fc4.png)
    
- `**minlength="n"` / `maxlength = “n”`**
    
    입력값의 최대길이 , 최소길이 설정
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/33bf30fa-4ce4-4750-96f8-f0a8e483d63b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/33bf30fa-4ce4-4750-96f8-f0a8e483d63b.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/afda54be-f10a-476c-b2e0-4c33e4a85d8e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/afda54be-f10a-476c-b2e0-4c33e4a85d8e.png)
    

- **`type="file"`**
    
    파일선택 버튼 생성
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/cdcd4bee-9950-4319-b3a1-b600785273f3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/cdcd4bee-9950-4319-b3a1-b600785273f3.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/4e0e4a0c-9471-4137-a024-e461042a119a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/4e0e4a0c-9471-4137-a024-e461042a119a.png)
    
    - **`type="file" acept="확장자"`**
        
        지정 확장자 파일만 선택 가능
        
        ex) `type="file" acept="image/*"` : 이미지 다 가능
        
        ****
        

---

## **label**

- 사용자 인터페이스 항목의 설명
- input과 함께 쓰임 (클릭하면 인풋창에 커서)
- `<label for="input-id-name">label-content</label>`
    
    input의 id가 for에 들어가야 연결됨
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/94eef806-7166-4f7e-af40-f4bded5fa469.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/94eef806-7166-4f7e-af40-f4bded5fa469.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/58c4d135-d5fa-4f7b-a40e-7fb4629712ef.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/58c4d135-d5fa-4f7b-a40e-7fb4629712ef.png)
    

## 컨테이너

같은 줄에 위치하도록 묶는 박스

읽기만 해도 의미 짐작 가능한 tag

- `semantic`
- `<header>`
- `<main>`
- `<footer>`
- `<address>`
- `<p>` 문장
- `<span>` 짧은 단어

## **id**

- 모든 tag에 들어갈 수 있음
- id 값은 고유해야 함
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/91a897d9-316c-4067-aa24-4c413cb1dcd9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/91a897d9-316c-4067-aa24-4c413cb1dcd9.png)
    

## class

- id와 달리 여러 태그에 중복 사용 가능
- 한 태그가 여러 class 가질 수 있음
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0acf8cb4-5f41-4af0-ab4c-d0705a678e16.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0acf8cb4-5f41-4af0-ab4c-d0705a678e16.png)
    

---

## **주석 달기**

- html 주석
    
    ```html
    <!-- content -->
    
    <!--
    개행된 내용도 모두 주석 처리!
    -->
    ```
    

- css 주석
    
    ```css
    /* 주석 */
    
    /*
    여러줄
    */
    ```
    

- `<br>` : 줄바꿈