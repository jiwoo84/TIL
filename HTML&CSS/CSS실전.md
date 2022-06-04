# CSS 실전

## vsc 단축어

- **class 포함한 div 만들기 단축키**
    - `.class*2`
        
        = `<div class="~"></div>` *2
        
    - `.class*2>tag`
        
        = `<div class="~"><tag></tag></div>` *2
        

- **** **tag1.class>tag2.class*n**
    
    = `<tag1 class="~">`
    
    `<tag2 class="~">`
    
    `<tag2 class="~"> * n개`
    
    이런식으로 쉽게 여러개 만들 수 있음
    

## **css 파일 나누기**

style.css 에는 모든 스크린에 적용될 수 있는 스타일을 써놓는다. 이는 하나의 방식이고, 자신만의 편한 방식을 택하면 된다.

## **여러 블럭 한줄로 맞추기**

space-between 상태

하지만 시계가 정가운데 아니고 가지고 있는 높이가 달라서 들쑥날쑥

이럴때 사용할 css hack

before

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/b2c8bb0a-4964-4b1b-92a6-9293270ef99b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/b2c8bb0a-4964-4b1b-92a6-9293270ef99b.png)

after

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/c7697802-f7d2-4050-a4f6-aa67243cdbb3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/c7697802-f7d2-4050-a4f6-aa67243cdbb3.png)

1.  먼저 space-between → center
    
    `부모 {justify-content:center;}`
    
2. 각자 같은 값의 width 부여 (3개니까 33%로)
    
    `자식 width: 33%;`
    
3. 가운데 부분을 flex/ center
    
    `display: flex;`
    
    `justify-content: center;`
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/012fa906-1deb-43ce-83ea-f0fb805c86df.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/012fa906-1deb-43ce-83ea-f0fb805c86df.png)
    
4. 나머지 flex 주고 원하는대로 조정

## **기본 설정 사항 없애기** (margin 등)

- reset.css 파일 만들기
    
    ① 파일 (reset.css) 새로 만듬
    
    ② 코드 복붙 ([사이트](https://meyerweb.com/eric/tools/css/reset/))
    
    ③ css 파일에 `@import "reset.css"` 추가
    
    +css파일에 추가하는게 좋음
    
    [https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/58d42e7d-d476-4e28-81af-ad9c9c7cb9a1.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/58d42e7d-d476-4e28-81af-ad9c9c7cb9a1.webm)
    

## 특정 속성만 적용 안하는 요청

`#id(.class) tag:not ([속성="속성값"]) {~}`

tag 에서 [속성=“속성값”] 만 빼고 적용

## 특정 속성만 적용

`#id(.class) tag[속성="속성값"] {~}`

## **마우스 포인터 모양 변경**

`cursor : 속성값`

- pointer (손가락)
- not-allowed (선택 안됨)
- progress (로딩중)

## a의 밑줄 없애기

![Untitled](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled.png)

- `text-decoration: none;`

## **inherit**

`속성: inherit;`

tag의 부모로부터 값 상속

![a 의 기본값은 blue, 하지만 inherit 하면 a의 부모 격에서 상속되기 때문에 default 값인 검정색](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/d9cdde0d-b3db-4dc3-bd23-2ec12df829dc.png)

a 의 기본값은 blue, 하지만 inherit 하면 a의 부모 격에서 상속되기 때문에 default 값인 검정색

## **form의 attributes**

- `form: action="…"`
    
    어떤 페이지로 data 보낼건지 지정
    
    - ex) `form: action="friends.html"`
        
        input 실행시, friends 라는 html 파일이 이어서 실행
        
- `form: method="…"`
    
    
    - `form: method="post"`
        
        백엔드 서버에 정보 전송
        
    - `form: method="get"`
        
        서버 없어도 됨
        
        (보안에 취약 url에 포함되어도 상관없는 정보들을 get으로 내보내야함, 자세히는 유튜브 클론코딩)
        
        - 하위 input 에 name 설정할 것
        
        ![html 작성/ 위 username, 아래 password](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%201.png)
        
        html 작성/ 위 username, 아래 password
        
        ![input에 입력해서 login 클릭하면](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%202.png)
        
        input에 입력해서 login 클릭하면
        
        ![url에 이렇게 표시된다](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%203.png)
        
        url에 이렇게 표시된다
        
        ## **하단/상단 고정**
        
        ```css
        position: fixed
        bottom: 0 (아래인 경우)
        top: 0 (위인 경우)
        width: 100%
        box-sizing: border-box
        ```
        
        ## **box-sizing: border-box**
        
        width,height 지정 상태에서 border 지정 시,
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/fb248efe-7ed4-42c4-9325-48fb9135916f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/fb248efe-7ed4-42c4-9325-48fb9135916f.png)
        
        지시 유지하기 위해서 박스가 커짐 (상하좌우 모두 마찬가지)
        
        ex) width: 50px / border: 30px
        
        = 결과적으로 크기 80px으로 보임
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/00aeecaa-9db7-48f6-8b99-408a7dd006ca.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/00aeecaa-9db7-48f6-8b99-408a7dd006ca.png)
        
        box-sizing: border-box 쓰면 box사이즈 신경쓰지 않고 border 만들어짐
        
        ex) width: 50px / border: 30px
        
        = 결과적으로 50px으로 보임
        

