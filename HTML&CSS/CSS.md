# CSS

---

# 기본

### CSS의 기본 **설정 사항 없애기**

- reset.css 파일 만들기
    
    ① 파일 (reset.css) 새로 만듬
    
    ② 코드 복붙 ([사이트](https://meyerweb.com/eric/tools/css/reset/))
    
    ③ css 파일에 `@import "reset.css"` 추가
    
    +css파일에 추가하는게 좋음
    
    [https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/58d42e7d-d476-4e28-81af-ad9c9c7cb9a1.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/58d42e7d-d476-4e28-81af-ad9c9c7cb9a1.webm)
    

### 브라우저와 공간 사이 공백 제거

```css
/* 1. html, body의 기본 margin, padding값 제거 */
html, body {
	margin : 0;
	padding: 0;
}

/* 2. 모든 태그의 기본 margin, padding값 제거 */
* {
	margin : 0;
	padding: 0;
}
```

### 사이즈 단위

- px : 절대 크기
- % : 상대 크기, 현재 창크긱 기준
- em : 상대 크기, 현재 스타일이 지정된 요소의 font-size 기준

## CSS 연동

### Inline Style Sheet

html 태그 안에 직접 원하는 스타일 적용

ex) `<h1 style="color: red;">hello world</h1>`

### Internal Style Sheet

html 파일 → <head> 태그 → <style> 태그 안에 css코드 작성

```html
<head>
	<style>
		<!-- css 코드 작성 -->
	</style>
</head>
```

### External Style Sheet 👑

css 파일 따로 만들고, 링크 연결

```html
<head>
	<link rel="stylesheet" href="style.css">
</head>
```

(단축 코드: `link:css`)

---

## 캐스캐이딩

CSS적용의 우선순위

### 1. 순서

나중에 적용한 속성값의 우선순위가 높음

### 2. 디테일

더 구체적으로 작성된 선택자의 우선순위가 높음

```css
/* header > p 지정시 */
header p { color: red; } /* 최종 실행 */
p { color: blue; }
```

### 3. 선택자

<aside>
💡 style > id > class > type

</aside>

---

## css 적용의 우선순위

1. 속성 값 뒤에 !important
2. HTML태그에 inline으로 style속성 지정
3. id선택자 > class선택자, 추상 클래스 (예 `:hover`) > 태그 선택자

# Selector (선택자)

### Type

`tag { 속성: 속성값; }`

지정 태그 안에 있는 내용 모두 선택됨

### Id

`#id {속성: 속성값}`

- ID 여러개 지칭하는 법 : `#id, #id, #id ... {속성:속성값;}`

### C**lass**

`.class {속성:속성값;}`

- class 안의 class 선택하기 : `.class1 .class2 {~;}`

### 이외

- 전체 선택 : `* {속성: 속성값}`
- `tag.class` or `tag#id` (띄어쓰기x) ⇒ tag 중에서 class나 id 찾기
    
    (`tag .class` or `tag #id` ⇒ tag의 자식 중에서 찾기)
    

---

## **combinator (연결자)**

선택자 사이에 관계를 설정하는 방식

### 부모·자식 **지정**

- `부모 자식 {…}` : 부모 안 모든 자식태그에 적용
- `부모 > 자식 {…}` : 직계 자식에게만 적용
- `자식 + 자식 {…}` : 인접 선택자/ 바로 다음에 있는 자매 tag에 지시
- `자식~자식 {…}` : 뒤에 오는 자매 모두에게 지시 (바로 뒤x)

```
a:link { color: red; }
a:visted { color: purple; }

```

```html
<head>
	<stlye>
		h1 { color: red; } // 자식 본인의 속성값 지정
		header { color: blue; } // 부모의 속성값 지정 (뒤에 나왔어도 영향x)
	</style>
</head>

<body>
	<header>
		<h1>naver</h1> // 빨간색 
	</header>
</body>
```

부모태그의 모든 속성이 자식에게 상속x ⇒ 동일한 속성에 다른 속성값을 가진다면 자식은 자신의 속성값을 가짐

### 속성 지정

- `[속성] {...}` : 특정 속성을 가진 요소 모두 선택

```html
<input type="text" placeholder="username" required />
<input type="e-mail" placeholder="e-mail" />
```

```css
input:required { color: blue; } /* required한 input에만 적용 */
input:optional { color: red; } /* required하지 않은 input에 적용 */
```

### 속성-속성값 지정

`tag[속성="속성값"] {~}`

- 지정값 제외 : `tag:not ([속성="속성값"]) {~}`
- 문자열 속성 선택자
    1. `[속성 ~= "string"] {…}`
        
        해당 속성-속성값에 ‘string’이라는 문자열을 포함하고 있다면 모두 포함
        
        - 공백 기준으로 문자열을 인식
            
            ⇒ ex) ‘string’, ‘love string’ 가능 / ‘lovestring’ 불가능  
            
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/625a0152-30c8-42de-9743-b7e26963306f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/625a0152-30c8-42de-9743-b7e26963306f.png)
        
    2. `[속성 ^= "string"] {…}`
        
        해당 속성-속성값이 ‘string’으로 시작하는 요소 모두 포함
        
    3. `[속성 $= "string"] {…}`
        
        해당 속성-속성값이 ‘string’으로 끝나는 요소 모두 포함
        

