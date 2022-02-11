# with browser

[→ Open in Slid](https://slid.cc/docs/cf74e387fe0d4abca62153b8b0eec072)

---

# Document

- DOM 트리의 최상위 객체
- js에서 접근 가능한 html의 객체
- 브라우저가 자동으로 실행한 js & html의 연결고리

![console.log 로 단순 값만 출력 시 : html 태그 보여줌](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/80a1398a-fa68-42b3-8f21-d52630207557.png)

console.log 로 단순 값만 출력 시 : html 태그 보여줌

![console.dir 로 element까지 출력 시](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/fa6b5c8f-bf99-42e9-9df5-b4bf0e996d3e.png)

console.dir 로 element까지 출력 시

## 추가/변경

`document.prop = ~`

- 수많은 property 를 가짐 → 추가, 변경 가능

![js를 통해 html <head> 속 title 내용 바꿈](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/0713e45b-3ddb-4ee3-b254-078010408c64.png)

js를 통해 html <head> 속 title 내용 바꿈

- 주요 property
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/e811e01a-2f22-414f-95ac-dbdf34a3433d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/e811e01a-2f22-414f-95ac-dbdf34a3433d.png)
    
    - `body` / `head` / `title` : 직접 호출 가능한 요소
        
        body 안 tag같이 상세한 요소는 호출 불가 (getElementByid 같은거 이용해야함)
        

# js에서 html 읽기

**(html) element → (js) object** 로 읽음

el의 class명(classname), 내용(innertext) → 하위 prop로 인식

![<h1> 요소 불러온 모습](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/cf74e387fe0d4abca62153b8b0eec072/68732b7f-9666-4789-ab9a-1ae55bc53184.png)

<h1> 요소 불러온 모습

![그러므로 class명 변경하면](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/aa35b6d1-3196-472e-ade9-792f251d8937.png)

그러므로 class명 변경하면

![h1(obj)안의 classname(prop)이 변경](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/6175a188-8f73-40fb-95a7-765cf5dc3b19.png)

h1(obj)안의 classname(prop)이 변경

# elment 호출

js에서 html의 element 호출

## **getElementById**

id로 element 찾음

`document.getElemmentById("id-name");` = object

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/0646819b-f687-48e1-b982-54950d091a6e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/0646819b-f687-48e1-b982-54950d091a6e.png)

console에서 입력 시, h1인 el 가져왔다

- **getElementsByClassName**

class로 다수의 el 찾음

`document.**getElementsByClassName**("class-name");` = array

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/ecbc9026-eb47-4071-b259-1d31e8d52e40.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/ecbc9026-eb47-4071-b259-1d31e8d52e40.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/cbe391ec-d8d2-42ef-9331-fd6e0a813ce2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/cbe391ec-d8d2-42ef-9331-fd6e0a813ce2.png)

js에서 호출

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/833a9ffd-abdf-4c8f-8d66-f454049cacb0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/833a9ffd-abdf-4c8f-8d66-f454049cacb0.png)

★obj 아닌 여러개의 el 있는 **array**이기 때문에 prop가 없다

∵ var 값 할당 후, `var-name.prop=~;` 로 변경 불가

- **getElementsByTagName**

tag명으로 다수의 el 찾음

`document.**getElementsByTagName**("tag-name");` = array

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/ef629ae1-dd83-4ad7-8aef-b46314b0f2dd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/ef629ae1-dd83-4ad7-8aef-b46314b0f2dd.png)

↳

,

,

,  … 모두 가능

*** querySelector (주로 사용)**
element 를 css 방식으로 검색
`document.**querySelector**("~");` = object
↳ .class / #id / i : first-child …
- 못 찾으면 null 로 표시
- 맨 첫번째 값만 표시

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/789e5703-4997-4850-af01-b8461f275d6c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/789e5703-4997-4850-af01-b8461f275d6c.png)

class = hello > h1 검색

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/0da848f5-e01b-4ce1-8e41-1893333d84bb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/0da848f5-e01b-4ce1-8e41-1893333d84bb.png)

obj 로 가져옴

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/7b485763-9852-4109-92a9-bc23fb1a3ea9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/7b485763-9852-4109-92a9-bc23fb1a3ea9.png)

결과적으로, 이 두 코드는 같은 일을 한다

- **querySelectorAll**

조건에 부합하는 값 모두 가져옴

`document.querySelectorAll("~");` = array

