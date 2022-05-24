# prog Lv.2

## 1. 그리디

(이것이 코딩테스트다 문제)

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

(프로그래머스 문제)

### 큰 수 만들기

어떤 숫자에서 k개의 수를 제거했을 때 얻을 수 있는 가장 큰 숫자를 구하려 합니다.

예를 들어, 숫자 1924에서 수 두 개를 제거하면 [19, 12, 14, 92, 94, 24] 를 만들 수 있습니다. 이 중 가장 큰 숫자는 94 입니다.

문자열 형식으로 숫자 number와 제거할 수의 개수 k가 solution 함수의 매개변수로 주어집니다. number에서 k 개의 수를 제거했을 때 만들 수 있는 수 중 가장 큰 숫자를 문자열 형태로 return 하도록 solution 함수를 완성하세요.

- 제한 조건
    - number는 2자리 이상, 1,000,000자리 이하인 숫자입니다.
    - k는 1 이상 `number의 자릿수` 미만인 자연수입니다.

```jsx
function solution(number, k) {
    // number에서 k개의 수 제거했을 때 얻기 가능한 최대의 수
    // = number에서 number.length - k개 선택하는 순열 배열 만들기
    // return 요소 중 가장 큰 수
    
    // 배열 answer = 순열 숫자 저장
    let answer = [];
    
    number = number.split('');
    
    // 함수 permutation
    function permutation(arr, selectNum) {
        
        let result = [];
        if(selectNum === 1) return arr.map(v => [v]);
        
        arr.forEach((v, idx, arr) => {
            let fixed = v;
            let restArr = arr.filter((v,index) => index !== idx);
            let permutationArr = permutation(restArr, selectNum -1);
            let combineArr = permutationArr.map(v => [fixed, ...v]);
            result.push(...combineArr);
        });
        return result;
    }
    
    // answer = permutation(number, number.length - k)
    answer = permutation(number, number.length - k).map(v => +v.join(''));
    
    // return Math.max(null, answer)
    return Math.max.apply(null, answer);
    
}
```

```jsx
function solution(number, k) {
    const stack = []; // 남은 숫자들이 저장될 스택
    
    for (let i = 0; i < number.length; i++) {
        
        let el = number[i]; // 현재 요소
        
        // 제거가능한 숫자 남아있음 && el이 스택 맨 위보다 클 때
        while(k > 0 && el > stack[stack.length-1]) {
            stack.pop(); // 맨 위 숫자 꺼냄
            k--; // 제거 숫자 하나 줄어듬
        }
        stack.push(el);
    }
    
    
    return stack.slice(0, number.length - k).join('');
}
```

### 구명보트

무인도에 갇힌 사람들을 구명보트를 이용하여 구출하려고 합니다. 구명보트는 작아서 한 번에 최대 **2명**씩 밖에 탈 수 없고, 무게 제한도 있습니다.

예를 들어, 사람들의 몸무게가 [70kg, 50kg, 80kg, 50kg]이고 구명보트의 무게 제한이 100kg이라면 2번째 사람과 4번째 사람은 같이 탈 수 있지만 1번째 사람과 3번째 사람의 무게의 합은 150kg이므로 구명보트의 무게 제한을 초과하여 같이 탈 수 없습니다.

구명보트를 최대한 적게 사용하여 모든 사람을 구출하려고 합니다.

사람들의 몸무게를 담은 배열 people과 구명보트의 무게 제한 limit가 매개변수로 주어질 때, 모든 사람을 구출하기 위해 필요한 구명보트 개수의 최솟값을 return 하도록 solution 함수를 작성해주세요.

- 제한사항
    - 무인도에 갇힌 사람은 1명 이상 50,000명 이하입니다.
    - 각 사람의 몸무게는 40kg 이상 240kg 이하입니다.
    - 구명보트의 무게 제한은 40kg 이상 240kg 이하입니다.
    - 구명보트의 무게 제한은 항상 사람들의 몸무게 중 최댓값보다 크게 주어지므로 사람들을 구출할 수 없는 경우는 없습니다.