- **사용 예시**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/18518474-3a34-4ef1-8db0-3ff47b193d84.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/18518474-3a34-4ef1-8db0-3ff47b193d84.png)
    
    이렇게 다 입력했는데 안 보일 때!
    
    width/ height + border + padding + margin… 이렇게 합쳐져서
    
    화면보다 크게 되어있을 가능성이 농후함
    
    이럴때 box-sizing: border-box; 쓰면
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/5f98558a-f3c7-4b21-b242-907af82dc92e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/5f98558a-f3c7-4b21-b242-907af82dc92e.png)
    
    이렇게 화면 안으로 들어온다!
    
- **navigation 만들기**
    
    `nav>ul>li*필요갯수>a` (단축코드)
    
    ```
        <nav>
            <ul>
                <li><a href=""></a></li>
                <li><a href=""></a></li>
                ...
            </ul>
        </nav>
    ```
    
    이게 기본적인 네비게이션의 구조
    
    입력하면 바로 커서가 입력해야 할 곳에 생김
    
    tab눌러 이동하면 원하는대로 이동
    
- **사진 사이즈 비율 유지**
    
    `object-fit: cover;`
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ec1d78fb-aeec-4ab6-afee-0e45eac75f17.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ec1d78fb-aeec-4ab6-afee-0e45eac75f17.png)

- 같은 .class(pseudo selector) {속성:속성값}을 공유하지만 특정 부분에 flex를 적용하고 싶지 않다면?
    
    → 해당 부분만 떼서 한 번 더 감싸줌
    
    부모-자식관계를 끊고 부모-손자 관계가 되어 부모의 flex 영향 받지 않음
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/715b5ef6-ed32-4e6d-9e74-9188fb6e23a4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/715b5ef6-ed32-4e6d-9e74-9188fb6e23a4.png)

![안에 넣어서 손자로 만듬](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/8b10b98f-b383-4171-9be1-4c0356d7dd81.png)

안에 넣어서 손자로 만듬

## 짧은 divider 만들기

- **div로 이용**

(그냥 `l`써도 되지만 div이용하려면…)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/7344be39-19f7-4613-bad2-fde89bb45a42.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cfbeaa4ea93f4c8d883e09a2f471fb40/7344be39-19f7-4613-bad2-fde89bb45a42.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/696021fb-9325-44f9-a4b5-0df3b9624b78.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cfbeaa4ea93f4c8d883e09a2f471fb40/696021fb-9325-44f9-a4b5-0df3b9624b78.png)

div에 공간감 주면 만들 수 있음!

## 아이콘에 링크 넣기

`<a href="파일명/링크”><i class=”아이콘”></i></a>`

a태그로 아이콘 감싸주기

## **margin: 0 auto;**

- 가로 정중앙 만들 수 있는 코드
- space-between은 글자수에 따라 중앙 아닐 수 있기 때문에 auto를 적절히 잘 사용하면 중앙에 놓을 수 있다!

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/82221621-50f9-4316-af34-9b0db6b918d0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/82221621-50f9-4316-af34-9b0db6b918d0.png)

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
    
    ![Untitled](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%204.png)
    

