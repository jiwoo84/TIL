# CSS

---

# 기본 설정

1. **html 파일 안에 css 코드 같이 쓰기 (inline CSS)**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/bc7561ac-50c0-437b-b6f7-663c436b6754.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/bc7561ac-50c0-437b-b6f7-663c436b6754.png)
    

1. **css 파일 따로 만들고, 링크 연결 (external CSS)**
    
    `<link href="href="폴더/style.css" rel="stylesheet" />` 
    
    (단축 코드: `link:css`)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0ad63608-3cb5-4c3e-a169-a80810047703.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0ad63608-3cb5-4c3e-a169-a80810047703.png)
    

## **기본 설정 사항 없애기** (margin 등)

- reset.css 파일 만들기
    
    ① 파일 (reset.css) 새로 만듬
    
    ② 코드 복붙 ([사이트](https://meyerweb.com/eric/tools/css/reset/))
    
    ③ css 파일에 `@import "reset.css"` 추가
    
    +css파일에 추가하는게 좋음
    
    [https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/58d42e7d-d476-4e28-81af-ad9c9c7cb9a1.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/58d42e7d-d476-4e28-81af-ad9c9c7cb9a1.webm)
    

# **css 기본 문법**

`tag { 속성: 속성값 }`

- 지정 태그 안에 있는 내용 모두 선택됨
- 위에서부터 실행 → 결국 적용되는건 마지막 코드
- 적용 우선순위 : id > class > 태그

### id

`#id {속성: 속성값}`

- ID 여러개 지칭하는 법 : `#id, #id, #id ... {속성:속성값;}`
- 전체 선택 : `* {속성: 속성값}`

### **class**

`.class {속성:속성값;}`

- class 안의 class 선택하기 : `.class1 .class2 {~;}`

### **BEM(Block Element Modifier)**

class 만드는 효율적 방법 ([설명](https://nykim.work/15))

`block--(modifier)__element`

---

### 글자 속성

`color`

`font-weight`(글씨 두께)

`font-size` 

`font-style`

`text-align`(글씨 정렬)

`text-transform: uppercase;` : 대문자 변환 (html에서 소문자로 작성됐을 시)

`text-decoration: none;` 기본 글자 설정 없애기 (ex) 링크의 밑줄)

### **크기 조정**

`width/ height: n%`

- px이나 다른 크기조정과 달리 %는 부모의 크기가 지정되야 가능
- 부모크기 기준으로 퍼센트 결정
- width/ height 하나만 써도, 비율에 맞춰 크기 조정 됨
- vh= viewpoint height (screen 화면을 꽉 채우는 높이)
- vw= viewpoint width

### **색상 설정**

- #000000
- **rgb (red green blue) →** rgb(000, 000, 000)
- rgba(000, 000, 000, 0)
    - a는 알파 → 투명도
    - 맨 끝 : 0 = 투명/ 1= 불투명

## **inherit**

`속성: inherit;`

tag의 부모로부터 값 상속

### **그림자 효과**

`box-shadow: inset;`

박스 안쪽에 그림자 효과

### 오버플로우

`overflow-축: hidden / scroll`

크기를 넘어서는 부분을 숨길지/ 스크롤 가능하게 할지

### **마우스 포인터 모양 변경**

`cursor : 속성값`

- pointer (손가락)
- not-allowed (선택 안됨)
- progress (로딩중)

### **사진 사이즈 비율 유지**

`object-fit: cover;`

---

## **form의 attributes**

- `form: action="…"` 어떤 페이지로 data 보낼건지 지정
    - ex) `form: action="friends.html"`
        
        input 실행시, friends 라는 html 파일이 이어서 실행
        
- `form: method="…"`
    - `form: method="post"` 백엔드 서버에 정보 전송
    - `form: method="get"` 서버 없어도 됨
        
        (보안에 취약 url에 포함되어도 상관없는 정보들만)
        
        - 하위 input 에 name 설정할 것
        
        ![html 작성/ 위 username, 아래 password](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled.png)
        
        html 작성/ 위 username, 아래 password
        
        ![input에 입력해서 login 클릭하면](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%201.png)
        
        input에 입력해서 login 클릭하면
        
        ![url에 이렇게 표시된다](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%202.png)
        
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

# **폰트 설정**

- **기본 폰트 쓰기**
    
    `font-family:` 쓰고 목록중에 고르기
    
- **사이트 [google fonts](https://fonts.google.com) 사용**
    1.  - html
    2. @import - css
        
        ① @import 복사해서 css 맨 상단에 복사
        
        ② font-family 복붙
        

# BOX

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/b754122e-ab70-47ee-8c6b-8d23a372e2a8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/b754122e-ab70-47ee-8c6b-8d23a372e2a8.png)

## margin

- 기본으로 body는 margin 값 가짐 (없애기 → `margin: 0;`)
- 값 설정
    
    `margin-top/ left/ right/ botom;`
    
    `margin: 숫자;` 사방에 다 적용
    
    `margin: 상 우 하 좌` (시계방향)
    
    `margin: 상하 좌우`
    
- **`margin: 0 auto;`**
    - 가로 정중앙 만들 수 있는 코드
    - space-between은 글자수에 따라 중앙 아닐 수 있음 → auto를 적절히 잘 사용하면 가능

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/82221621-50f9-4316-af34-9b0db6b918d0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/82221621-50f9-4316-af34-9b0db6b918d0.png)

- collapsing margins
    
    경계가 닿으면 박스의 margin이 같아지는 현상
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/bb377897-db22-46b7-973b-307e0161bf5c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/bb377897-db22-46b7-973b-307e0161bf5c.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/71735d27-e3c5-42f9-a44a-53e6f131eb27.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/71735d27-e3c5-42f9-a44a-53e6f131eb27.png)
    
    - ex) 1. 더 큰 값인 body의 margin이 따로 설정x
        1. div의 margin 설정 
        2. (div만 body 안에서 쏘옥 들어감x) div와 body 같이 움직여서 margin 설정됨
    - 이는 상하만 해당됨
        
        (깊게 이해하려 노력x, 하다보면 이해됨)
        

