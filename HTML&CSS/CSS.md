# CSS

---

# css 적용하는 방법

1. **html 파일 안에 css 코드 같이 쓰기 (inline CSS)**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/bc7561ac-50c0-437b-b6f7-663c436b6754.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/bc7561ac-50c0-437b-b6f7-663c436b6754.png)
    

1. **css 파일 따로 만들고, 링크 연결 (external CSS)**
    
    `<link href="href="폴더/style.css" rel="stylesheet" />` 
    
    (폴더 없다면 단축 코드: `link:css`)
    
    - 코드 같이 쓰는 것보다 이거 주로 사용 (css파일을 여러 파일에 적용가능해서)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/4e25db28-35ca-4992-a898-63b4ca505743.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/4e25db28-35ca-4992-a898-63b4ca505743.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0ad63608-3cb5-4c3e-a169-a80810047703.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0ad63608-3cb5-4c3e-a169-a80810047703.png)
    

# **css 기본 문법**

**`<style>`**

**`지정 태그 {속성: 속성값}`**

**`</style>`**

- 안에 태그 쓸 것/ 띄어쓰기 X / 끝에 ; 붙이기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/cd0a4eed-f38e-49a4-aa9c-4e9b64b25de1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/cd0a4eed-f38e-49a4-aa9c-4e9b64b25de1.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/b44b0ac8-de72-4ea0-8887-82397cdb4f85.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/b44b0ac8-de72-4ea0-8887-82397cdb4f85.png)
    

- 속성 : `color`/ `font-weight`(글씨 두께)/ `font-size` / `font-style`/ `text-align`(글씨 정렬) 등…
- 지정 태그 안에 있는 내용 모두 선택됨
- 위에서부터 실행 → 결국 적용되는건 마지막 코드
- 폰트에 그라데이션 넣기
    
    ```css
    element {background: linear-gradient(to right top, 왼·하 색상, 오·상 색상); color: transparent;-webkit-background-clip: text; }
    ```
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/5c3a46fb-c578-4191-b81d-bc82b6d68ebe.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/5c3a46fb-c578-4191-b81d-bc82b6d68ebe.png)
    
- **대문자 변환 (html에는 소문자로 작성됐을 시)**
    
    `text-transform: uppercase;`
    
- **크기 조정**
    
    `width/ height: n%`
    
    - px이나 다른 크기조정과 달리 %는 부모의 크기가 지정되야 가능
    - 부모크기 기준으로 퍼센트 결정
    - width/ height 하나만 써도, 비율에 맞춰 크기 조정 됨
    
- 적용 우선순위
    
    id > class > 태그
    

# **아이콘**

(svg: 픽셀 없는 이미지, 좌표로 되어있어서 무한으로 늘릴 수 있음)

- **이용 사이트**
    - heroicons :무료 사이트
    - fontawesome: 무료,유료
    
- **적용 방법**
    1. code kit를 body 맨 아래 넣을 것
        
        ```jsx
        <script
              src="https://kit.fontawesome.com/6478f529f2.js"
              crossorigin="anonymous"
            ></script>
        ```
        
    2. html 에  *복붙*
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e73f63bb-2833-416c-b31a-053ae8744863.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e73f63bb-2833-416c-b31a-053ae8744863.png)
        

- **아이콘 사이즈 변경**
    1. html : fa-~ 붙여주기
        
        `<i class="~fa-lg"> </i>`
        
        - lg/ 2x/ 3x/ xs … : 아이콘 사이즈 바꿔주는 class
    2. css
        
        `i {font-size: 속성값}`
        
        아이콘은 텍스트와 같다
        
- **아이콘 움직이기**

i는 텍스트와 같기 때문에 움직이려면 span이나 다른 블럭으로 감싸줘야함

# **폰트 설정**

`font-family: …;`

- **기본 폰트 쓰기**
    
    `font-family:` 쓰고 목록중에 고르기
    
- **사이트 google fonts 사용**
    1.  - html
    2. @import - css
        
        ① @import 복사해서 css 맨 상단에 복사
        
        ② font-family 복붙
        

# block / inline

