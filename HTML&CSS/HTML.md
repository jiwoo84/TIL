# HTML

# 생성 **규칙**

- **파일명 지정**
    
    index.html
    
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

- **기본적인 html  구문**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/e58b7cd9-9c89-4aa2-be39-18447ba2a2ee.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/e58b7cd9-9c89-4aa2-be39-18447ba2a2ee.png)
    

- **lang**
    
    주된 언어를 브라우저에 알려줌
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/95489b22-019c-4e7c-a094-9285121658a0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/95489b22-019c-4e7c-a094-9285121658a0.png)
    

## 구성요소

[다운로드.jfif](HTML%206c2a4/%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C.jfif)

- DOM
    
    [돔이란?](https://velog.io/@yejineee/DOM%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-DOM-Node%EC%99%80-Element%EC%9D%98-%EC%B0%A8%EC%9D%B4)
    
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
    

# <**head> - <tag>**

1. **title (탭 이름)**
    
    **`<title> </title>`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/575335e2-0b76-43da-81d3-a4a3be23f991.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/575335e2-0b76-43da-81d3-a4a3be23f991.png)
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/114e0e4b-bdf4-4555-a6e4-70b3b7fc7046.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/114e0e4b-bdf4-4555-a6e4-70b3b7fc7046.png)

1. **meta**
    
    
    - **content / name**
        
        **`<meta name="description" content="my site" />`**
        
        - attributes 의 순서 상관 x
        - self-closing 이지만 /는 쓰던 말던 내자유
        
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

1.  **link**
    
    탭 이미지 설정
    
    - 사이즈가 조정되어 있다면 `sizes` 사용 안해도 됨
    - 이미지에 따라 실행 안되기도 함 (왜?? 모름)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/c1359f5e-3236-465d-b176-d3517dc86549.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/c1359f5e-3236-465d-b176-d3517dc86549.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/7c4323e8-88b2-4e8a-9663-166da11fc23c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/839bbd6dd87a440e8d25b344d131199a/7c4323e8-88b2-4e8a-9663-166da11fc23c.png)

- **검색 팁**
    
    **구글 검색시 mdn 키워드 포함할 것**
    
    mozilla developer network 사이트를 안내해줌
    
    (firefox 브라우저 만든 회사 제공)
    
    아니면 w3 shools 가 나오는데 절대 사용x
    
    많은 코드들이 있고 찾아가면서 하면 됌
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/60497aa8-90b0-4582-9e10-6390b0c22980.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/60497aa8-90b0-4582-9e10-6390b0c22980.png)
    

# <**body> - <tag>**

## **<h1> : 글씨 두껍고 크게**

- </h1>: 태그 끝내기 (/)
- <h2,3...6> : 숫자 커질수록 글씨 크기 점점 작아짐
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0cf3ac6f-aa66-4f6f-8291-c6f8cfc4d4cd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0cf3ac6f-aa66-4f6f-8291-c6f8cfc4d4cd.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/a3e5eb2c-cfb3-41d2-a6ec-a95b5aa221d7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/a3e5eb2c-cfb3-41d2-a6ec-a95b5aa221d7.png)
    

## **<ul> : unordered list (순서없는 리스트)**

- <li> : list item/ 하위 리스트

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0462a2ce-62af-4b1c-910a-8d508a479091.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0462a2ce-62af-4b1c-910a-8d508a479091.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/5748bf00-3f06-4acc-b0ce-2cc2c261e9de.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/5748bf00-3f06-4acc-b0ce-2cc2c261e9de.png)

## **<ol> : ordered list (순서 매긴 리스트)**

 위 코드에서 ul ->ol 로 바꾸면 된다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3f73d7b3-7628-4b31-8c5c-a357dd687085.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3f73d7b3-7628-4b31-8c5c-a357dd687085.png)

## **<a> : anchor (닻) / 연결, 링크**

****attributes(속성)이 필요

- **href : HTTP reference & hyperlink reference 링크 주소입력**
    
    **`<a href="http://google.com"> Go to google.com </a>`**
    