```jsx
function solution(people, limit) {

    let count = 0;
    people.sort((a,b) => a - b);
    
    // while (people.length > 0)
    //  if : 최대 + 최소 <= limit -> 둘이 배열에서 뺌 -> count ++
    //  else : 최대만 뺌 -> count ++
    // return count;
    
    while (people.length > 0) {
        
        let min = people[0];
        let max = people[people.length - 1];
        
        if ((max+min) <= limit) {
            people.pop();
            people.shift();
            count++;
        }
        else {
            people.pop();
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

}

```

## 완전 탐색

### 소수찾기

```jsx
function solution(numbers) {
    // 숫자들로 조합을 만듬
    // 소수 검사해서 갯수 반환
    
    function isPrime(num) {
        if(num <= 1) return false;
        for(let i = 2; i*i <= num; i++) {
            if(num % i === 0) return false;
        }
        return true;
    }
    
    numbers = numbers.split('');
    
    function permutation(arr, selectNum) {
        
        let result = [];
        if(selectNum === 1) return arr.map(v => [v]);
        
        arr.forEach((v, idx, arr) => {
            let fixed = v;
            let restArr = arr.filter((e, index) => index !== idx);
            let restPermutations = permutation(restArr, selectNum - 1);
            let combineArr = restPermutations.map(e => [fixed, ...e]);
            result.push(...combineArr);
        })
        return result;
    }
    
    let answer = [];
    
    for(let i = 1; i <= numbers.length; i++) {
        let selectNums = permutation(numbers, i);
        selectNums.forEach(e => answer.push(+e.join('')));
        // 위 함수로 구한 배열 요소들 하나씩 answer에 추가
        // 그냥 추가하면 ["1","2"] 같은 형태로 추가되니 문자열로 변환(join) & 숫자로 변환(+)
        // 그래야 밑에 Set으로 중복 검사할때 정상적으로 수행됨
    }
    
    answer = [... new Set(answer)];
    // Set 객체로 만들어서 중복 제거 -> 값 하나씩 전달해서 다시 배열로 변환
    
    return answer.filter(v => isPrime(v)).length;
}
```

- 다른 답안
    
    ```jsx
    function solution(numbers) {
        var answer = [];
        let nums = numbers.split(''); 
        
        // 소수 판별
        const isPrimeNum = (num) => {
            if(num<=1) return false;
            for (let i = 2; i*i <= num; i++) {
                if (num % i === 0) return false;
            }
            return true;
        }
        
        // 순열 만들기
        const getPermutation = (arr, fixed) => {
            if(arr.length >= 1) {
                for (let i=0; i<arr.length; i++) {
                    const newNum = fixed + arr[i];
                    const copyArr = [...arr];
                    copyArr.splice(i, 1);
                    if (!answer.includes(+newNum) && isPrimeNum(+newNum)){
                        answer.push(+newNum) 
                    }
                    getPermutation(copyArr, newNum); 
                }
            }
        }
        
        getPermutation(nums, '');
        return answer.length;
    }
    ```
    

- 모범답안

```jsx
function solution(numbers) {
    var answer = 0;
    // numbers를 배열로 변환하고 내림차순으로 정렬
    let a = numbers.split('').sort((a,b)=>b-a);
    // 최댓값
    let N = Number(a.join(''));
    // 에라토스 테네스의 체로 소수 구하기
    let arr = makePrimeNum(N);
    
    for(let i=2; i<=N; i++){
        // 소수가 아니면 패스
        if(arr[i] == false) continue;
        // 소수면 해당 숫자를 문자열로 바꾸고 배열로 변환
        let temp = i.toString().split('');
        // numbers에 해당 하는 값을 돌면서 temp에도 있으면 temp에서 삭제
        for(let cn of a){
            let idx = temp.indexOf(cn);
            if(idx > -1) temp.splice(idx,1);
        }
        // temp.length가 0이면 numbers에 모두 있는 숫자 이므로 answer++
        if(temp.length == 0) answer++;
    }
    
    return answer;
}

//에라토스테네스의 체
function makePrimeNum(N){
    let arr = [];
    for(let i=2; i<=N; i++){
        if(arr[i] == false) continue;
        for(let k=i+i; k<=N; k+=i){
            arr[k] = false;
        }
    }
    return arr;
}
```