- **block** : 옆에 아무도 못 옴 (대부분)

`<div>` `<header>` `<address>` `<p>`

- **inline**: 옆에 올 수 있음 (이거 외우는게 편함)

`<span>` `<a>` `<img>` `<code>`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/da28c9d5-e496-4787-adcb-03e2ac50a5b3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/da28c9d5-e496-4787-adcb-03e2ac50a5b3.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ef54b228-42c5-44e8-bd03-9827f30fb713.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ef54b228-42c5-44e8-bd03-9827f30fb713.png)

- **block / inline 속성 변경**
    
    `tag {display: block / inline}`
    
    - inline 은 height, width 가질 수 없음
    - 크기 지정하고 싶다면 주로 `display: block / inline-block;` 사용
        
        ![div가 block 일 때 (default)](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/40dc31db-3042-4f79-91b3-8669bc09343d.png)
        
        div가 block 일 때 (default)
        
        ![하지만 inline으로 지정하는 순간](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e0a68265-76f6-4a8f-bb11-21c274baac9c.png)
        
        하지만 inline으로 지정하는 순간
        
        ![div 값이 없기 때문에 실행x, 아예 없어짐](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/6415d92a-8ffc-454a-8c49-36f2380f6346.png)
        
        div 값이 없기 때문에 실행x, 아예 없어짐
        
        ![내용 넣으면](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/2478ee22-033f-4881-b65c-62197476b6e7.png)
        
        내용 넣으면
        
        ![height과 width가 그 글자의 크기가 됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/7430f319-abf3-42d9-bab5-ab8f50947bea.png)
        
        height과 width가 그 글자의 크기가 됨
        

# BOX

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/b754122e-ab70-47ee-8c6b-8d23a372e2a8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/b754122e-ab70-47ee-8c6b-8d23a372e2a8.png)

## margin

- body 자동으로 margin 값 가짐
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/29780984-f745-4a13-a685-05283f6a5c66.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/29780984-f745-4a13-a685-05283f6a5c66.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e0332bd9-43c6-4788-bf6b-acb3c4f32f6b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e0332bd9-43c6-4788-bf6b-acb3c4f32f6b.png)
    

- margin 없애기
    
    `margin: 0;`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/a794cf14-549c-4409-83a6-4735834e756b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/a794cf14-549c-4409-83a6-4735834e756b.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0b64a8b2-8fe0-428c-918f-de8282df0aa6.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0b64a8b2-8fe0-428c-918f-de8282df0aa6.png)
    

- margin 값 설정
    
    `margin-top/ left/ right/ botom;`
    
    `margin: 숫자;` 사방에 다 적용
    
    `margin: 상 우 하 좌` (시계방향)
    
    `margin: 상하 좌우`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d55bb946-44e9-4fda-946d-9507c012f775.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d55bb946-44e9-4fda-946d-9507c012f775.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/f5850e52-f29f-42fc-85d1-1784cd761de1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/f5850e52-f29f-42fc-85d1-1784cd761de1.png)
    

- collapsing margins
    
    경계가 닿으면 박스의 margin이 같아짐
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/bb377897-db22-46b7-973b-307e0161bf5c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/bb377897-db22-46b7-973b-307e0161bf5c.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/71735d27-e3c5-42f9-a44a-53e6f131eb27.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/71735d27-e3c5-42f9-a44a-53e6f131eb27.png)
    
    더 큰 값인 body의 margin이 따로 설정x 일 때→ div의 margin 설정 
    
    → div만 dody 안에서 쏘옥 들어감x → div와 body 같이 움직여서 margin 설정됨
    
    - 이는 상하 만 해당!
    - 깊게 이해하려 노력x, 하다보면 이해됨
    

## **padding** : **경계 안쪽**

- 문법은 margin과 같다
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/9debb15e-bdef-44cb-801c-ad5b87cc5eb4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/9debb15e-bdef-44cb-801c-ad5b87cc5eb4.png)
    
    ![안쪽으로 공간 생김](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/9556e5b5-2cb6-44d9-b16a-36634ee7554a.png)
    
    안쪽으로 공간 생김
    

## **border**