---

## **pseudo selector**

여러 tag에 하나하나 id나 class 지정하기보다, 효율적으로 순서를 매겨서 지시하는 방법

형제 사이에서의 순서에 따라 요소를 선택

### tag: **nth-child**

- `first-child {…}` 형제 요소 중 가장 첫 요소에 적용
- `last-child {…}` 형제 요소 중 가장 마지막 요소에 적용
- `nth-child(숫자)` 지정한 순서에 적용
- `nth-child(even)` 짝수에 적용
- `nth-child(odd)` 홀수에 적용
- `nth-child(숫자n+숫자)`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ee0e527e-2e0c-4d9b-a995-816062e9472a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ee0e527e-2e0c-4d9b-a995-816062e9472a.png)
    
    ![첫번째 적용 후, 3번째마다 적용됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/783d50bf-ec9b-4538-8f4a-aec243377282.png)
    
    첫번째 적용 후, 3번째마다 적용됨
    

### tag: **nth-of-type(n)**

동일한 타입들 안에서 순서를 따짐

(even, odd, 2n+1 … 을 넣어서 활용 가능)

- `first-of-type`  첫번째
- `last-of-type` 마지막
- `nth-of-type(2)` 2번째 span 에 적용

### 주의사항

- 타입은 신경X, 오직 순서만 신경
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7d02766a-91e9-4931-ab0b-7ad0e59fdddd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7d02766a-91e9-4931-ab0b-7ad0e59fdddd.png)
    
- `tag : first-child` 하면 tag 안에 박스의 first-child도 선택됨
    
    ```html
    <main>
      <p>Hello World</p> // 적용
    	<p>Hello World</p>
    	<div>
    		<p>Hello World</p> // 적용(?)
    	</div>
    </main>
    ```
    
    ```css
    main p:first-child {
      color: red;
    }
    ```
    
    여기서 이렇게 하면 맨 위, 맨 아래 아이콘만 선택되는 것이 아니라 <span>안에 <i>도 선택
    

---

## **pseudo element**

### **::placeholder**

`tag::placeholder {…}`

tag 중 placeholder에만 적용 (입력텍스트에는 적용x)

### **::selection**

`tag::selection {…}`

드래그 된 부분만 적용 (padding 은 적용 안됨)

### ::**first-letter**

`tag::first-letter {…}`

첫번째 글자만 적용

- `first-line` : 첫번째 줄에 적용

# BOX

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/b754122e-ab70-47ee-8c6b-8d23a372e2a8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/b754122e-ab70-47ee-8c6b-8d23a372e2a8.png)

## margin

기본으로 body는 margin 값 가짐 (삭제: `margin: 0;`)

### 값 설정

- `margin-top/ left/ right/ botom;`
- `margin: 숫자;` 사방에 다 적용
- `margin: 상 우 하 좌` (시계방향)
- `margin: 상하 좌우`
- **`margin: 0 auto;`**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/82221621-50f9-4316-af34-9b0db6b918d0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/82221621-50f9-4316-af34-9b0db6b918d0.png)
    
    - 가로 정중앙 만들 수 있는 코드
    - space-between은 글자수에 따라 중앙 아닐 수 있음 → auto를 적절히 잘 사용하면 가능

### collapsing margins (마진병합현상)

경계가 닿으면 박스의 margin이 같아지는 현상

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/71735d27-e3c5-42f9-a44a-53e6f131eb27.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/71735d27-e3c5-42f9-a44a-53e6f131eb27.png)

1. **형제 간의 마진 병합**
    
    인접 형제 박스 간 상하 마진이 겹칠 때⇒ 같거나 큰 값으로 상쇄
    
2. **부모 자식간의 마진 병합**
    
    부모와 첫번째(or 마지막) 자식의 상단(or 하단) 마진이 겹칠 때
    
    → (예상) 자식에 margin-top or bottom 지정 시, 자식만 내려오거나 올라옴
    
    → (실제 실행) 부모도 같이 내려오거나 올라옴 (값의 크기와는 상관없이 상쇄된 마진은 부모 박스의 바깥으로 나타남)
    
    ⇒ 부모 박스에 padding이나 border값을 주어 벽을 만들어 예방 가능
    