- 첫번째 값만 → querySelector
- 모두 다 → querySelectorAll

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/0d4b4e2a-f507-4b56-b4ea-9f63a1a66e40.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/0d4b4e2a-f507-4b56-b4ea-9f63a1a66e40.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/722e025e-8065-4aa4-8bf7-7f65794cf5fb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/722e025e-8065-4aa4-8bf7-7f65794cf5fb.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/3c4690ba-ec88-480b-beeb-cc66285ef538.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/3c4690ba-ec88-480b-beeb-cc66285ef538.png)

3개의 h1 있는 array 출력

**★ 하위 tag 가져오는 방법**

① (상위 tag에 var 할당되어 있다면) `**상위var**.fnc("tag");`

- document가 아닌 상위var에서 el 찾기

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/8dd363af-bce8-458d-b906-334c9d54e8c3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/8dd363af-bce8-458d-b906-334c9d54e8c3.png)

② 바로 document 안에서 하위 tag 찾는다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/a1b8bfd4-144c-421e-9c1d-888fdead1a5b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/a1b8bfd4-144c-421e-9c1d-888fdead1a5b.png)

# js에서 html 변경

(html) el의 class/ id 나 위치 파악→ (js) document.~ 이용해서 호출 → fnc 이용해서 변경

- **변경하는 과정**

① (html) 바꾸고 싶은 el에 id/ class 혹은 위치 파악

② (js) 값을 찾아 var 로 할당

ex) `var var-name = document.querySelector("~");`

③ (js) object의 변경 prop 확인 후, 코드 작성

- `var-name.prop = ~;`

var-name = object 일 경우에만 가능!

+ event에 반응하게 하려면 fnc 제작 후, 코드 작성

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/72cb414f-bdb1-4996-8d1d-24fb1eacfb86.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/72cb414f-bdb1-4996-8d1d-24fb1eacfb86.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/84c8e856-ae58-4972-a3c7-58645273701e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/84c8e856-ae58-4972-a3c7-58645273701e.png)

변경 완료!

- **자주 나오는 오류**

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/c392f7a0-6545-4aa4-a98a-f3a021a49146.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/c392f7a0-6545-4aa4-a98a-f3a021a49146.png)

명령을 내린 id나 class 존재하지 않을 때 발생

- **js에서 스타일 변경** (비추; css에서 변경할 것)

`obj.**style**.prop = ~;`

- el> style (= object) > prop
- style은 el의 생김새, prop를 가진 obj

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/87974dce-da31-4e53-b6d1-ea15ce1e4373.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/87974dce-da31-4e53-b6d1-ea15ce1e4373.png)

el 안에 style(obj) 안에 또 수많은 obj…

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/676c44b9-e503-41cf-b378-729b6f462d94.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/676c44b9-e503-41cf-b378-729b6f462d94.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/e909de54-9f02-445c-a657-8417732413e8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/e909de54-9f02-445c-a657-8417732413e8.png)

obj. style. color 변경하면 색상 바뀜

# event

브라우저에서 일어나는 모든 반응

- **event 종류 찾기**

① google 검색: (tag-name) html element mdn

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/b994b3b4-4722-44f7-9384-b589539ee2d6.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/b994b3b4-4722-44f7-9384-b589539ee2d6.png)

② console.dir 통해 el 출력 후, on~ 인 prop 찾기

on을 떼고 뒤가 event 명이다

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/03ff1bc8-8cc7-4ed2-91d0-0292f516871e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/03ff1bc8-8cc7-4ed2-91d0-0292f516871e.png)

- **mouseenter**: 마우스 올림
- **mouseleave**: 마우스 떠남
- **contextmenu**: 마우스 우클릭 시, context menu가 사용자의 화면에 보여지기 전에 작동
- **click**: 클릭
- **auxclick** : 우클릭
- **dblclick** : 더블 클릭
- **resize** : 사이즈 조정
- **copy** : 복사 / paste: 붙여넣기
- **online** : wifi 연결 / offline: wifi 연결x
- **wheel** : 사용자가 휠을 작동시킬 때 작동
- **mouseup** : 마우스 클릭 유지 시
    
    **mousedown** : 클릭 유지를 풀었을 때
    
- **submit** : input에 내용 작성 후, enter | button 클릭

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/9d407247-27de-47e4-8f15-174d9763e3e4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/9d407247-27de-47e4-8f15-174d9763e3e4.png)

↳ 이렇게 복합적으로 fnc 줄 수 있음!

- **event 시, 동작시키는 방법**
    
    
    1.  fnc > **addEventListener**

`function fnc-name(argument) {명령문;}`

`obj.addEventListener("event-name", fnc-name)`

