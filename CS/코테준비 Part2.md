# 이것이코테다 Part2

## 1. 그리디

### 3-1 거스름돈

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

```