box의 경계 (block, inline 둘 다 가능)

`border: 두께 ·스타일·색상`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/6d787321-9aa9-4537-847f-65f3d014cc23.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/6d787321-9aa9-4537-847f-65f3d014cc23.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/21b711da-17b9-4f2b-9cbe-17b3f265902a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/21b711da-17b9-4f2b-9cbe-17b3f265902a.png)

- 스타일 변경
    
    `border-style: 속성값`
    

- 둥글게 만들기
    
    `border-radius : □단위`
    
    - `border-radius: 50%` 원 모양
    
- **border 한쪽 모서리만 수정**
    
    `border- (top or bottom) - (left or right) - radius : ~;`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/bcb5f19b-72ac-43f7-88b3-d7242c174069.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/bcb5f19b-72ac-43f7-88b3-d7242c174069.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ae5166a0-fefb-474a-b087-46a7fccc8591.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ae5166a0-fefb-474a-b087-46a7fccc8591.png)
    

- **border vs outline**
    - border : 상자 바깥으로 확장하면서 테두리 적용
    - outline : 상자 안쪽으로 테두리 생김
    
    ∴ border은 박스 크기가 커짐/ outline은 변화 없음
    

## **빈 공간이 margin vs padding 헷갈릴 때**

bottom을 경계로 안쪽은 padding!

바깥은 margin!

# inline 속 경계 적용

- padding : 사방에 작용
- margin : 좌우만 작용

∴ margin을 사방에 만들고 싶다면 block 으로 바꿔야 함

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/56674b08-18f0-4c55-b27a-0370d73916ce.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/56674b08-18f0-4c55-b27a-0370d73916ce.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/f883539c-f11a-44e1-8468-fe58f904bcdd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/f883539c-f11a-44e1-8468-fe58f904bcdd.png)

# css에서의 id 지칭

- `#id {속성: 속성값}`

![이렇게 body에서 한 tag가 다양한 id를 가진 상황이라면](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/3e072cf5-2acb-4033-b8e3-aa1177c30d14.png)

이렇게 body에서 한 tag가 다양한 id를 가진 상황이라면

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/b17256fa-39aa-42b9-8f57-d375fda0a532.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/b17256fa-39aa-42b9-8f57-d375fda0a532.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/475fd127-a820-4ef6-938b-0db1d2da78dc.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/475fd127-a820-4ef6-938b-0db1d2da78dc.png)

- **ID 여러개 지칭하는 법**
    
    `#id, #id, #id ... {□:□;}`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ecd6e9b5-761a-4e4b-ab7e-5e043c601bd1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ecd6e9b5-761a-4e4b-ab7e-5e043c601bd1.png)
    

- **전체 선택**
    
    `* {속성: 속성값}`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/a91fbb38-83e4-40d9-aed5-a8d950d58ea4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/a91fbb38-83e4-40d9-aed5-a8d950d58ea4.png)
    

# **class** (id보다 효율적)

- **BEM(Block Element Modifier)**
    
    class 만드는 효율적 방법 ([설명](https://nykim.work/15))
    
    `block--(modifier)__element`
    

- css에서 class 지칭 방법
    
    `.class {속성:속성값;}`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/172a20a0-8892-4a27-b8af-5853a6137cdd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/172a20a0-8892-4a27-b8af-5853a6137cdd.png)
    

- **class 안의 class 선택하기**
    
    `.class1 .class2 {~;}`
    
    class1 안에 속한 class2에만 적용
    
- id와는 달리 중복 사용 가능

- 한 요소가 여러 class 가질 수 있음
    
    ![한 span의 class 값: tomato / hello / honey / potato 총 4개!](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/0acf8cb4-5f41-4af0-ab4c-d0705a678e16.png)
    
    한 span의 class 값: tomato / hello / honey / potato 총 4개!
    
    ex) 사용 예시
    
    ![한꺼번에 적용하고 싶은 특성이 있다면 클래스 하나를 공통으로 넣어줘 (위 btn)](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/95dc5eba-8256-42a5-9d5f-fd0ba32df59d.png)
    
    한꺼번에 적용하고 싶은 특성이 있다면 클래스 하나를 공통으로 넣어줘 (위 btn)
    
    ![그 다음에 .btn {속성: 속성값;} 으로 특성을 넣어주면](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/94f803fd-d0a7-4adf-bca3-4d88d738bb1c.png)
    
    그 다음에 .btn {속성: 속성값;} 으로 특성을 넣어주면
    
    ![효율적으로 바꿀 수 있다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e257786a-5555-4891-825f-512badeced7e.png)
    
    효율적으로 바꿀 수 있다
    