3. **빈 요소의 상하 마진이 겹칠 때**
- 상쇄 규칙 예외
    - 박스가 `position: absolute` 된 상태
    - 박스가 `float: left/right` 된 상태 (단, clear 되지 않은 상태)
    - 박스가 `display: flex` 일 때 내부 flexbox item
    - 박스가 `display: grid` 일 때 내부 grid item

---

## **border**

### 속성 지정

- `border: 두께 스타일 색상`
- `border-style` 스타일 변경 ex) solid, dotted …
- `border-radius` 모서리 둥글게 만들기
    - 원 모양 `border-radius: 50%`
    - 특정 모서리만 수정 `border- (top or bottom) - (left or right) - radius : ~;`
        
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/bcb5f19b-72ac-43f7-88b3-d7242c174069.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/bcb5f19b-72ac-43f7-88b3-d7242c174069.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ae5166a0-fefb-474a-b087-46a7fccc8591.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ae5166a0-fefb-474a-b087-46a7fccc8591.png)
        
- **box사이즈 유지하면서 border만들기**
    
    **`box-sizing: border-box`**
    
    width,height 지정 상태에서 border 지정 
    
    → 크기 유지 위해 박스가 커짐 (width: 50px / border: 30px ⇒ 크기 80px이 됨) 
    
    → **`box-sizing: border-box` 사용** 
    
    **⇒** box사이즈 신경쓰지 않고 border 만들어짐
    
    (width: 50px / border: 30px ⇒ 결과적으로 50px으로 보임)
    

### **border vs outline**

- border : 상자 바깥으로 확장하면서 테두리 적용
- outline : 상자 안쪽으로 테두리 생김

∴ border은 박스 크기가 커짐/ outline은 변화 없음

# Block / Inline

 `display: ~;`

## **block**

1. y축 정렬 형태로 출력 (줄바꿈 현상)
2. width, heigth로 크기 지정 가능
3. 상하 배치 작업 가능

ex) `<div>` `<header>` `<address>` `<p>` 등 대다수

## **inline**

1. x축 정렬 형태로 출력 (한 줄에 다같이 출력)
2. 크기 지정 불가능
3. 상하 배치 작업 불가능

ex)  `<span>` `<a>` `<img>` `<code>` 등 일부 (이거 외우는게 편함)

- box 지정
    - padding : 사방에 작용
    - margin : 좌우만 작용(사방에 만들고 싶다면 block)
- `vartical-align` : inline에만 사용되는 y축 정렬

## **inline-block**

inline&block의 특성 동시 적용

- **장점** : inline 처럼 한 줄이지만 height/ width 가질 수 있음
    
    **단점** : 한 페이지를 채우면 좌우 여백의 크기가 다름
    
    inline이 가지고 있는 미세한 여백을 다루기 까다로움
    

![margin-right 값을 준다고 해도… 과하게 주면 다음줄로 넘어감](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/aa89737d-1955-4f90-af69-146d4d8b8690.png)

margin-right 값을 준다고 해도… 과하게 주면 다음줄로 넘어감

![스크롤에 따라 크기가 달라짐](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled.png)

스크롤에 따라 크기가 달라짐

### float

- 원 사용법 : 이미지와 텍스트 자연스럽게 정리하기 위한 기능
    
    ![2022-09-13 21;17;28.PNG](CSS%205fa503ac80d8450cbf12551077c7cad6/2022-09-13_211728.png)
    
- 구 사용법 : (flex, grid 탄생 전) 이를 이용해서 container 정렬했음
    
    새로운 레이어층을 만들어 왼쪽, 오른쪽 끝으로 정렬시 사용
    
    첫 태그 float → 다음 태그 float → 다음 태그 clear
    
    ⇒ 앞에 두 블럭은 일렬로 정렬되고, 세번째부터 아래로 정렬
    
1. `float: none` : 정렬 x
2. `float: left` : 왼쪽 정렬
3. `float: right` : 오른쪽 정렬
- `clear: left/ right/ both` : float 제어 (끄기)
    
    다음 태그가 float로 정렬된 공간 아래로 들어가게 하려면(float 속성을 끄려면) 다음 태그에  넣어주기
    
- 부모의 크기가 정렬하기 작다면 다음줄로 넘어감

# F**lexbox**

![css-flexbox-poster.png](CSS%205fa503ac80d8450cbf12551077c7cad6/css-flexbox-poster.png)

inline-block의 단점 극복 → 기본 값 유지하면서 창 크기에 가변적