---

## **border**

`border: 두께 ·스타일·색상`

- 스타일 변경 `border-style: 속성값`
- 둥글게 만들기 `border-radius : ~;`
    - 원 모양 `border-radius: 50%`
    - 특정 모서리만 수정 `border- (top or bottom) - (left or right) - radius : ~;`
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/bcb5f19b-72ac-43f7-88b3-d7242c174069.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/bcb5f19b-72ac-43f7-88b3-d7242c174069.png)
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ae5166a0-fefb-474a-b087-46a7fccc8591.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ae5166a0-fefb-474a-b087-46a7fccc8591.png)
        

- **border vs outline**
    - border : 상자 바깥으로 확장하면서 테두리 적용
    - outline : 상자 안쪽으로 테두리 생김
    
    ∴ border은 박스 크기가 커짐/ outline은 변화 없음
    

### **빈 공간이 margin vs padding 헷갈릴 때**

bottom을 경계로 안쪽은 padding/ 바깥은 margin

## **`box-sizing: border-box`**

box사이즈 유지하면서 border만들기

- 미사용: width,height 지정 상태에서 border 지정 → 크기 유지 위해 박스가 커짐
    
    ex) width: 50px / border: 30px ⇒ 크기 80px이 됨
    
- 사용: box사이즈 신경쓰지 않고 border 만들어짐
    
    ex) width: 50px / border: 30px ⇒ 결과적으로 50px으로 보임
    

# display 종류

 `display: ~;`

### **block**

옆에 아무도 못 옴 

- ex) `<div>` `<header>` `<address>` `<p>` 등 대다수

### **inline**

옆에 올 수 있음

- ex)  `<span>` `<a>` `<img>` `<code>` 등 일부 (이거 외우는게 편함)
- height, width 가질 수 없음
- box 지정
    - padding : 사방에 작용
    - margin : 좌우만 작용(사방에 만들고 싶다면 block)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/56674b08-18f0-4c55-b27a-0370d73916ce.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/56674b08-18f0-4c55-b27a-0370d73916ce.png)
    
    ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%203.png)
    

### **inline-block**

inline&block의 특성 동시 적용

- **장점** : inline 처럼 한 줄이지만 height/ width 가질 수 있음
- **단점** : 한 페이지를 채우면 좌우 여백의 크기가 다름

![margin-right 값을 준다고 해도… 과하게 주면 다음줄로 넘어감](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/aa89737d-1955-4f90-af69-146d4d8b8690.png)

margin-right 값을 준다고 해도… 과하게 주면 다음줄로 넘어감

![스크롤에 따라 크기가 달라짐](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%204.png)

스크롤에 따라 크기가 달라짐

---

# **flexbox**

`display : flex;` 

inline-block의 단점 극복 → 기본 값 유지하면서 창 크기에 가변적

- 가로 방향으로 배치되고, 자신이 가진 내용물의 width 만큼만 차지함. 마치 inline
    
    ![block](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%205.png)
    
    block
    
    ![flex](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%206.png)
    
    flex
    