- **target="_self" 기본값/ 탭에서 바로 이동**
    
    target="_blank" 새탭에서 열기
    
    **`<a href="http://google.com" target="_self"> go to google </a>`**
    

## **<img> : 이미지**

 self closing tag (</img> 존재x)

- **이미지 주소로 넣기**
    
    src= sourc
    
    **`<img src="이미지 주소"/>`** (★링크주소 아니라 이미지주소)
    
- **저장한 이미지 넣기**
    
    **`<img src="폴더/이름.확장자">`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/fce38f2d-8486-45c4-bce1-8eec2762b744.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/fce38f2d-8486-45c4-bce1-8eec2762b744.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/43c37458-e1cf-4027-aa12-f19736fbadad.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/43c37458-e1cf-4027-aa12-f19736fbadad.png)
    

## **input**

- 입력하는 칸, 다양한 툴 모양 만들 수 있음
- input의 크기 설정시, 부모의 크기 설정 들어가야 함
- input의 유효성 검사하려면 <form> 안에 있어야 함 (안 그러면 required 등 작동 안됨)
    
    하지만 form 안에 있으면 자동 submit(event)되니 유의
    

![초록색이 input의 padding](HTML%206c2a4/Untitled.png)

초록색이 input의 padding

- **attributes**
    - **`type="text"`**
        
        내용 입력할 수 있는 빈칸 생성
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0371dfe1-f617-4e74-87f7-737dbfbe26c9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0371dfe1-f617-4e74-87f7-737dbfbe26c9.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/262cf2a6-12bc-4a76-a4bb-ab976fdc758c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/262cf2a6-12bc-4a76-a4bb-ab976fdc758c.png)
        
    - `**type=”password”**`
        
        ![Untitled](HTML%206c2a4/Untitled%201.png)
        
    - **`type="email or url..."`** 해당 형식만 입력 가능
        
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
        1. 자동으로 데이터를 전송할 수 있는 버튼이 생성
        2. 버튼을 클릭하면 지정된 URL로 <form>태그 안에 입력된 값들이 'action' 속성으로 지정된 서버 페이지로 전송 (새로고침됨)
        - `value="~"`  버튼명 변경
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/bc625734-86e5-4ca7-89a9-ffca129c5284.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/bc625734-86e5-4ca7-89a9-ffca129c5284.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/23fd886f-2834-400c-b788-a5d03dde5544.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/23fd886f-2834-400c-b788-a5d03dde5544.png)
        
        - <button>과의 차이
            
            폼 전송 기능을 하는 `<input type="submit">` 과 `<button>` 은 기능적으로 동일 
            
            기본적으로 button 요소는 type 속성을 명시하지 않으면 submit 기능을 수행
            
            - button 속성값
                - `type="submit"` : 폼의 전송 기능을 담당한다.
                - `type="reset"` : 폼 작성 내용을 초기화하는데 사용한다.
                - `type="button"` : 흔히 자바스크립트를 이용한 기능 구현에 많이 사용한다.
    
    - **`disabled`**
    
    뭐든지 disable 붙이면 기능하지 않음 (위 버튼 클릭불가)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/7fc880ac-529a-4fbe-85b0-0d3bab416521.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/7fc880ac-529a-4fbe-85b0-0d3bab416521.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/80c162fb-3cb6-4957-af32-30bf86da4999.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/80c162fb-3cb6-4957-af32-30bf86da4999.png)
    
    - **특성마다 사용 가능 유형이 있으니 주의!**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/cda746c0-5a19-4ed4-b3b4-52a07dc52f72.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/cda746c0-5a19-4ed4-b3b4-52a07dc52f72.png)
    
    - **`required`**
        
        반드시 기입해야 함
        
        (<form>안에 input이 있어야 유효성 검사 가능)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/d83881be-d732-4c74-a97e-6eb2bd952a71.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/d83881be-d732-4c74-a97e-6eb2bd952a71.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/e3d0d4a2-1474-40e4-a75c-4f848d9b1fc4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/e3d0d4a2-1474-40e4-a75c-4f848d9b1fc4.png)
        
    - `**minlength="n"`**  입력값의 최소길이 n
        
        `**maxlength = “n”**` 입력값의 최대길이가 n
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/33bf30fa-4ce4-4750-96f8-f0a8e483d63b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/33bf30fa-4ce4-4750-96f8-f0a8e483d63b.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/afda54be-f10a-476c-b2e0-4c33e4a85d8e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/afda54be-f10a-476c-b2e0-4c33e4a85d8e.png)
        
    - **`type="file"`**
        
        파일선택 버튼 생성
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/cdcd4bee-9950-4319-b3a1-b600785273f3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/cdcd4bee-9950-4319-b3a1-b600785273f3.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/4e0e4a0c-9471-4137-a024-e461042a119a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/4e0e4a0c-9471-4137-a024-e461042a119a.png)
        
    
    ****	
    
    - **`type="file" acept="확장자"`**
        
        지정 확장자 파일만 선택 가능
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0650fe49-c613-4bad-9d15-9a6ace2e58fd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/0650fe49-c613-4bad-9d15-9a6ace2e58fd.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2eccb2bf-ae17-4c2f-94dc-46dea1d3b2cd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/2eccb2bf-ae17-4c2f-94dc-46dea1d3b2cd.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3a09c432-3fa4-4b85-8e88-457a4e007c52.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/3a09c432-3fa4-4b85-8e88-457a4e007c52.png)
        
        image/* 넣으면 이미지면 다 가능 (jpg, png, svg...)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/f3bf8de7-77ab-416c-aec0-e65ac6908a3b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/f3bf8de7-77ab-416c-aec0-e65ac6908a3b.png)
        
        png, pdf 만 가능
        

## **label**

- 사용자 인터페이스 항목의 설명
- input과 함께 쓰임 (클릭하면 인풋창에 커서)
- for과 id의 value 가 동일해야 함 (노란 밑줄 두개)
    
    동시에 변경하려면 [alt +다른 하나] 클릭
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/94eef806-7166-4f7e-af40-f4bded5fa469.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/94eef806-7166-4f7e-af40-f4bded5fa469.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/58c4d135-d5fa-4f7b-a40e-7fb4629712ef.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/58c4d135-d5fa-4f7b-a40e-7fb4629712ef.png)
    

## **id**

- 모든 tag에 들어갈 수 있음
- id 값은 고유해야 함
    
    (form, input 둘이 같은 id값이면 작동 안됨
    
     css가 id값을 찾아서 작동하기 때문에 겹치면 안됨)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/91a897d9-316c-4067-aa24-4c413cb1dcd9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/91a897d9-316c-4067-aa24-4c413cb1dcd9.png)
    

## 컨테이너

같은 줄에 위치하도록 묶는 박스

읽기만 해도 의미 짐작 가능한 tag

- **`semantic`**
- `header` =  div id="header"
- `main` =  div id="main"
- `footer` = div id="footer" (꼬릿말)
- `address`
    
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/9fee8714-490d-4303-9c07-5cfeda57a5ab.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/9fee8714-490d-4303-9c07-5cfeda57a5ab.png)
    
    ↳ 안 좋은 예 (div만 보면 이게 제목인지 내용인지 모름)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ed606e5c-2b6e-4570-9b84-8cb6b01cf8f0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/839bbd6dd87a440e8d25b344d131199a/ed606e5c-2b6e-4570-9b84-8cb6b01cf8f0.png)
    
    ↳ semantic 사용 예
    
    (div 처럼 줄 나누기도 되면서 뭔지도 알 수 있음)
    
- `<p>` 문장 `</p>`
    
    `<span>` 짧은 text `<span>`
    
    : 둘 다 의미 없음 like <div>
    
    *<span>은 <div>와 매우 유사하지만,* 
    
    *<div>는 블록 레벨 요소인 반면 <span>은 인라인 요소입니다.*
    

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