- 한 줄로 배치
- 내용물의 크기만큼 width 차지
    
    ![block](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%201.png)
    
    block
    
    ![flex](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%202.png)
    
    flex
    
- height는 컨테이너의 높이만큼 늘어남
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%203.png)
    
- flex-direction: column을 적용하면 height가 지정됨
    
    ## flex의 width와 height
    
    flex를 설정하면 내용물의 크기에 맞춰 width가 지정됨
    
    - 기본값
        
        ```css
        .main-chat {
          margin-top: 120px;
        }
        
        .chat__timestamp {
          background-color: rgba(0, 0, 0, 0.3);
          color: white;
          padding: 15px;
          border-radius: 25px;
        }
        ```
        
        ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%204.png)
        
    
    - flex 설정 시
        
        ```css
        .main-chat {
          margin-top: 120px;
          display: flex;
        }
        ```
        
        ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%205.png)
        
    
    - flex-direction: column; 적용시
        
        ```css
        .main-chat {
          margin-top: 120px;
          display: flex;
          flex-direction: column;
        }
        ```
        
        ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%206.png)
        
        - 다시 늘어난 이유?
            
            수직, 수평이 뒤바뀌어서 현재 width가 아닌 내용물에 맞게 height가 적용된 상태
            
    - align-items: center; 적용
        
        ```css
        .main-chat {
          margin-top: 120px;
          display: flex;
          flex-direction: column;
        	align-items: center;
        }
        ```
        
        ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%207.png)
        
        다시 줄어들었다
        
        이유는... 나도 모름
        

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%208.png)

---

## container 속성

flex item들의 부모인 container에 지정하는 속성

- `display : flex`

### flex-direction

아이템이 배치되는 축의 방향 결정

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%209.png)

- `row` 왼→오 정렬
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2010.png)
    
- `row-reverse` 오→왼 정렬
    
    (reverse: start 와 end의 순서도 뒤바뀜)
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2011.png)
    
- `column` 위→아래 정렬
    
    (justify-content & align-items 의 축이 뒤바뀜)
    
- `column-reverse` 아래→위 정렬
- 사용 예시 (box의 순서 뒤집기)
    
    파랑 이용해서 빨강 만들기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/f01b1be7-cc2c-4fb2-a59a-b44e26e09219.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/f01b1be7-cc2c-4fb2-a59a-b44e26e09219.png)
    
    1. **modifier 추가**
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/600f371f-45b1-421f-8905-8e6c04f57600.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/600f371f-45b1-421f-8905-8e6c04f57600.png)
        
        파랑 태그를 그대로 복사한 다음, modifier (–own)을 붙여 다른 속성 부여하기
        
    
    **2. 태그의 순서 바꾸기**
    
    - `order: n;`
        
        현재 요소의 배치 순서를 지정 (오름차순으로 정렬)
        
        - flex 자식만 사용 가능
        - 단점: 자식수가 많아지면 써야할 코드 많아짐
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/753ee2ec-dd3b-46a6-9df6-55edf62b30f4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/753ee2ec-dd3b-46a6-9df6-55edf62b30f4.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/27728793-7533-43bb-92a7-4a53078b4907.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/27728793-7533-43bb-92a7-4a53078b4907.png)
        
        ![html은 bubble → time 순서로 작성되어있으나 order을 지정해주자 오름차순으로 정렬됨 (0이 먼저)](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/eb622466-c672-4316-a3b5-b6094308d171.png)
        
        html은 bubble → time 순서로 작성되어있으나 order을 지정해주자 오름차순으로 정렬됨 (0이 먼저)
        
    1. **row-reverse**
        
        `flex-direction: row-reverse;`
        
        이거 한 방이면 순서가 거꾸로 바뀐다
        
        - flex 자식만 사용 가능
        - 단점: 세세하게 순서 지정 불가
        

### flex-wrap

container안의 요소들이 강제로 한줄에 배치 or 여러행으로 나눌 것인지 결정

- `nowrap` (기본값)
    
    화면 크기를 줄여도 요소 크기를 줄여 한 줄에 모두 배치
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2012.png)
    

- `wrap`
    
    화면이 꽉 차면 다음 줄로 넘어감
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2013.png)
    

- `wrap-reverse`
    
    위에서부터 거꾸로 줄세우기
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2014.png)
    

### flex-flow

`flex-flow: direction wrap여부`

flex-direction, flex-wrap을 혼합해서 쓸 수 있음

### justify-content / align-content

중심축/ 교차축에서 아이템을 배치 방식 설정 (각 item 순서는 유지)

1. `center` 가운데 정렬
2. `flex-start`: 왼→오 정렬
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2015.png)
    