### 카펫

Leo는 카펫을 사러 갔다가 아래 그림과 같이 중앙에는 노란색으로 칠해져 있고 테두리 1줄은 갈색으로 칠해져 있는 격자 모양 카펫을 봤습니다.

Leo는 집으로 돌아와서 아까 본 카펫의 노란색과 갈색으로 색칠된 격자의 개수는 기억했지만, 전체 카펫의 크기는 기억하지 못했습니다.

Leo가 본 카펫에서 갈색 격자의 수 brown, 노란색 격자의 수 yellow가 매개변수로 주어질 때 카펫의 가로, 세로 크기를 순서대로 배열에 담아 return 하도록 solution 함수를 작성해주세요.

- 제한사항
    - 갈색 격자의 수 brown은 8 이상 5,000 이하인 자연수입니다.
    - 노란색 격자의 수 yellow는 1 이상 2,000,000 이하인 자연수입니다.
    - 카펫의 가로 길이는 세로 길이와 같거나, 세로 길이보다 깁니다.

```jsx
function solution(brown, yellow) {
    // 테두리 1줄 = brown / 중앙 = yellow
    // return 카펫의 길이 [가로, 세로] (가로 >= 세로)
    
    // brown + yellow = c x r (column <= row)
    // 경우의 수 중, (r-2)*(c-2) = yellow -> return [r,c]
    
    //for (c = 1 ~ brown제곱근)
    //  변수 r = brown/c
    //  if r정수인지 확인
    //      if (r-2)*(c-2) = yellow -> return [r,c]
    let arr = [];
    
    for (let c = 1; c <= Math.sqrt(brown + yellow); c++) {
        
        let r = (brown+yellow)/c;
        
        if ( r % 1 === 0) {
            if((r-2) * (c-2) === yellow) arr = [r,c];
        }
    }
    return arr;
}
```

```jsx
for (let c = 3; c <= (brown+yellow)/c; c++) {
        
        let r = (brown+yellow)/c;
        
        if((r-2) * (c-2) === yellow) return [r,c];
        }
    }
```

## 스택&큐

### 기능개발

프로그래머스 팀에서는 기능 개선 작업을 수행 중입니다. 각 기능은 진도가 100%일 때 서비스에 반영할 수 있습니다.

또, 각 기능의 개발속도는 모두 다르기 때문에 뒤에 있는 기능이 앞에 있는 기능보다 먼저 개발될 수 있고, 이때 뒤에 있는 기능은 앞에 있는 기능이 배포될 때 함께 배포됩니다.

먼저 배포되어야 하는 순서대로 작업의 진도가 적힌 정수 배열 progresses와 각 작업의 개발 속도가 적힌 정수 배열 speeds가 주어질 때 각 배포마다 몇 개의 기능이 배포되는지를 return 하도록 solution 함수를 완성하세요.

- 제한 사항
    - 작업의 개수(progresses, speeds배열의 길이)는 100개 이하입니다.
    - 작업 진도는 100 미만의 자연수입니다.
    - 작업 속도는 100 이하의 자연수입니다.
    - 배포는 하루에 한 번만 할 수 있으며, 하루의 끝에 이루어진다고 가정합니다. 예를 들어 진도율이 95%인 작업의 개발 속도가 하루에 4%라면 배포는 2일 뒤에 이루어집니다.