- height는 컨테이너의 높이만큼 늘어납니다.
    
    ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%207.png)
    
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
        
        ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%208.png)
        
    
    - flex 설정 시
        
        ```css
        .main-chat {
          margin-top: 120px;
          display: flex;
        }
        ```
        
        ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%209.png)
        
    
    - flex-direction: column; 적용시
        
        ```css
        .main-chat {
          margin-top: 120px;
          display: flex;
          flex-direction: column;
        }
        ```
        
        ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2010.png)
        
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
        
        ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2011.png)
        
        다시 줄어들었다
        
        이유는... 나도 모름
        

### 기본축 설정

컨테이너는 주축과 교차축을 가지고 있음

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/f6004b3d-8218-43cb-a670-7ee58ea039d5.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/f6004b3d-8218-43cb-a670-7ee58ea039d5.png)

![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2012.png)

- **X축 정렬** (기본값)
    
    `justify-content: ~;`
    
- **y축 정렬**
    
    `align-items: ~;`
    
    body의 height 설정하고 적용해야 함 (height: 100vh)
    
    - 설정하지 않으면 body가 안의 tag의 값에 맞춰져 있어서 변화 없을 수 있음

- **속성값**
    - `center`
    - `flex-end` : 끝 정렬
    - `flex-start`: 기본값
    - `space-evenly`: 빈 공간 같은 크기로 나누어 배치
    - `space-around` / `space-between` …
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/fcbf428a-9564-4056-8ce9-c70a0ff44839.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/fcbf428a-9564-4056-8ce9-c70a0ff44839.png)
    

### 방향 **변경**

`flex-direction: …;`

 

- `flex-direction: row` 그대로
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/ebb9325f-5f9b-48db-b602-e846ec911561.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/ebb9325f-5f9b-48db-b602-e846ec911561.png)
    

- `flex-direction: row-reverse` 텍스트 반대방향 정렬
    
    (reverse: start 와 end의 순서도 뒤바뀜)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/dd0d9c2e-311a-4bb0-ae20-5b67dbd90436.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/dd0d9c2e-311a-4bb0-ae20-5b67dbd90436.png)
    

- `flex-direction:column` 위에서 아래로 정렬
    
    (justify-content & align-items 의 축이 뒤바뀜)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/0b585f2b-18a6-4b68-a6ab-8575d8442ed5.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/0b585f2b-18a6-4b68-a6ab-8575d8442ed5.png)
    

- `flex-direction:column-reverse` 아래서 위로 정렬
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/5e586fc6-3faa-485f-9f7d-0ed593fc1cf1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/5e586fc6-3faa-485f-9f7d-0ed593fc1cf1.png)
    
    [개구리게임 해보기](https://flexboxfroggy.com/#ko)
    

- **좋은 사용 예시 (box의 순서 뒤집기)**
    
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
        
    - **row-reverse**
        
        `flex-direction: row-reverse;`
        
        이거 한 방이면 순서가 거꾸로 바뀐다
        
        - flex 자식만 사용 가능
        - 단점: 세세하게 순서 지정 불가
        

### flex-wrap

flex 안의 요소들이 강제로 한줄에 배치 or 여러행으로 나누어 표현 할 것인지 결정하는 속성

- flex-wrap: nowrap;
    
    ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2013.png)
    
- flex-wrap: wrap;
    
    ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2014.png)
    
- flex-wrap: wrap-reverse;
    
    ![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2015.png)
    

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

![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2016.png)

# **pseudo selector**

여러 tag에 하나하나 id나 class 지정하기보다, 효율적으로 순서를 매겨서 지시하는 방법

형제 사이에서의 순서에 따라 요소를 선택

## **nth-child**

`first-child {…}` tag 중 가장 첫번째에 적용

`last-child {…}` tag 중 가장 마지막에 적용

`nth-child(숫자)` 지정한 순서에 적용

`nth-child(even)` 짝수에 적용

`nth-child(odd)` 홀수에 적용

`nth-child(숫자n+숫자 )` ↴

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ee0e527e-2e0c-4d9b-a995-816062e9472a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ee0e527e-2e0c-4d9b-a995-816062e9472a.png)

![첫번째 적용 후, 3번째마다 적용됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/783d50bf-ec9b-4538-8f4a-aec243377282.png)

첫번째 적용 후, 3번째마다 적용됨

## **nth-of-type(n)**

- 동일한 타입들 안에서 순서를 따짐
- `span: nth-of-type(2)` : 2번째 span 에 적용
- `first-of-type` / `last-of-type` : 첫번째, 마지막
- even, odd, 2n+1 … 을 넣어서 활용 가능

### 주의사항

- 타입은 신경X, 오직 순서만 신경
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7d02766a-91e9-4931-ab0b-7ad0e59fdddd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7d02766a-91e9-4931-ab0b-7ad0e59fdddd.png)
    