3. `flex-end` : 오→왼 정렬
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2016.png)
    
4. `space-around` / `space-evenly` / `space-between`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/fcbf428a-9564-4056-8ce9-c70a0ff44839.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/fcbf428a-9564-4056-8ce9-c70a0ff44839.png)
    

### align-items

반대축에서 아이템 배치 방식 설정 (각 item 순서는 유지)

1. `stretch` (기본값) 아이템들이 수직축 방향으로 쭉 늘어남
2. `center` 가운데 정렬
3. `flex-start` 시작점으로 정렬
4. `flex-end` 끝점으로 정렬
5. `baseline` 텍스트 베이스라인 기준으로 정렬
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2017.png)
    
- 주의사항
    
    body의 height 설정하고 적용해야 함
    
    ⇒ 설정하지 않으면 body가 안의 tag의 값에 맞춰져 있어서 변화 없을 수 있음
    

---

## flex item 속성

### order

`order: n`

아이템의 순서를 숫자로 설정(기본값=0)

### flex-grow

`flex-grow: n`

아이템의 증가 너비 비율 설정

(기본값은 0 ⇒ 화면이 커져도 아이템 크기 변하지 않음)

- ex) item1에만 `flex-grow: 1` 설정 ⇒ 화면 늘리면 1만 늘어남

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2018.png)

### flex-shrink

`flex-shrink: n`

아이템의 감소 너비의 비율의 설정

(기본값은 0 ⇒ 화면이 작아져도 아이템 크기 변하지 않음)

- ex) 1은 `flex-shrink: 2` 설정, 2&3은 `flex-shrink: 1` 설정 ⇒ 화면 줄이면 1이 더 줄어듬
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2019.png)
    

### flex-basis

`flex-basis: ~`

아이템의 기본 너비 설정

- 기본 점유 크기 설정 ⇒ width가 작으면 그만큼 늘어나고, 크면 크기변경 없음

```css
.item {
	flex-basis: auto; /* 기본값 */
	/* flex-basis: 0; */
	/* flex-basis: 50%; */
	/* flex-basis: 300px; */
	/* flex-basis: 10rem; */
	/* flex-basis: content; */
}
```

### align-self

교차 축에서 각 아이템 별로 정렬 방법 설정 (align-items의 아이템 버전)

1. `stretch` (기본값) 아이템들이 수직축 방향으로 쭉 늘어남
2. `center` 가운데 정렬
3. `flex-start` 시작점으로 정렬
4. `flex-end` 끝점으로 정렬
5. `baseline` 텍스트 베이스라인 기준으로 정렬
- ex) 1에만 `align-self: flex-end` 설정
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2020.png)
    

# Grid

2차원(행, 열)의 레이아웃을 배치 가능

(flexbox는 단순한 1차원 레이아웃으로 좀 더 복잡한 레이아웃은 grid 이용)

- Flex vs Grid
    
    ![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2021.png)
    
- grid 요약 그림
    
    ![css-grid-poster.png](CSS%205fa503ac80d8450cbf12551077c7cad6/css-grid-poster.png)
    

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2022.png)

## container 속성

`display: grid`

### grid-template

- `grid-template-row : [이름] size, size, ...`
    
    `grid-template-column : [이름] size, size, ...`
    
    행/열의 크기 정의
    
    - size: fr(fraction, 공간비율), px, % …
    - `repeat()` 사용 가능: `repeat(반복횟수, size)`
- `grid-auto-rows: size`
    
    `grid-auto-columns: size`
    
    행/ 열 개수 상관없이 자동 배치
    
    - minmax(minsize, maxsize) 최소, 최대값을 지정하는 함수
        
        ex) `grid-auto-rows: minmax(100px, auto)` ⇒ 최소 100px 크기지만 컨텐츠가 많아지면 값 자동으로 늘어남
        
    
    ![`grid-auto-rows: 100px`](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2023.png)
    
    `grid-auto-rows: 100px`
    
    ![`grid-auto-rows: minmax(100px, auto)`](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2024.png)
    
    `grid-auto-rows: minmax(100px, auto)`
    

### gap

- `(grid-)gap` 행,열 사이 간격 지정
- `(grid-)row/column-gap` 행or열 사이 간격 지정

셀 사이 간격만 생기기 때문에 전체적으로 균등한 간격 주고 싶다면 padding 이용

![`grid-gap: 10px`](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2025.png)

`grid-gap: 10px`

![`padding: 10px`](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2026.png)

`padding: 10px`

---

## grid item 속성

### grid-row/column-start/end

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2027.png)

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2028.png)

아이템을 배치하기 위해 그리드 선의 시작 위치와 끝 위치를 지정