```jsx
function solution(progresses, speeds) {
    
    let answer = [];

    while (progresses.length > 0) { 
        
        let count = 0;
        progresses.forEach((v, idx) => progresses[idx] += speeds[idx]);
        
        while (progresses[0] >= 100) {
            progresses.shift();
            speeds.shift();
            count++;
        }
        
        if(count > 0) answer.push(count);
        
    }
    return answer;
}
```

### 프린터

```jsx
function solution(priorities, location) {

    let queue = priorities.map((v, idx) => [idx, v]);
    let answer = [];

    while (queue.length > 0) {

        let temp = queue.shift();

        if (queue.find(v => v[1] > temp[1])) {
            queue.push(temp);
        }
        else {
            answer.push(temp);
        }
    }
    return answer.indexOf(answer.find(v => v[0] === location)) + 1;
}
```

### 다리를 지나는 트럭

```jsx
function solution(bridge_length, weight, truck_weights) {

    let nowBridge = new Array(bridge_length).fill(0);
    let nowWeight = 0;
    let sec = 0;
    

    let firstTruck = truck_weights.shift();
    
    nowBridge.push(firstTruck);
    nowBridge.shift();
    nowWeight += firstTruck;
    sec++;
    
    while (nowWeight) {
        sec++;
        nowWeight -= nowBridge.shift();
        
        let nowTruck = truck_weights[0] ? truck_weights[0] : 0;
        
        if (nowWeight + nowTruck > weight) nowBridge.push(0);
        else {
            nowBridge.push(truck_weights.shift());
            nowWeight += nowTruck;
        }
    }
    return sec;
}
```

```jsx
function solution(bridge_length, weight, truck_weights) {
  let bridge = new Array(bridge_length).fill(0)
  let sec = 0;

  while (bridge.length) {
      
    bridge.shift(); 
    sec += 1;

    if (truck_weights.length) { // 대기 트럭 존재하면
        
      let totalWeight = bridge.reduce((sum, v) => sum + v, 0);

      if (totalWeight + truck_weights[0] <= weight) {
        bridge.push(truck_weights.shift());
      } else {
        bridge.push(0);
      }
    }
  }
  return sec;
}
```

## 정렬

### 가장 큰 수

```jsx
function solution(numbers) {
    numbers = numbers.map(v => String(v));
    numbers.sort((a,b) => {
        return (b + a) - (a + b); 
    })
    return numbers[0] === '0' ? '0' : numbers.join('');
}
```

### H-index

```jsx
function solution(citations) {

    citations.sort((a,b) => b - a);
    let answer = 0;

    for (let i = 0; i < citations.length; i++) {
        let citation = citations[i];
        if(citations.filter(v => v >= citation).length >= citation) {
            answer = citation;
            break;
        }
    }
    return answer;
}
```

## DFS / BFS

![Untitled](prog%20Lv%202%209cdc0f3cf8b841c0860e516219a8b32e/Untitled.png)

```jsx
const graph = {
  A: ['B', 'C'],
  B: ['A', 'D'],
  C: ['A', 'G', 'H', 'I'],
  D: ['B', 'E', 'F'],
  E: ['D'],
  F: ['D'],
  G: ['C'],
  H: ['C'],
  I: ['C', 'J'],
  J: ['I']
};
```

### BFS

```jsx
const BFS = (graph, startNode) => {
  const visited = []; // 탐색을 마친 노드들
  let needVisit = []; // 탐색해야할 노드들

  needVisit.push(startNode); // 노드 탐색 시작

  while (needVisit.length !== 0) { // 탐색해야할 노드가 남아있다면
    const node = needVisit.shift(); // queue이기 때문에 선입선출, shift()를 사용
    if (!visited.includes(node)) { // 해당 노드가 탐색된 적 없다면
      visited.push(node); 
      needVisit = [...needVisit, ...graph[node]];
    }
  }
  return visited;
};

console.log(BFS(graph, "A"));
// ["A", "B", "C", "D", "G", "H", "I", "E", "F", "J"]
```

