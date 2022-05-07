# 코테준비 Part2

## 순열 & 조합

- **조합**
    
    n개 중에서 m개를 선택하는 경우의 수 (nCr = n개 중 r개의 combination)
    
    조합은 순서 상관 없음 ⇒ [1,2] & [2,1]은 같은 것으로 취급
    
    - ex) Input: [1, 2, 3, 4]
        
        Output: [ [1, 2, 3], [1, 2, 4], [1, 3, 4], [2, 3, 4] ] 
        
    - 코드 원리
        
        ```jsx
        시작
          1을 선택(고정)하고 -> 나머지 [2, 3, 4] 중에서 2개씩 조합을 구한다.
          [1, 2, 3] [1, 2, 4] [1, 3, 4]
          2를 선택(고정)하고 -> 나머지 [3, 4] 중에서 2개씩 조합을 구한다.
          [2, 3, 4]
          3을 선택(고정)하고 -> 나머지 [4] 중에서 2개씩 조합을 구한다. 
          [] 
          4을 선택(고정)하고 -> 나머지 [] 중에서 2개씩 조합을 구한다.
          []
        종료
        ```
        
    - 코드
        
        ```jsx
        function permutation(arr, selectNum) {
        
        	const result = []; // 1
        	if (selectNum === 1) return arr.map(v => [v]); // 1. 재귀 종료 조건: 1개 고르면 바로 요소담은 배열 반환
        
        	arr.forEach((v, idx, arr) => {
        		const fixed = v; // 숫자 하나 고정
        		const restArr = arr.slice(index + 1); // 2. 해당하는 fixed를 제외한 나머지 뒤
        		const restPermutations = permutation(restArr, selectNum - 1); // 3. 나머지에 대해서 조합을 구한다.
        		const combineFixed = restPermutations.map(v => [fixed, ...v]); // 4. 조합에 떼 놓은(fixed) 값 붙이기
        		result.push(...combineFixed); // 5. result에 값 추가
        	});
        	return result;
           // 재귀가 진행중이면 해당 값이 restPermutations의 반환값이 되어 combineFixed를 통해 fixed와 결합함
        }
        
        console.log(permutation([1,1,7]));
        // [[1, 1], [1, 7], [1, 1], [1, 7], [7, 1], [7, 1]]
        ```
        
        1. 원소 1개의 조합을 구한다고 하면 바로 요소 하나씩 배열로 만들어서 return
            
            ex) `arr = [1,2,3,4]` / `selectNumber = 1` ⇒ return `[[1], [2], [3], [4]]`
            
        2. 맨 첫번째 값부터 선택됨 (선택값 = fixed) → rest = fixed 뒤부터 맨끝까지의 배열
            
            ex) `arr = [1,2,3,4]` / `fixed = 1` (맨 처음 순회라면) / `rest = [2,3,4]`
            
        3. 재귀함수 호출
            
            코드가 어떻게 실행될지 모르겠다면, 재귀가 종료조건을 만났을 때 반환값이 무엇일지 계산하고 이를 바탕으로 읽으면 된다
            
            위 코드는 맨 마지막에 selectNumber = 1 이면 반환값은 [[3], [4]]가 되고 다음 코드 진행
            
        4. 차곡차곡 result 배열에 반환값이 쌓임
            
            (재귀함수가 호출되면서 result가 재선언되지만, 그건 재귀함수 안에서고 바깥 함수에는 영향을 미치지 않는다)
            
- **순열**
    
    순열은 조합에서 순서까지 신경 쓴 것이다. 고로 `nCr x 3!` ( n! ⇒  n x (n-1) x ... x 1)
    
    - 코드 원리
        
        ```jsx
        1(fixed) => permutation([2, 3, 4]) => 2(fixed) => permutation([3, 4]) => ...
        2(fixed) => permutation([1, 3, 4])
        3(fixed) => permutation([1, 2, 4])
        4(fixed) => permutation([1, 2, 3])
        ```
        
        조합과 다른 점은 배열의 처음부터 선택(고정)하면서 나머지 배열을 구할 때 고정된 값 뒤에 있는 값들에 대해서 순열을 구하는게 아니라, 고정된 값을 제외한 모든 원소에 대해서 순열을 구해야 한다는 것이다.
        
        조합 코드에서 나머지 배열을 구하는 코드만 다음과 같이 바꾸면 된다.
        
        `const rest = [...origin.slice(0, index), ...origin.slice(index+1)] // 해당하는 fixed를 제외한 나머지 배열`
        
    - 코드 구현
        
         `rest`를 나를 제외한 모든 요소를 표함한 배열로 만들어주면 된다
        
        ```jsx
        function permutation(arr, selectNum) {
        
        	const result = [];
        	if (selectNum === 1) return arr.map(v => [v]); // 재귀 종료 조건: 1개 고르면 바로 요소담은 배열 반환
        
        	arr.forEach((v, idx, arr) => {
        		const fixed = v; // 숫자 하나 고정
        		const restArr = arr.filter((e, index) => index !== idx); // fixed를 제외한 나머지 배열 생성
        		const restPermutations = permutation(restArr, selectNum - 1);
        		const combineFixed = restPermutations.map(v => [fixed, ...v]); // 구한 순열에 fixed 붙이기
        		result.push(...combineFixed); // result에 순열 추가
        	});
        	return result;
           // 재귀가 진행중이면 해당 값이 restPermutations의 반환값이 되어 combineFixed를 통해 fixed와 결합함
        }
        ```
        
        [참고링크](https://pul8219.github.io/algorithm/algorithm-permutation-and-combination/)
        

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

```jsx
function solution(numbers) {
    
    let nums = numbers.split('');
    
    // 소수 판별
    function isPrime(num) {
        if(num <= 1) return false;
        for (let i = 2; i*i <= num; i++) {
            if (num % i === 0) return false;
        }
        return true;
    }
    
    // 순열 만들기
    function permutation(arr, selectNum) {

        const result = [];
        if (selectNum === 1) return arr.map(v => [v]); 

        arr.forEach((v, idx, arr) => {
            const fixed = v; // 숫자 하나 고정
            const restArr = arr.filter((e, index) => index !== idx); 
            const restPermutations = permutation(restArr, selectNum - 1);
            const combineFixed = restPermutations.map(v => [fixed, ...v]); 
            result.push(...combineFixed); 
        });
        return result;
       
        }

    let answer = permutation(nums, '');

    return answer.filter(e => isPrime(e)).length;

}ㅛ

```