# **inline-block**

inline&block의 특성 동시 적용하기

`tag {display: inline-block}`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/8a21b088-6925-4d71-80f3-5deec1bb3922.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/8a21b088-6925-4d71-80f3-5deec1bb3922.png)

- **장점**
    
    inline 처럼 한 줄이지만 height/ width 가질 수 있음
    

- **단점**
    
    좌우 여백의 크기가 다름
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/c2bc9762-4b50-42f7-b3ee-32cc6b53bb55.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/c2bc9762-4b50-42f7-b3ee-32cc6b53bb55.png)
    
    ![margin-right 값을 준다고 해도… 과하게 주면 다음줄로 넘어감](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/aa89737d-1955-4f90-af69-146d4d8b8690.png)
    
    margin-right 값을 준다고 해도… 과하게 주면 다음줄로 넘어감
    
    ![스크롤에 따라 크기가 달라짐](CSS%20e3b50/Untitled.png)
    
    스크롤에 따라 크기가 달라짐
    

# **flexbox**

- inline-block의 단점 극복 → 기본 값 유지하면서 창 크기에 가변적
    
    ![Untitled](CSS%20e3b50/Untitled%201.png)
    
    ![줄이면 찌그러짐](CSS%20e3b50/Untitled%202.png)
    
    줄이면 찌그러짐
    
- 가로 방향으로 배치되고, 자신이 가진 내용물의 width 만큼만 차지함. 마치 inline
    
    ![block](CSS%20e3b50/Untitled%203.png)
    
    block
    
    ![flex](CSS%20e3b50/Untitled%204.png)
    
    flex
    
- height는 컨테이너의 높이만큼 늘어납니다.
    
    ![Untitled](CSS%20e3b50/Untitled%205.png)
    

## **입력 방법**

각 tag에 명시x / 부모격 tag에 명시

`display: flex;`

![div에 명시x , body에 명시 → 그럼 body라는 부모가 flex 컨테이너 됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/e7052767-fc72-44f0-ac4a-1ce2e97147fc.png)

div에 명시x , body에 명시 → 그럼 body라는 부모가 flex 컨테이너 됨

## 기본축 설정

컨테이너는 주축과 교차축을 가지고 있음

부모에 jusify-content / align-items 입력해야 자식들이 행,열대로 늘어섬!

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/f6004b3d-8218-43cb-a670-7ee58ea039d5.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/f6004b3d-8218-43cb-a670-7ee58ea039d5.png)

![Untitled](CSS%20e3b50/Untitled%206.png)

- **X축 정렬** (기본값/ 변경 가능)
    
    `justify-content: □;`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/47acd0bf-0abf-4b1d-b1b9-397dd52ee3b8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/47acd0bf-0abf-4b1d-b1b9-397dd52ee3b8.png)
    
    ![ 값이 설정에 따라 정렬됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/722fddff-85d7-4f30-bb3e-64b9f0d36d29.png)
    
     값이 설정에 따라 정렬됨
    
    - `flex-end` : 끝 정렬
    - `flex-start`: 기본값
    - `space-evenly`: 빈 공간 같은 크기로 나누어 배치
    - `space-around` / `space-between` …
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/fcbf428a-9564-4056-8ce9-c70a0ff44839.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/fcbf428a-9564-4056-8ce9-c70a0ff44839.png)
    