- `tag : first-child` 하면 tag 안에 박스의 first-child도 선택됨
    
    ```html
    <div class="main-actions">
      <i class="fas fa-redo"></i> 
      <i class="fas fa-step-backward fa-lg"></i>
      <span>
       <i class="fas fa-play fa-lg"></i>
    	</span>
      <i class="fas fa-step-forward fa-lg"></i>
      <i class="fas fa-random"></i>
    </div>
    ```
    
    ```css
    .main-actions i:first-child, 
    .main-actions i:last-child {
      color: rgba(0, 0, 0, 0.2);
    }
    ```
    
    여기서 이렇게 하면 맨 위, 맨 아래 아이콘만 선택되는 것이 아니라 <span>안에 <i>도 선택
    

# **combinator**

## **tag 지정**

- `부모 자식 {…}`
    
    모든 부모tag 안 자식tag에 적용
    
    ![div안의 p 안의 span 만 색깔 변경](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/5b1e2d43-9588-4aa2-a1fc-1c58caca4112.png)
    
    div안의 p 안의 span 만 색깔 변경
    
- `부모 > 자식 {…}`
    
    부모 바로 아래 자식에만 지시
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/32458170-3efc-4a31-bf45-cc1b4a9d7317.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/32458170-3efc-4a31-bf45-cc1b4a9d7317.png)
    

- `자식 + 자식 {…}`
    
    바로 밑에 있는 자매 tag에 지시 (부모자식 x, 자식 관계ㅇ)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/07cf95be-8906-4dc4-a6e8-7a470e3bdfbe.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/07cf95be-8906-4dc4-a6e8-7a470e3bdfbe.png)
    
- `자식~자식 {…}`
    
    뒤에 오는 자매 모두에게 지시 (바로 뒤x)
    

## 특정 속성

- 특정 속성만 적용

`#id(.class) tag[속성="속성값"] {~}`

- 특정 속성만 적용 안하는 요청
    
    `#id(.class) tag:not ([속성="속성값"]) {~}`
    
    tag 에서 [속성=“속성값”] 만 빼고 적용
    

## **attribute 지정**

- `tag:attribute {…}`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/6c4d2c27-de3f-4c04-a104-1c0fe5fd06df.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/6c4d2c27-de3f-4c04-a104-1c0fe5fd06df.png)
    
    ![input 중 required 만 지시](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/b27acf35-d66c-4950-b874-ba42f15aca58.png)
    
    input 중 required 만 지시
    
- `tag [attribute="name"] {…}`
    
    name까지 지정
    
- `tag [attribute~="name"] {…}`
    
    attiribute에 name 을 포함하고 있다면 모두 선택
    
    - `~=` : name을 포함한다면 해당 (앞or뒤 공백 있어야 함)
    - `=` : name을 포함한다면 해당 (앞뒤 공백 상관없음)
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/625a0152-30c8-42de-9743-b7e26963306f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/625a0152-30c8-42de-9743-b7e26963306f.png)

- `a[href$= ".org"] {…}`
    
    .org 포함된 링크 달렸다면 모두 선택
    

# **states**

## **active**

`tag:active {…}`

마우스로 누르는 동안 적용

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d03dee8d-3ae1-4eed-8f89-cb998ec7927f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d03dee8d-3ae1-4eed-8f89-cb998ec7927f.png)

![Untitled](CSS%2003974fa3a62a42409367485416fc3d2d/Untitled%2017.png)

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

## **visited**

`a:visited {…}`

링크에만 적용, 눌러서 방문 후에 적용

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/92209acc-b4c6-4c42-9386-7df1b257f558.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/92209acc-b4c6-4c42-9386-7df1b257f558.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1e9d836d-009f-45ec-bc27-84b6f73bd739.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1e9d836d-009f-45ec-bc27-84b6f73bd739.png)

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

# **pseudo element**

## **::placeholder**

`tag::placeholder {…}`

tag 중 placeholder에만 적용

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7a8663fa-5465-4989-a537-17df6441eb21.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7a8663fa-5465-4989-a537-17df6441eb21.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/46190da2-daf2-45e2-9137-6e7f3a796ec7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/46190da2-daf2-45e2-9137-6e7f3a796ec7.png)

![placeholder의 색만 변함. input 하면 색상 그대로.](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/22919db5-74e0-4324-b3f2-c424c83f31f4.png)

placeholder의 색만 변함. input 하면 색상 그대로.

## **::selection**

`tag::selection {…}`

드래그 된 부분만 적용 (padding 은 적용 안됨)

## ::**first-letter**

`tag::first-letter {…}`

첫번째 글자만 적용

- `first-line` : 첫번째 줄에 적용