- flex 설정 시
    
    ```css
    .main-chat {
      margin-top: 120px;
      display: flex;
    }
    ```
    
    ![Untitled](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%205.png)
    

- flex-direction: column; 적용시
    
    ```css
    .main-chat {
      margin-top: 120px;
      display: flex;
      flex-direction: column;
    }
    ```
    
    ![Untitled](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%206.png)
    
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
    
    ![Untitled](CSS%20%E1%84%89%E1%85%B5%E1%86%AF%E1%84%8C%E1%85%A5%E1%86%AB%20ef25d/Untitled%207.png)
    
    다시 줄어들었다
    
    이유는... 나도 모름
    

## **splash screen (앱 시작 페이지) 만들기**

1. **forwards**
    
    `animation: 이름 · 지속시간 · ease-in function · **forwards**`
    
    keyframes의 마지막 애니메이션 기억
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/feaaf4fc-7a22-4561-9da2-651294a9881d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/feaaf4fc-7a22-4561-9da2-651294a9881d.png)
    
    ![opacity:0.1 이라서 흐리게 남아있음](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/b6691985-8a59-4b21-9edb-0acf135c158d.png)
    
    opacity:0.1 이라서 흐리게 남아있음
    
    - 여기서 끝내면 안되는 이유
        
        opacity:0 이라 안 보이더라도 화면 위에 있는 것! 클릭 안됨
        
- **** `visibility: hidden;`
    - 존재하긴 하지만 보이지 않고 마우스에 걸리지 않음
        
        그러나 숨겨놓은 것에 불과하기 때문에 javascript 필요
        
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/7aaec57a-9028-4897-a0ea-7484075596a0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/7aaec57a-9028-4897-a0ea-7484075596a0.png)
    
    [https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/6bf8e774-4c27-4bcc-bbd7-698428a41650.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b6982c476559498bae1a6e437bbb01f5/6bf8e774-4c27-4bcc-bbd7-698428a41650.webm)
    

## **없다가 올라오는 애니메이션 만들기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/2d22776f-e43b-4e65-8013-f03ac8a4e188.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/2d22776f-e43b-4e65-8013-f03ac8a4e188.png)

1. 태그에 translate로 위치 이동 (opacity로 아예 안보이게 할 수도)
2.  `@keyframes { to {transform: none;} }` 으로 위치 변경해서 없애준다
3. forwards 적용해서 위 상태 유지할 것
    
    (안하면 애초에 적용한 transform으로 돌아감)
    

- **애니메이션 안정화**
    
    `will-change: ~;`
    
    애니메이션을 적용했는데 흔들리고 불안정 할 때,
    
    변화를 미리 알려줌으로써 애니메이션을 부드럽게 함
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/d5cd0a1f-4c99-401f-a959-b33f4c045236.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/d5cd0a1f-4c99-401f-a959-b33f4c045236.png)
    
    - Assignment 11 숙제
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/79b95081-95b1-4b06-8a39-7469a96b1709.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/79b95081-95b1-4b06-8a39-7469a96b1709.png)
        
    

## **body값 설정하기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/0f3fa372-f148-422a-81c9-1b2a8d8da408.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/0f3fa372-f148-422a-81c9-1b2a8d8da408.png)

- 따로 width/ height 주지 말고, 안에 다른 container 를 만들거나 정렬만 잡아주면 됨
- 크기 설정하려면 퍼센트가 깔끔함 -> 그러려면 부모부터 퍼센트로 계획적으로 크기 잡을 것
- container 값 설정하기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/1d444c7e-dc4e-4c52-82d7-1dbe4940a340.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/1d444c7e-dc4e-4c52-82d7-1dbe4940a340.png)
    
    니코의 screen 크기설정 min-height 까지 보다가 맘
    
    아예 height을 없애도 크기가 그대로 있는데 왜그러지? 그럼 앞으로는 container 크기는 따로 정하지 않아도 되는가?
    

## 자잘한 예시