- **y축 정렬**
    
    `align-items: □;`
    
    - body의 height 설정하고 적용할 것! width는 안해도 됨 (추천/ height: 100vh)
        
        (vh= viewpoint height = screen 화면을 꽉 채우는 높이
        
        vw= viewpoint width)
        
    - 설정하지 않고 적용시 (height 없다면)
        
        body가 안의 tag의 값에 맞춰져 있어서 변화 없을 수 있음
        
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/a45e1c64-aab6-4b2d-86bf-8c16dfce381c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/a45e1c64-aab6-4b2d-86bf-8c16dfce381c.png)
    
    ![전체 화면이 된 body 안에서 y축 center 정렬!](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/9182a513-2454-42be-a7b0-5aa4019e098c.png)
    
    전체 화면이 된 body 안에서 y축 center 정렬!
    
- 방향 **변경**
    
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
        
    
    이해를 돕는 개구리게임
    
    [https://flexboxfroggy.com/#ko](https://flexboxfroggy.com/#ko)
    

- **좋은 사용 예시 (box의 순서 뒤집기)**
    
    파랑 이용해서 빨강 만들기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/f01b1be7-cc2c-4fb2-a59a-b44e26e09219.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/f01b1be7-cc2c-4fb2-a59a-b44e26e09219.png)
    
    1. modifier 추가
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/600f371f-45b1-421f-8905-8e6c04f57600.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/600f371f-45b1-421f-8905-8e6c04f57600.png)
        
        파랑 태그를 그대로 복사한 다음, modifier (–own)을 붙여 다른 속성 부여하기
        
    
    2. 태그의 순서 바꾸기
    
    - **order**
        
        `order: n;`
        
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
        

## flex-wrap

`flex-item` 요소들이 강제로 한줄에 배치되게 할 것인지, 또는 가능한 영역 내에서 벗어나지 않고 여러행으로 나누어 표현 할 것인지 결정하는 속성

- flex-wrap: nowrap;
    
    ![Untitled](CSS%20e3b50/Untitled%207.png)
    

- flex-wrap: wrap;
    
    ![Untitled](CSS%20e3b50/Untitled%208.png)
    

- flex-wrap: wrap-reverse;
    
    ![Untitled](CSS%20e3b50/Untitled%209.png)
    

# **position**

## **fixed**

`position: fixed;`

- 스크롤 내려도 지정된 위치 그대로 있음
- fixed 하는 순간, 아예 다른 레이어가 됨 (맨위 레이어)
    
    아래에 태그를 작성하면 밑으로 놓이는게 아니라 아래 깔리는 형태가 됨.
    
    (z-index 설정해서 레이저 변경할 수 있음)
    
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

- 자기 자신을 기준으로 `top`, `right`, `bottom`, `left`의 값에 따라 오프셋을 적용합니다.
- top/ bottom/ left/ right 방향에서 숫자 만큼 떨어진다
- top: 10px; 하면 위로 이동하는게 아니라 오히려 아래로 10px만큼 이동하는 것이다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/307013c3-4f11-4bd4-b636-eee60e1bebf7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/307013c3-4f11-4bd4-b636-eee60e1bebf7.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d1bb932a-d26b-4844-9725-3d7bab562f94.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/d1bb932a-d26b-4844-9725-3d7bab562f94.png)

## **absolute**

`position: absolute;`

`top/ bottom/ left/ right: 숫자;`

- 새로운 레이어를 형성, 제일 위로 떠서 위치 선정
- 아래에 태그를 작성 시, 밑으로 놓이는게 아니라 아래 깔리는 형태가 됨
    
    (z-index 설정해서 레이어 수정 가능)
    