- fnc-name 옆에 () X→ fnc의 실행권을 js에게 넘김
- `.removeEventListener` 사용 가능해서 추천

★ event로 얻는 값(event **object)**

- **obj 이고 많은 event의 정보를 prop로 갖고 있음**
- fnc에 argument로 전달됨 (기본동작이 있는 경우, preventDefault 해야 얻음)

ex) submit: SubmitEvent (입력값 아님, 그건 value)

click: MouseEvent / PointerEvent

- 실행 과정

① obj에 “event” 가 일어남 → fnc 실행

② event로부터 얻은 정보를 fnc의 첫번째 argument로 전달

③ 명령문 실행

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/04bc3463-4443-4b54-af0d-2fed04e0831c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/04bc3463-4443-4b54-af0d-2fed04e0831c.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/19a355a1-f4ed-49e6-b07b-490c61b8b78e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/1ee8946e1ebd4ed0bc1abd974af2bc6c/19a355a1-f4ed-49e6-b07b-490c61b8b78e.png)

+ event에서 얻는 값이 없거나, argument가 비어있을 때

: 그냥 실행

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/86048919-5b8a-4f65-98c0-0f4d538788a4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/86048919-5b8a-4f65-98c0-0f4d538788a4.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/b83ecc27-7cf9-4aa2-874a-8d5241cb82c6.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/b83ecc27-7cf9-4aa2-874a-8d5241cb82c6.png)

↳ click 시, 색깔 변경

2. on(event) prop 직접적으로 변경

`obj.**on(event)** = fnc-name;`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/f4c5d9ee-69fb-48b7-9c90-214b708ada9a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/f4c5d9ee-69fb-48b7-9c90-214b708ada9a.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/97ffe135-989b-4c3c-9a71-25e457586ef4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/97ffe135-989b-4c3c-9a71-25e457586ef4.png)

둘은 똑같이 기능한다

- —————————————————————————————————

# window

- 기본적으로 제공되는 var
- 화면 전체를 뜻함

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/b47181de-85fe-4a4d-90c7-7ae177caa2fd.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/b47181de-85fe-4a4d-90c7-7ae177caa2fd.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/8a8471cd-54fa-4cc7-ae27-57c08b057a85.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/8a8471cd-54fa-4cc7-ae27-57c08b057a85.png)

↳ 화면 크기를 줄이니, background-color 변화

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/41bc6bd0-7802-4fab-8175-7777c68d6a3f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/41bc6bd0-7802-4fab-8175-7777c68d6a3f.png)

↳ 이런식으로 다양하게 효과줄 수 있음

- —————————————————————————————————

# 조건에 따라 실행하는 fnc

`function fnc-name() {`

- `*if** (condition) {명령문;}`
- `*else if** (condition) {명령문;}`
- `*else** {명령문;}`

`}`

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/44488659-c6a2-47c9-8257-428bf28f5bbe.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/44488659-c6a2-47c9-8257-428bf28f5bbe.png)

- **코드 개선**

하나의 el이 여러 의미로 사용되고 중복됨

→ var로 구분해서 의미 파악 가능하게 해야 함

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/39e4f453-4bda-4bdc-86a0-6a1985bcb894.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/39e4f453-4bda-4bdc-86a0-6a1985bcb894.png)

① 조건문 el (원래 상태) → const 할당 (currentColor)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/05fba219-df30-4715-81bf-da13be744dbf.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/05fba219-df30-4715-81bf-da13be744dbf.png)

②변경 el → let 비어있는 변수 (newColor)

**Q**. newColor = h1.style.color; 아닌 이유

초반에 currentColor에 현재 색상 값을 저장, 그리고 newColor라는 빈 let변수를 선언

if, else를 거치면서 초기화 값을 할당받음. 즉, newColor = “tomato”;

그리고 그 값을 h1에 넣어주는 것이기 때문에

h1.style.color = newColor;가 되는 것!

- ——————————————————————————————————–

# **CSS & HTML & JS 연결**

html을 통해 css & js 연결하기

★ js에서 html 수정 → css는 html 보고 실행

(직접적으로 연결x / 코드 짧아져서 훨씬 효율적)

# 1. classname(prop) 이용

`obj.**classname** = "class-name";`

- **단일적 움직임**

(css) 기본 class + 변경 class 생성

(js) fnc가 ‘변경 class’ 입력하게 설정, event에 기능하는 방식

(css)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/f0798149-e09b-4644-979f-e540737be8e2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/f0798149-e09b-4644-979f-e540737be8e2.png)