- 속성값: 숫자 or 선 이름 or span n (startLine부터 n개의 칸 차지)
1. `grid-row-start: n` 시작 행  
    
    `grid-row-end: n` 끝 행
    
2. `grid-column-start: n` 시작 열
    
    `grid-column-end: n` 끝 열
    
- 단축속성
    - `grid-row: startLine / endLine`
    - `grid-column: startLine / endLine`

![`grid-colunm: 2/ -1`  `grid-row: 1 / 3`](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2029.png)

`grid-colunm: 2/ -1`  `grid-row: 1 / 3`

### grid-area

각 영역에 이름을 붙이고, 이를 이용해서 배치하는 방식

![보통 이와 같은 영역이름 사용](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2030.png)

보통 이와 같은 영역이름 사용

- **grid container에 적용 ⇒ 영역 만들기**
    
    각 영역이 차지하는 셀의 개수만큼 해당 위치에 이름 쓰기
    
    - 행이나 셀을 구분하거나, 빈칸은 `none` or `.` 사용
    
    ```css
    .container {
    	grid-template-areas:
    		"header header header"
    		"main . sidebar"
    		"footer footer footer";
    }
    ```
    

- **각 grid item에 적용 ⇒ 이름 매칭**
    
    `grid-area: 지정이름`
    
    ```css
    .header { grid-area: header; }
    .main { grid-area: main; }
    .sidebar { grid-area: sidebar; }
    .footer { grid-area: footer; }
    /* 이름 값에 따옴표가 없는 것에 주의하세요 */
    ```
    

### 이외

- `align-self` : 단일 아이템의 교차축 정렬
- `justify-self` : 단일 아이템의 메인축 정렬
- `order` : 아이템 배치 순서 지정
- `z-index` : 아이템의 레이어 지정

# **position**

## **fixed**

`position: fixed;`

- 스크롤 내려도 지정된 위치 그대로 있음
- fixed 하는 순간, 아예 다른 레이어가 됨 (맨위 레이어)
    
    아래에 태그를 작성하면 밑으로 놓이는게 아니라 아래 깔리는 형태가 됨
    
    (z-index로 레이어 변경 가능)
    

![fixed 된 상태에서 top/ bottom/ left/ right 로 위치 설정하면](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/912d2275-ad8d-4d91-8954-b34c16846e4e.png)

fixed 된 상태에서 top/ bottom/ left/ right 로 위치 설정하면

![아예 위로 올라감. wheat 색깔 네모는 스크롤 내려도 계속 저 자리에 있음](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/c9563345-bb39-4078-a300-b64e90f12e81.png)

아예 위로 올라감. wheat 색깔 네모는 스크롤 내려도 계속 저 자리에 있음

## **static**

`position: static;`

- 레이아웃이 박스를 처음 위치하는 곳에 둠
- top/bottom/left… 사용 불가 (쓰려면 relative)

## **relative**

`position: relative;`

`top/ bottom/ left/ right: 숫자;`

- 자기 자신을 기준으로 위치 적용
- top/ bottom/ left/ right 방향에서 숫자 만큼 떨어짐
    
    (top: 10px; 하면 위로 이동하는게 아니라 아래로 10px만큼 이동)
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/307013c3-4f11-4bd4-b636-eee60e1bebf7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/307013c3-4f11-4bd4-b636-eee60e1bebf7.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d1bb932a-d26b-4844-9725-3d7bab562f94.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d1bb932a-d26b-4844-9725-3d7bab562f94.png)

## **absolute**

`position: absolute;`

`top/ bottom/ left/ right: 숫자;`

- 새로운 레이어를 형성, 제일 위로 떠서 위치 선정
- 아래에 태그를 작성 시, 밑으로 놓이는게 아니라 아래 깔리는 형태가 됨
    
    (z-index 설정해서 레이어 수정 가능)
    
- 적용 시, width/ height이 적용되어 있지 않다면 자식의 사이즈에 맞춰 줄어듬
- 가장 가까운 relative한 부모 기준 (없으면 body 기준)

![green의 부모 = div, div에 relative 설정](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/31702fd7-89e1-45b5-9eb8-55f8c39a27ee.png)

green의 부모 = div, div에 relative 설정

![div 안에서 초록박스 움직임](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/af25b30b-fa11-450c-8c70-138100af1d65.png)

div 안에서 초록박스 움직임

