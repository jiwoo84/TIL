# ADVANCED CSS

[→ Open in Slid](https://slid.cc/docs/b928a2f592124229b3b7326dabe56399)

---

# transition

상태 → 상태 사이에 애니메이션을 넣어줌

`tag {transition: 변하는 속성·시간·속도}`

`tag:state {변하는 속성: 속성값}`

### 조건

1. state가 없는 요소에 붙어야 함 (첫 상태 element)
    
    state에 붙는다면 state 상태에서만 애니메이션 작동
    
2. 속성이 state의 속성이어야 함 (그게 변화하는 요소니까)
    
    ![hover 시, background-color 변화하도록 설정했고](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/eaaf4e78-8bf8-4b18-a999-3c5d2f1cd818.png)
    
    hover 시, background-color 변화하도록 설정했고
    
    [천천히 변화한다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/b514ae91-866c-4ec4-b6d9-5ba78ce7cd2b.webm)
    
    천천히 변화한다
    

### 속성

- `all` → state 설정된 모든 요소 선택
- 각자 효과 다르게 주고 싶다면, 따로 쓰면 된다
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/cacdc4f6-6211-4392-b42c-4d56e45e3bd1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/cacdc4f6-6211-4392-b42c-4d56e45e3bd1.png)
    

## **ease-in function (속도)**

https://matthewlein.com/tools/ceaser (설명 사이트)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b928a2f592124229b3b7326dabe56399/131ad86a-fd9a-4965-91d0-84caa5176ef9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b928a2f592124229b3b7326dabe56399/131ad86a-fd9a-4965-91d0-84caa5176ef9.png)

- linear : 같은 속도로 변화
- ease-in : 시작과 끝이 빠름
- ease-out : 시작과 끝이 느림
- ease-in-out : 시작이 빠르고 끝이 느림
- cubic-bezier (0, 0, 0, 0) : 변화 커브 직접 설정

# transformation

요소에 회전, 크기 조절, 기울이기, 이동 효과를 부여

### **기본 문법**

`tag {transform: ~;}`

### **속성값 예시**

축: X/ Y/ Z

- `rotate축(~)` 지정 축을 중심으로 3D 회전
    - 축 지정 불필요 : rotate 는 중심을 점으로 회전
    - ex) `0.5turn` , `~deg`
- `scale축(~)` 지정 축을 중심으로 크기 n배로 변경
- `translate축(~)` 지정 축을 중심으로 이동
- `skew(~)` 비스듬히 기울이기

### **특징**

- 이 움직임은 다른 element에 영향주지 않고 받지도 않고 이동함
- 당연히 margin, padding 이 적용 안 됨

## **with transition**

`tag {transition: transform · 시간 · ease-in function}`

`tag:state {transform: 속성값}`

[천천히 돌아가는 애니메이션 만듬](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/ee4fade8-dc7b-410c-a9b0-8f714be1fb40.webm)

천천히 돌아가는 애니메이션 만듬

![이외 엄청 많은 효과들이 있음.. 복사해서 쓰면 됌](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/77912e1d-c9b3-478d-ac42-6f04b0928021.png)

이외 엄청 많은 효과들이 있음.. 복사해서 쓰면 됌

# animation

## **기본 문법**

`@keyframes 이름 {from{~:~;} to{~:~;} }`

`tag {animation: 이름·지속시간·ease-in function·유지시간}`

from 상태 → to 상태까지 애니메이션 됨 

- 유지시간
    - `infinite` 연속해서 계속
    - `forwards` 마지막 상태 유지

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/c6d169df-bcc4-426c-8016-4ab3067ae2ed.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/c6d169df-bcc4-426c-8016-4ab3067ae2ed.png)

[https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/c55b4740-c14f-4e54-b5ba-67c7642da731.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/c55b4740-c14f-4e54-b5ba-67c7642da731.webm)

- **단계별로 움직이게 하기**
    
    from& to 대신에 n%로 단계별로 지정
    

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/9c429b2a-4595-4ffa-8ded-0c6e09aa1b2d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/9c429b2a-4595-4ffa-8ded-0c6e09aa1b2d.png)

