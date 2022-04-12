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

# **Date 객체**

## 객체 생성

인수에 따라 결과값이 달라짐

- `**new Date()`**
    
    현재 요일/ 월/ 일/ 년/ 시:분:초/ 위치
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/e3c995bd4d8c459cacd5026f8d2cf4f1/8562a51d-498f-4be4-9d6f-b19c4f1d4642.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/e3c995bd4d8c459cacd5026f8d2cf4f1/8562a51d-498f-4be4-9d6f-b19c4f1d4642.png)
    
- `**new Date(timestamp)**`
    - `timestamp`(타임스탬프) : 1970년 1월 1일 0시 0분 0초(UTO+0)을 기준으로 흘러간 밀리초(1/1000 초)를 나타내는 정수
    - 1970년 첫날에서 타임스탬프 이후 시점의 `Date`객체가 반환
    - 음수는 이전 날짜를 반환
    
    ```jsx
    // 1970년 1월 1일 0시 0분 0초(UTC+0)를 나타내는 객체
    let Jan01_1970 = new Date(0);
    
    // 1970년 1월 1일의 24시간 후는 1970년 1월 2일(UTC+0)임
    // 24시간 = 24 * 3600(60분 60초) * 1000 (밀리초*1000=1초)
    let Jan02_1970 = new Date(24 * 3600 * 1000);
    
    // 31 Dec 1969
    let Dec31_1969 = new Date(-24 * 3600 * 1000);
    ```
    
- `**new date(datestring)**`
    
    `Date.parse`의 알고리즘이 적용되어 문자열이 자동으로 구문 분석되어 객체가 반환
    
    ```jsx
    let date = new Date("2017-01-26");
    alert(date);
    // 인수로 시간은 지정하지 않았기 때문에 GMT 자정이라고 가정하고
    // 코드가 실행되는 시간대(timezone)에 따라 출력 문자열이 바뀝니다.
    // 따라서 얼럿 창엔
    // Thu Jan 26 2017 11:00:00 GMT+1100 (Australian Eastern Daylight Time)
    // 혹은
    // Wed Jan 25 2017 16:00:00 GMT-0800 (Pacific Standard Time)등이 출력됩니다.
    ```
    
- **`new Date(year, month, date, hours, minutes, seconds, ms)`**
    
    주어진 인수를 조합해 만들 수 있는 날짜가 저장된 객체가 반환(지역 시간대 기준)
    
    - 인수 (year, month만 필수)
    • `year` : 반드시 네 자리 숫자
    • `month` :  `0`(1월)부터 `11`(12월) 사이의 숫자
    • `date` : 값이 없는 경우엔 1일로 처리
    • `hours/minutes/seconds/ms` : 값이 없는 경우엔 `0`으로 처리 최소 정밀도는 밀리초(1/1000초)
    
    ```jsx
    new Date(2011, 0, 1, 0, 0, 0, 0); // 2011년 1월 1일, 00시 00분 00초
    new Date(2011, 0, 1); // hours를 비롯한 인수는 기본값이 0이므로 위와 동일
    
    // 2011년 1월 1일, 02시 03분 04.567초
    let date = new Date(2011, 0, 1, 2, 3, 4, 567);
    ```
    

## 날짜 구성요소 얻기

`new Date().get메서드`

- `getFullYear()`  년도(네 자릿수)
- `getMonth()`  월 (0~11)
- `getDay()`  요일을 나타내는 숫자 0~6 ( 0 = 일요일)
- `getDate()`  일
- `getHours()`  시간
- `getMinutes()`  분
- `getSecond()`  초
- `getMilliseconds()`  밀리초
- `date.now`
    
    1970년 1월 1일 00:00:00 UTC로부터 지난 시간을 밀리초 단위의 숫자 값으로 반환. 윤초는 무시함.
    

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
- `Math.trunc()`  소수부를 무시 (IE에서 지원X)

( `toFixed(n)`소수점 n번째 수까지 어림수를 구한 후, 문자형으로 반환)

- `Math.random()`  0과 1 사이의 난수를 반환
- `Math.max()` / `Math.min()`  인수 중 최대/최솟값 반환
- `Math.pow(n, power)`  n을 power번 거듭제곱한 값 반환
- `Math.abs(n)` n의 절대값 반환
- `Math.sqrt(x)`  주어진 숫자에 루트(**√** )를 씌운 수 반환
    
    만약 숫자가 음수이면 `NaN` 반환
    

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