### DFS

```jsx
const DFS = (graph, startNode) => {
  const visited = []; // 탐색을 마친 노드들
  let needVisit = []; // 탐색해야할 노드들

  needVisit.push(startNode); // 노드 탐색 시작

  while (needVisit.length !== 0) { // 탐색해야할 노드가 남아있다면
    const node = needVisit.shift(); // queue이기 때문에 선입선출, shift()를 사용한다.
    if (!visited.includes(node)) { // 해당 노드가 탐색된 적 없다면
      visited.push(node); 
      needVisit = [...graph[node], ...needVisit];
    }
  }
  return visited;
};

console.log(DFS(graph, "A"));
// ["A", "B", "D", "E", "F", "C", "G", "H", "I", "J"]
```

### 타켓넘버

```jsx
function solution(numbers, target) {
    let answer = 0;
    
    dfs(0,0);
    
    function dfs(level, sum) {
        if(level === numbers.length){
            if(sum === target){
                answer += 1;
            }
            return;
        }
        dfs(1,1)
        dfs(level + 1, sum + numbers[level]);
        dfs(level + 1, sum - numbers[level]);
    }
    return answer;
}
```

[설명](https://jjnooys.medium.com/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%ED%83%80%EA%B2%9F-%EB%84%98%EB%B2%84-javascript-1d7983d423b5)

### 위장

```jsx
function solution(clothes) {
    var answer = 1;
    var obj={};
    for(var i=0;i<clothes.length;i++){
        obj[clothes[i][1]]=(obj[clothes[i][1]] || 1) + 1;
    }

    for(var key in obj){
        answer *= obj[key];
    }
    
    return answer-1;
```

---

### 피보나치 수

```jsx
function solution(n) {

    function accF(m) {
        if(m < 2) return m;
        return accF(m-1) + accF(m-2);
    }
    
    return accF(n) % 1234567;
}
```

```jsx
function solution(n) {
    
    let arr = [0, 1];
    
    for (let i = 2; i <= n; i++) {
        arr.push((arr[i-1] + arr[i-2]) % 1234567);
    }
    return arr[n] ;
}
```

```jsx
function solution(arr) {
    // 배열 오름차순 정렬
    arr.sort((a,b) => a - b);
    
    // max = 제일 큰 숫자 pop해서 변수 할당
    let max = arr.pop();
    let temp = max;
    
    // 반복문 max배수 중, arr의 모든 요소로 나누어 떨어지는 수 return
    while(true) {
        
        for(let i = 0; i < arr.length; i++) {
            if(max % arr[i]) break;
            if(i === arr.length - 1) return temp;
        }
        temp += max; 
    }
}
```

### 모음사전

```jsx
function solution(word) {
    const words = ['A', 'E', 'I', 'O', 'U'];
    const dict = [];
    
    function getDict(word, dept) {
        
        if(dept === 6) return;
        dict.push(word);
        
        for(let nextWord of words) {
            getDict(word + nextWord, dept + 1);
        }
    }
    
    words.forEach((word) => getDict(word, 1));
    
    return dict.indexOf(word) + 1;
}
```

```jsx
function solution(word) {
    
    let answer = [];
    
    function dfs(p) {
        if (p.length > 5) return;

        answer.push(p);
        for (let w of "AEIOU") {
            dfs(p + w);
        }
    }

    dfs("");
    return answer.indexOf(word);
}
```

### 짝지어 제거하기

```jsx
function solution(s) {

    s = s.split('');
        
    for(let i = 0; i < s.length;) {
        if(s[i] === s[i+1]) {
            s.splice(i, 2);
            i = 0;
        }
        else i++;
    }
    
    return s.length ? 0 : 1;
}
```