(js)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/a08b1a20-ebac-456a-9ea3-096de59f88a1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/a08b1a20-ebac-456a-9ea3-096de59f88a1.png)

event(click)시, 실행하는 fnc 명령문에 class 생성 지시

→ tag가 class 가지게 되어 (css).class의 속성 실행

- **반복적인 동작 만들기**

condition 이용해서 class 줬다·뺐다 하는 fnc 제작

(위 코드에서 h1.className = getter & setter

∴ 현재 값 알 수 있으면서, 변경도 가능하니까)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/9736d72c-5532-4d50-8ff8-8bd1d42fa89c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/9736d72c-5532-4d50-8ff8-8bd1d42fa89c.png)

클릭할 때마다 색깔이 바뀜

[https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/cf74e387fe0d4abca62153b8b0eec072/abfd846e-27e4-4329-a140-a543e29b1e77.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/cf74e387fe0d4abca62153b8b0eec072/abfd846e-27e4-4329-a140-a543e29b1e77.webm)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/7e1d5698-95f4-4b7c-a3a7-0b255bf53a89.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/7e1d5698-95f4-4b7c-a3a7-0b255bf53a89.png)

transtion도 줄 수 있음 (색깔이 0.5초동안 바뀜)

- **오류 줄이기**

css에서 따오는 부분 (=raw value) 이 많을수록 오류 확률↑

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/132ce909-dd88-425e-8056-ef71e26c883e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/132ce909-dd88-425e-8056-ef71e26c883e.png)

이 부분 오타나고 실행 안 되도 console에서 이유 안나옴

∴ js가 아니라 css 에서 문제가 발생하니까!

js가 classname 바꿈(문제x)

→ html 에서 classname 바뀜(문제x)

→ css에서 오타 난 class니까 적용 안됨 (문제 발생!)

- **해결 방법**

css에서 따오는 부분 (=raw value)에 var 할당

한 부분만 수정하면 되니까, 오류 발생 부분 축소

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/b9abd45a-aab3-40cb-b2df-ee2114d51ac4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/b9abd45a-aab3-40cb-b2df-ee2114d51ac4.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/eb05df8c-f532-4f8a-b003-b2365f404127.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/eb05df8c-f532-4f8a-b003-b2365f404127.png)

↳ 오류가 나면 알 수 있다

- **단점**

원래 html에 class가 있는 상태라면, 아예 사라져버림

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/5492d541-1ec2-41d3-bbc1-7ed2aae28f8d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/5492d541-1ec2-41d3-bbc1-7ed2aae28f8d.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/e9dce75d-9737-43a4-8727-9db5fc507290.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/e9dce75d-9737-43a4-8727-9db5fc507290.png)

원래 sexy-font (폰트를 가진) 라는 class 보유

[https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/cf74e387fe0d4abca62153b8b0eec072/779d619b-8bd8-40eb-a673-6f24a709238e.webm](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/clip_videos/cf74e387fe0d4abca62153b8b0eec072/779d619b-8bd8-40eb-a673-6f24a709238e.webm)

실행하면 원래의 class 아예 사라지고

clicked 만 생겼다 없어졌다 반복

원래의 class 유지하면서, clicked 라는 class 추가하려면?

→ classList 이용

# 2. classList(obj/prop) 이용

class를 목록으로 작업할 수 있다

원래 html에서 가지고 있던 class 보존

- **classList의 fnc**

① `classList.**contains**(~)`

class 중에 ~을 포함하고 있는지 확인 (boolean)

② `classList.**remove**(~)`

class 중에 ~을 삭제

③ `classList.**add**(~)`

class에 ~을 추가

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/6ea826d8-1048-49d7-b2a2-87d0eb5d9a8d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/6ea826d8-1048-49d7-b2a2-87d0eb5d9a8d.png)

위 3개의 fnc 이용해서 똑같은 움직임 만듬

# 3. toggle(fnc) 이용

`classList.**toggle**(~)`

- class 안에 ~ 있으면 제거/ 없으면 생성
- 최고로 효율적!

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/f353f860-fc2c-42da-a834-cefa6092289a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/cf74e387fe0d4abca62153b8b0eec072/f353f860-fc2c-42da-a834-cefa6092289a.png)

이 다섯 줄의 코드를

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/372d80ed-eb1c-4966-90d3-ad5d52afb7a1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/cf74e387fe0d4abca62153b8b0eec072/372d80ed-eb1c-4966-90d3-ad5d52afb7a1.png)

한 줄로 줄일 수 있다.

raw value 중복하지 않으니, var 할당 할 필요도 없음