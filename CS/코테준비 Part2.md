# 코테준비 Part2

## 1. 그리디

### 거스름돈

500, 100, 50, 10 원짜리 동전이 무한히 있을 경우, 금액 n을 거슬러 주기 위해 필요한 최소한의 동전 개수를 구하라.

```jsx
function solution(n) {

  let count = 0;

  let coin = [500, 100, 50, 10];

  coin.forEach((e) => {
    count += parseInt(n / e);
    n = n % e;
  });

  return count;
}
```

```jsx
function solution(n) {

  let count = 0;

  let coin = [500, 100, 50, 10];

  for (let i = 0; i < 4; i++) {
    count += parseInt(n / coin[i]);
    n = n % coin[i];
    if (n === 0) break;
	}

  return count;
}
```

- 시간복잡도 : O(n)

### 큰 수의 법칙

```jsx
function solution(n, m, k, arr) {

  arr.sort((a, b) => b - a);

  let sum = 0;
  let count = 0;

  for (let i = 1; i <= m; i++) {
    if (i % (k + 1) === 0) {
      sum += arr[1];
      count++;
    } else {
      sum += arr[0];
      count++;
    }
  }
  return sum;
}
```

```jsx
function solution(n, m, k, arr) {
  
  arr.sort((a, b) => b - a);

  let sum = 0;

  let count = parseInt(m / (k + 1)) * k + (m % (k + 1));
  return arr[0] * count + arr[1] * (m - count);
}
```

### 숫자 카드 게임

```jsx
function solution(n, m, arr) {

  let arrMin = arr.map((e, i) => Math.min.apply(null, arr[i]));

  return Math.max.apply(null, arrMin);
}
```

### 1이 될 때까지

```jsx
while (n !== 1) {
    if (n % k === 0) {
      n = n / k;
      count++;
    } else {
      n--;
      count++;
    }
  }
  return count;
}
```

## 2. 구현

### 상하좌우

NxN 정사각형의 출발점이 (1,1)일 때, 주어진 배열을 따라 이동한 결과 반환

- 차례대로 시뮬레이션하는 과정을 구현해야함

```jsx
function solution(n, arr) {
 
  let pos = [1, 1];

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === "L") {
      pos[1] -= 1;
      if (pos[1] < 1) pos[1] = 1;
    } else if (arr[i] === "R") {
      pos[1] += 1;
      if (pos[1] > n) pos[1] = n;
    } else if (arr[i] === "U") {
      pos[0] -= 1;
      if (pos[0] < 1) pos[0] = 1;
    } else if (arr[i] === "D") {
      pos[0] += 1;
      if (pos[0] > n) pos[0] = n;
    }
  }
  return pos;
}
```

### 시각

00:00:00 ~ N:59:59 중에서 3이 들어간 시간의 경우의 수 구하기

- 모든 경우의 수를 검색/ 100만 이하의 검색 ⇒ 완전 탐색

```jsx
function solution(n) {
  // 00:00:00 ~ N:59:59 중 3이 들어간 시간 경우의 수

  // N:ab:cd
  // 자리당 경우의 수 : a-6; b-10; c-6; d-10

  // 모든 경우의 수 - 3이 하나라도 든 경우의 수
  //  모든 경우의 수 = (n+1) * 6*10*6*10
  //  3이 하나라도 든 경우의 수
  //    1. n < 3 => (n+1)*5*9*5*9
  //    2. 3<= n <13 => n*5*9*5*9
  //    3. 13=< n <23 => n-1*5*9*5*9
  //    4. n=23 => n-2*5*9*5*9

  if (n < 3) return (n + 1) * 6 * 10 * 6 * 10 - (n + 1) * 5 * 9 * 5 * 9;
  else if (n >= 3 && n < 13)
    return (n + 1) * 6 * 10 * 6 * 10 - n * 5 * 9 * 5 * 9;
  else if (n >= 13 && n < 23)
    return (n + 1) * 6 * 10 * 6 * 10 - (n - 1) * 5 * 9 * 5 * 9;
  else if (n === 23) return (n + 1) * 6 * 10 * 6 * 10 - (n - 2) * 5 * 9 * 5 * 9;

  //   if (n < 3) {
  //     return (n + 1) * 1920;
  //   }
  //   return n * 1920 + 600;
}
```

```jsx
function solution(n) {
  // 00:00:00 ~ N:59:59 중 3이 들어간 시간 경우의 수

  let count = 0;

  for (let i = 0; i <= n; i++) {
    for (let j = 0; j < 60; j++) {
      for (let k = 0; k < 60; k++) {
        let timeStr = `${i}${j}${k}`;

        if (timeStr.includes(3)) count++;
      }
    }
  }
  return count;
}
```

### 왕실의 나이트

```jsx
function solution(input) {
  // 8 x 8 좌표 평면
  // 행 : a~h / 열 : 1~8
  // 수평으로 두칸 -> 수진 한칸 / 수직 두칸 -> 수평 한칸 가능
  // 이동 가능한 경우의 수 반환

  let column = ["a", "b", "c", "d", "e", "f", "g", "h"];
  let posColumn = [column.indexOf(input[0]) + 1, +input[1]];

  let move = [
    [2, 1],
    [2, -1],
    [-2, 1],
    [-2, -1],
    [1, 2],
    [1, -2],
    [-1, 2],
    [-1, -2],
  ];
  let count = 0;

  for (let i = 0; i < move.length; i++) {
    let moveColumn = position[0] + move[i][0];
    let moveRow = position[1] + move[i][1];

    if (moveColumn < 1 || moveColumn > 8 || moveRow < 1 || moveRow > 8)
      continue;
    else count++;
  }
  return count;
}
```

```jsx
function solution(input) {
  // 8 x 8 좌표 평면
  // 행 : a~h / 열 : 1~8
  // 수평으로 두칸 -> 수진 한칸 / 수직 두칸 -> 수평 한칸 가능
  // 이동 가능한 경우의 수 반환

  let column = ["a", "b", "c", "d", "e", "f", "g", "h"];
  let posColumn = column.indexOf(input[0]) + 1;
  let posRow = +input[1];

  let move = [
    [2, 1],
    [2, -1],
    [-2, 1],
    [-2, -1],
    [1, 2],
    [1, -2],
    [-1, 2],
    [-1, -2],
  ];
  let count = 0;

  for (let i = 0; i < move.length; i++) {
    let moveColumn = posColumn + move[i][0];
    let moveRow = posRow + move[i][1];

    if (moveColumn < 1 || moveColumn > 8 || moveRow < 1 || moveRow > 8)
      continue;
    else count++;
  }
  return count;
}
```