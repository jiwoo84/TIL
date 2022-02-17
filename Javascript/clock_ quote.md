# clock_ quote

[→ Open in Slid](https://slid.cc/docs/e3c995bd4d8c459cacd5026f8d2cf4f1)

---

## **setInterval**

`setInterval (fnc, n(ms))`

fnc이 n(ms)마다 실행 (1000ms = 1s(초))

## **setTimeout**

`setTimeout (fnc, ~(ms))`

fnc이 n(ms) 후에 실행 (1번)

## **padStart / padEnd**

`~.padStart(n,…)` / `~.padEnd(n,…)`

~(string)이 n자리가 안된다면 앞/뒤에 …(string) 추가

- string 만 가능

```jsx
"1".padstart(2,"0");  // "01"
"hello".padEnd(10,"x");  // "helloxxxxx"
```

# 시간

## **Date**

- `new Date()`  현재 요일/ 월/ 일/ 년/ 시:분:초/ 위치
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/e3c995bd4d8c459cacd5026f8d2cf4f1/8562a51d-498f-4be4-9d6f-b19c4f1d4642.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/e3c995bd4d8c459cacd5026f8d2cf4f1/8562a51d-498f-4be4-9d6f-b19c4f1d4642.png)
    
- `new Date().getDate()`  일
- `new Date().getDay()`  요일 ( 0 = 일요일)
- `new Date().getFullYear()`  년도
- `new Date().getHours()`  시간
- `new Date().getMinutes()`  분
- `new Date().getSecond()`  초

## **시:분:초 출력**

(`const date = new Date();`)

``${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`;`

```jsx
const clock = document.querySelector("#clock");

function getClock() {
  const date = new Date();
  clock.innerText = `${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`;
}

getClock(); // 안 써주면 새로고침하고 1초 후에 시간 뜬다
setInterval(getClock, 1000);
```

- **00:00:00 형태로 시간 출력**
    
    ```jsx
    const date = new Date();
    const hours = String(date.getHours()).padStart(2, "0");
    const minutes = String(date.getMinutes()).padStart(2, "0");
    const seconds = String(date.getSeconds()).padStart(2, "0");
    clock.innerText = `${hours}:${minutes}:${seconds}`;
    ```
    
    `date.getHours()`이 num이기 때문에 string으로 변환 후, padstart 적용
    

# Math

수학적인 상수와 함수를 위한 속성과 메서드를 가진 내장 객체

## 종류

- `Math.random()`   0 과 1 사이 랜덤한 소수
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/e3c995bd4d8c459cacd5026f8d2cf4f1/e92cc8f0-b9f6-4957-923f-f5db5eb03179.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/e3c995bd4d8c459cacd5026f8d2cf4f1/e92cc8f0-b9f6-4957-923f-f5db5eb03179.png)
    
- `Math.round()`  숫자를 반올림
- `Math.ceil()` 숫자를 올림
- `Math.floor()`  숫자를 내림

## **랜덤 정수(integer) 얻기**

( `Math.random() * n`  0과 n사이의 소수를 반환 )

`Math.floor(Math.random() * n)`   0과 n사이의 정수를 반환

- 0 ~ n-1 의 숫자를 반환 ( 0, 1, …, n-1)

- **사용 예시**
    - array 값 랜덤 호출
        
        `array[Math.floor(Math.random() * quotes.length)];`
        
        array의 n번째 값 호출 위해서는 n-1 써야하므로 랜덤정수 그대로 사용
        
    
    ```html
    <div id="quote">
          <span></span>
          <span></span>
        </div>
    ```
    
    ```jsx
    const quotes = [
      {
        quote: "Pizza is delicious.",
        author: "jiwoo",
      },
      {
        quote: "life is irony.",
        author: "namjun",
      },
      {
        quote: "Today's dinner is kimbap.",
        author: "mom",
      },
    ];
    
    const quote = document.querySelector("#quote span:first-child");
    const author = document.querySelector("#quote span:last-child");
    
    const todayQuote = quotes[Math.floor(Math.random() * quotes.length)];
    // math 이용해서 array의 값 랜덤하게 호출
    
    quote.innerText = todayQuote.quote;
    author.innerText = todayQuote.author;
    ```
    

---

# js에서 node 추가

## **createElement**

`document.createElement("tag")`

지정한 `tagName`의 HTML 요소를 만들어 반환

js상에 el 생성 (html에 생성 X / 브라우저에 표시 X)

- 변수 할당 한다면 var은 추가된 tag를 뜻함
    
    `const img = document.createElement("img")`
    
    ∴ `console.log(img)`  = <img>
    
- tag에 필수 attribute가 있다면, 추가해 줄 것
    
    ex) img : `img(obj).src = "00.jpg"`
    

## **appendChild / prepend**

node를 해당 node의 자식으로 추가 (부모의 맨 끝에/ 맨 앞)

`element.appendChild(추가할el)`

### 예시

```jsx
const bgImage = document.createElement("img");

bgImage.src = `img/0.jpg`;

document.body.appendChild(bgImage);
```

![body 맨 끝에 <img> 추가되어 있음](clock_%20quo%20413d1/Untitled.png)

body 맨 끝에 <img> 추가되어 있음