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

### 같은 class를 공유하지만 특정 부분에 flex를 적용하고 싶지 않다면?

→ 해당 부분만 떼서 한 번 더 감싸줌

부모-자식관계를 끊고 부모-손자 관계가 되어 부모의 flex 영향 받지 않음

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ec1d78fb-aeec-4ab6-afee-0e45eac75f17.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b6982c476559498bae1a6e437bbb01f5/ec1d78fb-aeec-4ab6-afee-0e45eac75f17.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/715b5ef6-ed32-4e6d-9e74-9188fb6e23a4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/715b5ef6-ed32-4e6d-9e74-9188fb6e23a4.png)

![안에 넣어서 손자로 만듬](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/8b10b98f-b383-4171-9be1-4c0356d7dd81.png)

안에 넣어서 손자로 만듬

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
    

## **body값 설정하기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/79b95081-95b1-4b06-8a39-7469a96b1709.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/79b95081-95b1-4b06-8a39-7469a96b1709.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/0f3fa372-f148-422a-81c9-1b2a8d8da408.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/0f3fa372-f148-422a-81c9-1b2a8d8da408.png)

- 따로 width/ height 주지 말고, 안에 다른 container 를 만들거나 정렬만 잡아주면 됨
- 크기 설정하려면 퍼센트가 깔끔함 -> 그러려면 부모부터 퍼센트로 계획적으로 크기 잡을 것
- container 값 설정하기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/1d444c7e-dc4e-4c52-82d7-1dbe4940a340.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/1d444c7e-dc4e-4c52-82d7-1dbe4940a340.png)
    
    니코의 screen 크기설정 min-height 까지 보다가 맘
    
    아예 height을 없애도 크기가 그대로 있는데 왜그러지? 그럼 앞으로는 container 크기는 따로 정하지 않아도 되는가?
    

### 앱의 크기 만들기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/a26c74b8-d40a-4b6b-b9dd-c871f7c7a882.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/a26c74b8-d40a-4b6b-b9dd-c871f7c7a882.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/eb374dda-639e-4526-bb00-12d8b7cfc0a2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/eb374dda-639e-4526-bb00-12d8b7cfc0a2.png)

따로 body 크기를 설정하지 말고

margin 양 옆/ 아래 공간 padding 주기

### **header 배경 만들기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/c8c01703-476d-4553-834c-71a926aef468.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/c8c01703-476d-4553-834c-71a926aef468.png)

header의 width/ height를 지정x

→ 각 header의 padding값을 지정하는 것이 좋음

- **header 정렬**
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/9ee5fbdb-edca-4792-8ae9-159a9a71f91d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/9ee5fbdb-edca-4792-8ae9-159a9a71f91d.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e3dcbfe3-7c3e-4975-acf8-ee362c196794.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/e3dcbfe3-7c3e-4975-acf8-ee362c196794.png)
    
    (위에 나온 방법) 전체에 width:33% 주고 그 안에서 중앙정렬
    

### **search bar 만들기**

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

### 1. **왼쪽 아래 부분 만들기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/547d7dcf-66f2-48df-80c8-4a4260c6142b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/547d7dcf-66f2-48df-80c8-4a4260c6142b.png)

모양 만들고 `position: absolute;`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/3baf4f7d-1809-45a3-8831-a7577426b395.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/3baf4f7d-1809-45a3-8831-a7577426b395.png)

relative를 왼쪽 screen

absolute 설정 후, 위 방법으로 중앙 정렬

+ 다른 방법

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/4ba111cf-b565-4d54-bff5-bb209fb50afb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/4ba111cf-b565-4d54-bff5-bb209fb50afb.png)

### 2. **재생 바 만들기**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/6ba18cda-7fa3-483f-99ac-526b144d8c58.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/6ba18cda-7fa3-483f-99ac-526b144d8c58.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/41449868-6d48-4037-a097-f5cd9077cec8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/41449868-6d48-4037-a097-f5cd9077cec8.png)

재생 됨 - 동글뱅이 - 전체 바

→ 모두 형제 관계로 작성

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/5d8c3de1-7fba-425d-bbf2-0e3e9492115b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b6982c476559498bae1a6e437bbb01f5/5d8c3de1-7fba-425d-bbf2-0e3e9492115b.png)

- total 부분에 relative 설정하고 played에 absolute 하니까, 위치 따로 안잡아도 알맞게 위치함
- played와 marker 를 absolute 안했으면 위에서 아래로 나열됨

### 다른 방법

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/80fc68e8-fd78-4528-8745-db596e165176.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/80fc68e8-fd78-4528-8745-db596e165176.png)