- 스크롤 맨 밑에 놓고 싶다면 꼭 body에 relative 적용할 것
    - body에 relative 설정 시: 찐으로 스크롤 내리면 제일 밑에 있음
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/676112d5-a407-43e4-8cda-6418e6baf738.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/676112d5-a407-43e4-8cda-6418e6baf738.png)
        
    - body에 relative 미설정 시: 펼쳤을 때 보이는 화면 기준으로 이동
        
        ex) bottom: 0px → 스크롤을 내리기 전에는 맨 밑 스크롤을 내리면 밑에 공간 더 있음
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/12f02250-c25f-4a03-aee1-3d275b98c974.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/12f02250-c25f-4a03-aee1-3d275b98c974.png)
        

- **absolute 요소를 부모 정중앙에 놓기**
    - absolte 요소에 top: 50%, letf: 50% 를 선언하면, 요소의 좌상단 꼭지점이 정중앙에 옴
    - transform: translate (-50%, -50%); 하면 요소의 크기를 기준으로 너비와 높이의 50%만큼 좌상으로 이동하니까 정중앙으로 옴
        
        

## **레이어 설정하기**

`z-index: ~;`

- default: 0
- 숫자가 작을수록 밑의 layer, 클수록 위의 layer
- `position: fixed/absolute` 에 이용 가능.

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2031.png)

# **states**

## **active**

`tag:active {…}`

마우스로 누르는 동안 적용

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d03dee8d-3ae1-4eed-8f89-cb998ec7927f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d03dee8d-3ae1-4eed-8f89-cb998ec7927f.png)

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2032.png)

## **hover**

`tag:hover {…}`

마우스를 올리기만 하면 적용

- button 에게 속성을 하나라도 부여하면 지정되어 있던 border 속성을 잃어버림 (완전 이해x)

## **focus**

`tag:focus {…}`

선택이 되면 적용

![input 같은 경우, 입력하려고 하면 속성 적용](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/11203e96-f4a2-4993-913a-9d4da0a1f283.png)

input 같은 경우, 입력하려고 하면 속성 적용

- 클릭했을 때 생기는 테두리 없애기

`tag: focus, tag: active {outline: none; }`

## link / **visited**

- `a:link {…}` : 방문한 적 없는 링크에 적용
- `a:visited {…}` : 방문한 적 있는 링크에 적

## **focus-within**

`tag:focus-within {…}`

tag의 자식이 focused(선택)되면 tag에게 적용

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/f2a433eb-45d3-4c76-8e75-d3a1cca116b3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/f2a433eb-45d3-4c76-8e75-d3a1cca116b3.png)

![선택x](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/95cf7bd2-9021-47ad-bab7-1254acdc6ff3.png)

선택x

![안에 칸 하나 선택되니까 form의 border 변함!](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/79bd2a20-ecf2-464d-8118-02af07659ff1.png)

안에 칸 하나 선택되니까 form의 border 변함!

## **연계 사용**

- `tag1:state tag2 {…}`
    
    tag1이 state 일 때 → tag2에 …적용
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e42f4673-467d-4643-a5c4-05549b464ea8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e42f4673-467d-4643-a5c4-05549b464ea8.png)

![ form에 hover하면, input의 background-color적용](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ac66302b-ee77-41ee-a3c7-08a4bff29dc0.png)

 form에 hover하면, input의 background-color적용

- `tag1:state tag2:state {…}`
    
    두 조건이 모두 맞을때 … 실행
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/64c73c21-3be7-4352-bbb9-c6945aee2f4b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/64c73c21-3be7-4352-bbb9-c6945aee2f4b.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e42726e3-810a-4be8-83f8-d0126f9c89cd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e42726e3-810a-4be8-83f8-d0126f9c89cd.png)

![form 위에 마우스 올라가있고, input 선택되니까 실행](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/8b6ba9d5-a20a-4739-b065-edd7501a57a4.png)

form 위에 마우스 올라가있고, input 선택되니까 실행

# 주요 속성

## 글자 속성

- `font-family: 폰트명, 폰트명…` : 폰트 선택
    - 입력한 순서대로 우선순위 적용
    - 브라우저마다 지원 폰트 다르므로 여러 개 작성하기
        
        맨 마지막은 `sans-serif` ⇒ 모든 브라우저에서 지원하므로 디폴트값임
        