- 적용 시, width/ height이 적용되어 있지 않다면 자식의 사이즈에 맞춰 줄어든다
- 가장 가까운 relative한 부모 기준 (static 이 아닌 가까운

![green의 부모 = div, div에 relative 설정](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/31702fd7-89e1-45b5-9eb8-55f8c39a27ee.png)

green의 부모 = div, div에 relative 설정

![div 안에서 초록박스 움직임](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/af25b30b-fa11-450c-8c70-138100af1d65.png)

div 안에서 초록박스 움직임

![nav_notification 에 absolute 적용하려면 부모인 nav__link 에 position: relative 주면 된다. (nav__link: nth child(2)라고 콕 찝어서 설정 안해도 됌)](CSS%20e3b50/Untitled%2010.png)

nav_notification 에 absolute 적용하려면 부모인 nav__link 에 position: relative 주면 된다. (nav__link: nth child(2)라고 콕 찝어서 설정 안해도 됌)

- relative한 부모 없을 경우, body 기준
    
    
    - body에 relative 설정 시: 찐으로 스크롤 내리면 제일 밑에 있음
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/676112d5-a407-43e4-8cda-6418e6baf738.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/676112d5-a407-43e4-8cda-6418e6baf738.png)
        
    
    - body에 relative 미설정 시: 펼쳤을 때 보이는 화면 기준으로 이동
        
        ex) bottom: 0px → 스크롤을 내리기 전에는 맨 밑 스크롤을 내리면 밑에 공간 더 있음
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/12f02250-c25f-4a03-aee1-3d275b98c974.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/12f02250-c25f-4a03-aee1-3d275b98c974.png)
        

- **absolute 요소를 부모 정중앙에 놓기**
    - absolte 요소에 top: 50%, letf: 50% 를 선언하면, 요소의 좌상단 꼭지점이 정중앙에 옴
    - transform: translate (-50%, -50%); 하면 요소의 크기를 기준으로 너비와 높이의 50%만큼 좌상으로 이동하니까 정중앙으로 옴
        
        

# **pseudo selector**

여러 tag에 하나하나 id나 class 지정하기보다, 효율적으로 순서를 매겨서 지시하는 방법

형제 사이에서의 순서에 따라 요소를 선택

## **nth-child**

![이런 상황에서 사용!](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/29e9bed4-20b6-4f80-862f-c9b23294eabc.png)

이런 상황에서 사용!

`tag: first-child {…}` tag 중 가장 첫번째에 적용

`last-child {…}` tag 중 가장 마지막에 적용

`nth-child(숫자)` 지정한 순서에 적용

`nth-child(even)` 짝수에 적용

`nth-child(odd)` 홀수에 적용

`nth-child(숫자n+숫자 )` ↴

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ee0e527e-2e0c-4d9b-a995-816062e9472a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ee0e527e-2e0c-4d9b-a995-816062e9472a.png)

![첫번째 적용 후, 3번째마다 적용됨](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/783d50bf-ec9b-4538-8f4a-aec243377282.png)

첫번째 적용 후, 3번째마다 적용됨

- class도 적용 가능
    
    `.class: nth-child {…}` 
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/d7566615-5512-4f62-9adc-e121ef716e7d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/d7566615-5512-4f62-9adc-e121ef716e7d.png)
    

- span 적용
    
    `span:first-child {~;}` 
    
    모든 박스의 첫번째 span 에 모두 적용!
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/887d84c2-ed9b-49c8-8d3b-301c5535b9fc.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/887d84c2-ed9b-49c8-8d3b-301c5535b9fc.png)
    

- 주의사항
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
    

- **nth-of-type(n)**
    - 동일한 타입들 안에서 순서를 따짐
    - `span: nth-of-type(2)` : 2번째 span 에 적용
    - `first-of-type` / `last-of-type` : 첫번째, 마지막
    - even, odd, 2n+1 … 을 넣어서 활용 가능
    

# **combinator**

## **tag 지정**

- `부모 자식 {…}`
    
    특정한 부모-자식tag에만 지시 가능
    
    ![body / 이렇게 겹겹이 tag 들어가 있음](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1c7e98bc-6c83-42ea-9aee-9d82012f42dd.png)
    
    body / 이렇게 겹겹이 tag 들어가 있음
    
    ![div안의 p 안의 span 만 색깔 변경](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/5b1e2d43-9588-4aa2-a1fc-1c58caca4112.png)
    
    div안의 p 안의 span 만 색깔 변경
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ab12a368-0b3d-4c53-99c0-e66bba4942e9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ab12a368-0b3d-4c53-99c0-e66bba4942e9.png)
    
    - 부모 안에 있는 자식 태그 모두에 적용
        
        div span : div 안에 span에 모두 적용
        
        ```html
        <div>
        	<span>Hi</span>
        	<div class="inside-div">
        			<span>Hi2</span>
        	</div>
        </div>
        ```
        

