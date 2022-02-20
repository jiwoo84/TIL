# weather

[→ Open in Slid](https://slid.cc/docs/c8d5399ff54047bdaf4446f1f27d60e6)

---

# geolocation

`navigator.geolocation.getCurrentPosition(성공fnc-name, 실패fnc-name)`

(현재 위치를 불러오기 성공 시, 실행할 fnc / 실패 시, fnc 입력)

- 사용자가 원할 경우 웹 애플리케이션에 위치 정보를 제공할 수 있는 API
- 실행되기 전에 권한에 대한 알림 뜸
- 성공 시, GeolocationPosition (위치 좌표 obj) 발생 → 성공fnc에 arg로 전달
- `arg.coords.latitude;`  위도
    
    `arg.coords.longitude;`  경도
    

```jsx
function onGeoOk(position) {
  const lat = position.coords.latitude;
  const lon = position.coords.longitude;
	console.log("you live in ", lat, lon);
}

function onGeoError() {
  alert("error");
}

navigator.geolocation.getCurrentPosition(onGeoOk, onGeoError);
```

![성공하면 console 화면](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/c8d5399ff54047bdaf4446f1f27d60e6/d1c30317-4fed-41ea-b202-0881c69a2d12.png)

성공하면 console 화면

# API 사용법

## 1. API url 준비

- 불러오면 정보 obj 가져옴
- 예시
    
    [weather API 받기](http://openweathermap.org/) : openweathermap.org
    
    (내 API_KEY: 9fa4320ce0f2af5804626dcb41e2a97e )
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/c8d5399ff54047bdaf4446f1f27d60e6/0b150870-8728-462f-af03-69c40b3e5619.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/c8d5399ff54047bdaf4446f1f27d60e6/0b150870-8728-462f-af03-69c40b3e5619.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/c8d5399ff54047bdaf4446f1f27d60e6/807b8bfe-1d62-4538-96be-52ac4eac3bde.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/c8d5399ff54047bdaf4446f1f27d60e6/807b8bfe-1d62-4538-96be-52ac4eac3bde.png)
    

## 2. (js) fetch API

- `fetch(url)` : url의 obj를 js로 가져온다
- promise이고 불러오는데 시간이 걸림 (서버의 응답 기다림)
- `.then` 을 사용하여 다음 행동 지정
- 자세히 배우지 않은 영역이라 추후 추가

```jsx
function onGeoOk(position) {
  const API_KEY = "9fa4320ce0f2af5804626dcb41e2a97e";
  const lat = position.coords.latitude;
  const lon = position.coords.longitude;
  const url = `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${API_KEY}&units=metric`;
  fetch(url)
    .then((response) => response.json())
    .then((data) => {
      const weather = data.weather[0].main;
			const temperature = data.main.temp;
      const city = data.name;
      console.log(`${city} ${weather} ${temperature}`;
			// seoul clouds 16  이렇게 출력
    });
}
```