- `font-weight` : 글씨 두께 (100~900 사이의 수/ bold)
- `font-size`
- `font-style` : `italic` (기울이기) … 등등
- `text-align` : 글씨 x축 정렬
- `line-height: n`  : 줄높이 설정 (한줄일 경우 y축 높이 조절 가능)
- `text-transform: uppercase;` : 대문자 변환 (html에서 소문자로 작성됐을 시)
- `text-decoration: none;` 기본 글자 설정 없애기 (ex) 링크의 밑줄)
- **사이트 [google fonts](https://fonts.google.com) 사용**
    1.  - html
    2. @import - css
        
        ① @import 복사해서 css 맨 상단에 복사
        
        ② font-family 복붙
        

## **크기 조정**

`width/ height: ~;`

- px : 고정값 / % : 가변값 (부모의 크기 지정되어야 가능)
- 부모크기 기준으로 퍼센트 결정
- width/ height 하나만 써도, 비율에 맞춰 크기 조정 됨
- vh= viewpoint height (screen 화면을 꽉 채우는 높이)
    
    vw= viewpoint width (100vw썼는데 스크롤바 생겼다면 기본 margin, padding이 설정되어있을 가능성 있음)
    

## backgrond

- `background-color : color`
- `background-image : url(이미지 경로)`
    - `<img>` vs `background-image`
        - 디자인적으로 꾸밀 수 있는건 ⇒ background-image
        - 콘텐츠, 정보 전달 ⇒ img (alt를 표기함으로써 웹접근성에 좋고, 성능 측면에서 효율적)
- `background-repeat: ~`
    - `no-repeat` 반복 x
    - `repeat-x` x축으로 반복
    - `repeat-y` y축으로 반복
- `background-position : top/ bottom/ center/ left/ right`
    
    공간 안에서 이미지의 좌표를 변경
    
- `background: color url(이미지 경로) no-repeat left;`
    
    이렇게 한 줄에 함께 쓸 수도 있음
    

## **색상 설정**

- #000000
- **rgb (red green blue) →** rgb(000, 000, 000)
- rgba(000, 000, 000, 0)
    - a는 알파 → 투명도
    - 맨 끝 : 0 = 투명/ 1= 불투명

## 이외

- `box-shadow: inset;` 박스 안쪽에 그림자 효과
- `overflow-축: hidden / scroll`
    
    크기를 넘어서는 부분을 숨길지/ 스크롤 가능하게 할지
    
- `cursor : 속성값` 마우스 포인터 모양 변경
    - pointer (손가락)
    - not-allowed (선택 안됨)
    - progress (로딩중)
- `object-fit: cover;` 사진 사이즈 비율 유지
- `list-style: none`  ol, ul의 순서표시 삭제

## **form의 attributes**

- `form: action="…"` 어떤 페이지로 data 보낼건지 지정
    - ex) `form: action="friends.html"`
        
        input 실행시, friends 라는 html 파일이 이어서 실행
        
- `form: method="…"`
    - `form: method="post"` 백엔드 서버에 정보 전송
    - `form: method="get"` 서버 없어도 됨
        
        (보안에 취약 url에 포함되어도 상관없는 정보들만)
        
        - 하위 input 에 name 설정할 것
        
        ![html 작성/ 위 username, 아래 password](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2033.png)
        
        html 작성/ 위 username, 아래 password
        
        ![input에 입력해서 login 클릭하면](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2034.png)
        
        input에 입력해서 login 클릭하면
        
        ![url에 이렇게 표시된다](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2035.png)
        
        url에 이렇게 표시된다
        
    

---

## **변수 만들기**

설정값을 변수로 만들어놓아 효율적

- 생성 `:root {a:b}`
- 사용 `var(a)` ⇒ b
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1370d85e-35dd-4205-a846-6d2d46769dec.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1370d85e-35dd-4205-a846-6d2d46769dec.png)
    

# **아이콘**

(svg: 픽셀 없는 이미지, 좌표로 되어있어서 무한으로 늘릴 수 있음)

- 이용 사이트: [heroicons](https://heroicons.com/) / [fontawesome](https://fontawesome.com/v5.15/icons?d=gallery&p=2)

### **적용 방법**

1. code kit를 body 맨 아래 넣음
    
    ```jsx
    <script
          src="https://kit.fontawesome.com/6478f529f2.js"
          crossorigin="anonymous"
        ></script>
    ```
    
2. html 에 복붙
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e73f63bb-2833-416c-b31a-053ae8744863.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e73f63bb-2833-416c-b31a-053ae8744863.png)
    

### **아이콘 사이즈 변경**

1. **html** : 태그에 `fa-size` 추가 
    
    `<i class="~fa-lg"> </i>`
    
    - size: g, 2x, 3x, xs …
2. **css :** 글자와 같이 크기 수정
    
    `i {font-size: 속성값}`
    

### **아이콘 움직이기**

i는 텍스트와 같기 때문에 움직이려면 span이나 다른 블럭으로 감싸줘야함

### 아이콘에 링크 넣기

`<a href="파일명/링크”><i class=”아이콘”></i></a>`

a태그로 아이콘 감싸주기

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2036.png)

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2037.png)

![Untitled](CSS%205fa503ac80d8450cbf12551077c7cad6/Untitled%2038.png)