- 앱의 크기 만들기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/a26c74b8-d40a-4b6b-b9dd-c871f7c7a882.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/a26c74b8-d40a-4b6b-b9dd-c871f7c7a882.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/eb374dda-639e-4526-bb00-12d8b7cfc0a2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/eb374dda-639e-4526-bb00-12d8b7cfc0a2.png)
    
    따로 body 크기를 설정하지 말고
    
    margin 양 옆/ 아래 공간 padding 주기
    

- **header 배경 만들기**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/c8c01703-476d-4553-834c-71a926aef468.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/c8c01703-476d-4553-834c-71a926aef468.png)
    
    header의 width/ height를 지정x
    
    → 각 header의 padding값을 지정하는 것이 좋음
    

- **header 정렬**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/9ee5fbdb-edca-4792-8ae9-159a9a71f91d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/9ee5fbdb-edca-4792-8ae9-159a9a71f91d.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e3dcbfe3-7c3e-4975-acf8-ee362c196794.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e3dcbfe3-7c3e-4975-acf8-ee362c196794.png)
    
    (위에 나온 방법) 전체에 width:33% 주고 그 안에서 중앙정렬
    
- **search bar 만들기**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/efb08d0b-f81d-427d-9060-16c80372fc21.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/efb08d0b-f81d-427d-9060-16c80372fc21.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/cfd1d26f-774d-4a47-8104-130d909880af.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/cfd1d26f-774d-4a47-8104-130d909880af.png)
    
    Q. 어떻게 search 바를 올리고, 돋보기 아이콘도 올리나요?
    
    방법은 두가지!
    
    **① header에 relative → search-bar를 absolute해서 올리고, 안에서 input & i 정렬**
    
    쉽게 떠올릴 수 있지만, 생각보다 복잡해진다
    
    ∵ search-bar를 absolute하게 되면, 다른 레이어가 되면서
    
    크기 퍼센트 설정 불가,아예 margin, padding 새로 설정해야 한다.
    
    **② search-bar에 relative 설정, top: -30px 줘서 올림 → 돋보기에 absolute 줘서 정렬**
    
    이렇게 하면 훨씬 간결하고 쉬워진다!
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e0ca791a-0811-493b-822d-04c41db207ac.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e0ca791a-0811-493b-822d-04c41db207ac.png)
    
    ★ absolute 를 줘야 하는 상황이라면, 큰 것보단 최대한 작고 모양이 잡힌 것에 줘야 함
    

# day13

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/b3f0b25c-4a91-43d0-9499-cb7aa95b770c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/b3f0b25c-4a91-43d0-9499-cb7aa95b770c.png)

**1. 왼쪽 아래 부분 만들기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/547d7dcf-66f2-48df-80c8-4a4260c6142b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/547d7dcf-66f2-48df-80c8-4a4260c6142b.png)

모양 만들고 `position: absolute;`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/3baf4f7d-1809-45a3-8831-a7577426b395.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/3baf4f7d-1809-45a3-8831-a7577426b395.png)

relative를 왼쪽 screen

absolute 설정 후, 위 방법으로 중앙 정렬

+ 다른 방법

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/4ba111cf-b565-4d54-bff5-bb209fb50afb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/4ba111cf-b565-4d54-bff5-bb209fb50afb.png)

**2. 재생 바 만들기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/6ba18cda-7fa3-483f-99ac-526b144d8c58.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/6ba18cda-7fa3-483f-99ac-526b144d8c58.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/41449868-6d48-4037-a097-f5cd9077cec8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/41449868-6d48-4037-a097-f5cd9077cec8.png)

재생 됨 - 동글뱅이 - 전체 바

→ 모두 형제 관계로 작성

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/5d8c3de1-7fba-425d-bbf2-0e3e9492115b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/5d8c3de1-7fba-425d-bbf2-0e3e9492115b.png)

- total 부분에 relative 설정하고

played에 absolute 하니까, 위치 따로 안잡아도 알맞게 위치함

- played와 marker 를 absolute 안했으면 위에서 아래로 나열됨

+ 다른 방법

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/80fc68e8-fd78-4528-8745-db596e165176.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/80fc68e8-fd78-4528-8745-db596e165176.png)