- `부모 > 자식 {…}`
    
    부모 바로 아래 자식에만 지시
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/32458170-3efc-4a31-bf45-cc1b4a9d7317.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/32458170-3efc-4a31-bf45-cc1b4a9d7317.png)
    

- `자식 + 자식 {…}`
    
    바로 아래 있는 자매 tag에 지시 (부모자식 x, 자식 관계ㅇ)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/07cf95be-8906-4dc4-a6e8-7a470e3bdfbe.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/07cf95be-8906-4dc4-a6e8-7a470e3bdfbe.png)
    
- `자식~자식 {…}`
    
    뒤에 오는 자매에게 지시 (바로 뒤x)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/132a95c9-eaa0-4523-ba06-976fefe56ace.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/132a95c9-eaa0-4523-ba06-976fefe56ace.png)
    

## **attribute 지정**

- `tag:attribute {…}`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/6c4d2c27-de3f-4c04-a104-1c0fe5fd06df.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/6c4d2c27-de3f-4c04-a104-1c0fe5fd06df.png)
    
    ![input 중 required 만 지시](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/b27acf35-d66c-4950-b874-ba42f15aca58.png)
    
    input 중 required 만 지시
    
    ![이렇게 더 깔끔하게 정리할 수도 있음](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/88d7debe-8fa9-4564-b75f-430ce952bc24.png)
    
    이렇게 더 깔끔하게 정리할 수도 있음
    
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

![Untitled](CSS%20e3b50/Untitled%2011.png)

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

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/856b438e-8f94-41d2-8eb9-1e7446bc0b54.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/856b438e-8f94-41d2-8eb9-1e7446bc0b54.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/234ef492-27ad-4ba0-a6a0-53553da7ed6e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/234ef492-27ad-4ba0-a6a0-53553da7ed6e.png)

## **first-letter**

`tag::first-letter {…}`

첫번째 글자만 적용

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/8163a9b9-13f9-44e6-badc-2da5e24cdf1c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/8163a9b9-13f9-44e6-badc-2da5e24cdf1c.png)

- `first-line` : 첫번째 줄에 적용

# **색상**

## **hexadecimal color** (16진수 색상)

- #000000
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/dad74f27-be3d-41dd-a206-2d9a5c58d44c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/dad74f27-be3d-41dd-a206-2d9a5c58d44c.png)
    

- **rgb (red green blue)**
    
    rgb(000, 000, 000)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/5c4fd6a2-e701-4c50-90ac-6cdd3d280646.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/5c4fd6a2-e701-4c50-90ac-6cdd3d280646.png)
    

- rgba
    - a는 알파 → 투명도
    - 0 = 투명/ 1= 불투명
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ba0d5123-826a-4b7e-833c-ccd9377e4332.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/ba0d5123-826a-4b7e-833c-ccd9377e4332.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/c2d245f4-5362-48a9-b0e1-308beac92afd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/c2d245f4-5362-48a9-b0e1-308beac92afd.png)
    

# **변수**

`:root {a:b}`

→ `var(a)` = b

설정값을 변수로 만들어놓음. 효율적인 작성 가능.

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1370d85e-35dd-4205-a846-6d2d46769dec.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cfbeaa4ea93f4c8d883e09a2f471fb40/1370d85e-35dd-4205-a846-6d2d46769dec.png)

- main-color : 색상 지정
- default-boder: 경계선 지정
    
    (띄어쓰기 있으면 안됨, 무조건 - 쓸 것)
    

## **그림자 효과**

`box-shadow: inset;`

박스 안쪽에 그림자 효과

## 오버플로우

`overflow-축: hidden / scroll`

크기를 넘어서는 부분을 숨길지/ 스크롤 가능하게 할지

## **레이어 설정하기**

`z-index: ~;`

- default: 0
- 숫자가 작을수록 밑의 layer, 클수록 위의 layer
- `position: fixed/absolute` 에 이용 가능.

![Untitled](CSS%20e3b50/Untitled%2012.png)