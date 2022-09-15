# ADVANCED CSS

[→ Open in Slid](https://slid.cc/docs/b928a2f592124229b3b7326dabe56399)

---

# Transformation

`tag {transform: ~;}`

요소에 회전, 크기 조절, 기울이기, 이동 효과를 부여

- 한 요소에 여러 번 적용 ⇒ 맨 마지막 속성 적용
- 이 움직임은 다른 element에 영향주지 않고 받지도 않고 이동함
- 당연히 margin, padding 이 적용 안 됨
- 크로스 브라우징 체크 (prefix 접두사)
    
    transformation은 css3의 최신문법이기 때문에 구버전의 브라우저에서는 동작하지 않을 수도 있음. prefix 접두사를 붙여줘야함
    
    ```css
    .transition {
    	-webkit-transform: translate(100px, 200px); /* 크롬, 사파리 */
    	-mox-transform: translate(100px, 200px); /* 파이어폭스 */
    	-mx-transform: translate(100px, 200px); /* 익스플로러 9.0 */
    	-o-transform: translate(100px, 200px); /* 오페라 */
    }
    ```
    

## **속성값**

축: X / Y / Z

### rotate

- `rotate(~)` 중심을 점으로 회전 (`0.5turn` , `~deg`, 음수 가능)
- `rotate축(~)` 지정 축을 중심으로 회전

### scale

- `scale(~)` 전체적으로 n배 확대 (소수사용으로 축소 가능)
- `scale(x, y)` x축, y축을 입력한 수만큼 확대
- `scale축(~)` 지정 축을 중심으로 크기 ~배 확대

### translate

- `translate(x, y)` x축, y축으로 입력한만큼 이동 (음수 가능)
- `translate축(~)` 지정 축을 중심으로 이동

### skew

- `skew(x[, y])` x축, y축을 기준으로 입력한만큼 비틀어 회전 (음수 가능)
- `skew축(~)` 지정 축을 기준으로 비틀어 회전

# Transition

특정 조건에서 애니메이션이 동작

기본값 설정(트랜지션 설정) & 상태 변경 태그(속성-속성값 설정) ⇒ 기본값에서 상태 변경 시, 속성이 변경

### **기본 태그**

`tag {transition: 지정속성 지속시간 속도 [delay]}`

- 속도 (ease-in function)
    - linear : 같은 속도로 변화
    - ease-in : 시작과 끝이 빠름 ([눈으로보기](https://matthewlein.com/tools/ceaser))
    - ease-out : 시작과 끝이 느림
    - ease-in-out : 시작이 빠르고 끝이 느림
    - cubic-bezier (0, 0, 0, 0) : 변화 커브 직접 설정
- 속성값 따로 설정하기
    - `transition-property` 변할 속성
    - `transition-duration` 지속 시간
    - `transition-timing-funtion` 효과의 속도
    - `transition-delay` 특정조건하에서 실행 (딜레이 설정 가능)
    

### **상태 변경 태그**

`tag:state {지정속성: 속성값}`

![hover 시, background-color 변화하도록 설정](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/b928a2f592124229b3b7326dabe56399/eaaf4e78-8bf8-4b18-a999-3c5d2f1cd818.png)

hover 시, background-color 변화하도록 설정

[천천히 변화한다](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/b928a2f592124229b3b7326dabe56399/b514ae91-866c-4ec4-b6d9-5ba78ce7cd2b.webm)

천천히 변화한다

### 속성

- `all` → state 설정된 모든 요소 선택
- 각자 효과 다르게 주고 싶다면, 따로 쓰면 된다
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/cacdc4f6-6211-4392-b42c-4d56e45e3bd1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/b928a2f592124229b3b7326dabe56399/cacdc4f6-6211-4392-b42c-4d56e45e3bd1.png)
    

# Animation

`@keyframes 이름 {from{~:~;} to{~:~;} }`

`tag {animation: 이름 지속시간 속도 유지시간 [delay 반복횟수 진행방향]}`

from 상태 → to 상태까지 애니메이션 됨

- 크로스 브라우징 체크 (prefix)
    
    ```css
    .animation{
    		/* animation 속성 앞에 붙여주기 */
        -webkit- animation: changeWidth 3s linear 1s 6 alternate; 
    }
    
    /* 대응되는 @keyframes 앞에 붙여주기 */
    -webkit- @keyframes changeWidth {
    		/* 만약 안에서 transform같이 css3 사용한다면 그 앞에도 붙여야함 */
        from { -webkit- transform: rotate(-10deg); }
        to { -webkit- width: 600px; }
     }
    ```
    
- `animation-name` : 이름
- `animation-duration` : 지속시간
    - `infinite` 연속해서 계속
    - `forwards` 마지막 상태 유지
- `animation-timing-function` : 속도
- `animation-delay` : 딜레이 시간
- `animation-iteration-count` : 반복 횟수
- `animation-direction` : 진행 방향
    - `alternate` : from→to→from (왔다갔다하며 반복횟수 2개 차감)
    - `nomal` : from → to
    - `reverse` : to → from

### **단계별로 움직이게 하기**

from& to 대신에 n%로 단계별로 지정

```css
.animation{
    animation: changeWidth 3s linear 1s 6 alternate;
}

@keyframes changeWidth {
    from {
        width: 300px;
    }
    to {
        width: 600px;
    }
 }
```

![AC_[20200805-161944].gif](ADVANCED%20CSS%20eae3aa6e815b4214abaa01b484424b54/AC_20200805-161944.gif)

### **애니메이션 안정화**

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
    

# Media query

pc / mobile / 태블릿에도 대응되는 반응형, 적응형 웹사이트 만들기 위해 사용하는 구문

## 구문

`@media 미디어 유형 / 논리연산자 / 특성`

### 미디어 유형

- `@media all {}` 모든 디바이스 대상
- `@media print {}` 인쇄 결과물, 인쇄 미리보기 문서
- `@media screen {}` 컴퓨터 스크린, 태블릿, 스마트폰 등
- `@media speech {}` 스크린 리더기 or 리더기 읽어주는 미디어

### 논리연산자

- `@media all and {}` 모든 쿼리가 참이어야 적용
- `@media all not {}` 모든 쿼리가 거짓이어야 작용
- `@media all, (comma) {}` 어느 하나라도 참이면 적용(or)
- `@media only screen {}` 미디어쿼리를 지원하는 브라우저만 적용

## 속성

### 화면 크기 변경에 반응

- `@media screen and (max/min-width/height: …px) {tag {속성:속성값;}}`
    - min: width/ height가 ~px보다 클 때 적용
    - max: width/ height가 ~px보다 작을 때 적용
- `@media screen and (min-width: …px) and (max-width: …px) {tag {속성:속성값;}}`
    
    min 과 max의 사잇값에 속성 적용
    

### 모바일 화면에서 적용

- `min/max-device-width` : 모바일 화면에서 적용
    - max~: ~이하/ min~: ~이상

### 모바일 가로/세로모드

- `@media screen and (orientation: landscape/ portrait)`
    
    `{tag {속성:속성값;}}`
    
    핸드폰 가로모드/세로모드 일 때, 속성 적용
    

## 주의사항

### viewport

스마트기기는 기본으로 설정된 뷰포트 영역으로 인해 미디어 쿼리가 정상적으로 작동하지 않을 수 있음 ⇒ 이를 방지하기 위해 뷰포트 메타 태그를 이용해 화면의 크기, 배율 조절해야함

`<meta name="viewport" content="width=device-width, initial-scale=1.0 ">`

- width=device-width
    
    viewport의 가로폭 = 디바이스의 가로폭으로 조절
    
- initial-scale=1.0
    
    기기에서 화면의 크기를 1.0으로 유지함
    

### CSS 속성 상속

미디어쿼리에서 지정하지 않은 속성은 외부 영역에 있는 CSS 속성을 상속받음
(미디어쿼리로 bakcground-color을 지정하지 않으면 원래 값 쓴다는 말)

⇒ 상속받지 않으려면 none 입력 ex) `background-color: none;`