[https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/403dfaff-ea14-4030-9bff-98af5b0e4864.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/403dfaff-ea14-4030-9bff-98af5b0e4864.webm)

- **애니메이션 안정화**
    
    `will-change: ~;`
    
    애니메이션을 적용했는데 흔들리고 불안정 할 때,
    
    변화를 미리 알려줌으로써 애니메이션을 부드럽게 함
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/d5cd0a1f-4c99-401f-a959-b33f4c045236.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b6982c476559498bae1a6e437bbb01f5/d5cd0a1f-4c99-401f-a959-b33f4c045236.png)
    
- 챌린지 과제 예시
    
    ![중간 원을 중심으로 180deg 씩 돌고 있음](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b928a2f592124229b3b7326dabe56399/4c9faf01-7e6c-4ed6-9247-34ab35124597.png)
    
    중간 원을 중심으로 180deg 씩 돌고 있음
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/315b6e93-228e-49b9-b2a0-93b7a04ab4f1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/315b6e93-228e-49b9-b2a0-93b7a04ab4f1.png)
    
    - 가운데 점을 중심으로 풍차처럼 돌리고 싶다면 `transform: rotate` 이용
        
        height을 줘서는 안된다
        
    - 0~50% 까지 180도 돌고 → 50%~100% 까지 180도 돔
    - `from {transform:rotate(0.5turn);}`
        
        `to {transform:rotate(0.5turn);}` 로 쓰면 움직이지 않음
        
        ∵ 단순히 180도 돌아있는 상태 → 같은 상태 이므로
        
    
    - **animation-delay**
    
    `animation-delay: ~s;`
    
    입력된 시간만큼 애니메이션 딜레이 됨
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b928a2f592124229b3b7326dabe56399/59da68b5-8498-4741-8220-a10d498a76a6.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/b928a2f592124229b3b7326dabe56399/59da68b5-8498-4741-8220-a10d498a76a6.png)
    
    ![이런식으로 50%, 100% 를 같은 상태로 두고animation-delay 를 주면 된다!](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/4e3fdc31-1e4f-4924-841a-633558d06d55.png)
    
    이런식으로 50%, 100% 를 같은 상태로 두고animation-delay 를 주면 된다!
    

# media query

핸드폰, 스크린사이즈에 맞춰 변화하게 지시

- `@media screen and (max/min-width/height: …px)`
    
    `{tag {속성:속성값;}}`
    
    - max: width/ height가 ~px보다 클때 적용
    - min: width/ height가 ~px보다 클때 적용
    
- `@media screen and (min-width: …px) and (max-width: …px)`
    
    `{tag {속성:속성값;}}`
    
    min 과 max의 사잇값에 속성 적용
    
- `min/max-device-width` : 모바일 화면에서 적용
    - max~: ~이하/ min~: ~이상
    

![width가 600px보다 작을 때, 색깔 변경](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/478da117-9b18-4232-9016-2bfb2fb85795.png)

width가 600px보다 작을 때, 색깔 변경

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/ab0f83b1-1cc6-4900-8f6a-763fdecb0c6d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/ab0f83b1-1cc6-4900-8f6a-763fdecb0c6d.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/447333e8-8094-4d30-ac41-4ef87eb71401.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/447333e8-8094-4d30-ac41-4ef87eb71401.png)

- `@media screen and (orientation: landscape/ portrait)`
    
    `{tag {속성:속성값;}}`
    
    핸드폰 가로모드/세로모드 일 때, 속성 적용
    
    - 가로모드 확인
        
        우클릭 - 검사 - 노란동글뱅이 클릭
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/111ed282-84e1-4182-b863-9619586cb16a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/111ed282-84e1-4182-b863-9619586cb16a.png)
        
         `display: none;` 을 써서 가로모드에서 글씨를 없앰
        
- **조건 combination**
    
    and를 이용해서 이어주면 됨
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/f549e08c-20a2-426b-90f1-450ec97753a1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/f549e08c-20a2-426b-90f1-450ec97753a1.png)
    
    ↳ 이렇게 사용하면 화면 크기에 따라 3가지 색 볼 수 있음