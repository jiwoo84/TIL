# codingTest-keyPoint

- **자연수**
    
    1부터 무한히 증가하는 수 (1,2,3,4,5...) / 음수, 분수, 소수 미포함
    
- **정수**
    
    자연수와 비슷하지만 음수 포함 ( ... -2, -1, 0, 1, 2 ...) / 분수, 소수 미포함
    

# 순열 & 조합

[edwith 강의](https://www.edwith.org/sutudy/lecture/29037?isDesc=false)

## 📌경우의 수

### **순열**

n개 중에서 r개를 선택하는 경우의 수 (순서 상관 ㅇ)

(0! = 1)

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled.png)

- 중복순열 : 중복을 허용하여 r개 선택 ⇒ $n^r$

### **조합**

n개 중에서 r개를 선택하는 경우의 수 (순서 상관 x)

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%201.png)

⇒ $n! /(n-r)!*r!$

- 중복조합: 중복을 허용하여 r개 선택 ⇒ n+r-1Cr

### 같은 것이 있는 경우

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%202.png)

---

## 📝 구현

### 조합

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
    
    console.log(permutation([1,1,7], 2));
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
        

### **순열**

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
    

---

# DFS / BFS

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%203.png)

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

- 특정 노드의 서브트리는 탐색x

```jsx
function dfs(root,exception) {

    let count = 0;
    let queue = [root];
    let visit = []; // 방문 여부 체크 배열 (idx = root, 값 = 방문 여부)

    while(queue.length) {

        let cur = queue.shift();
        visit[cur] = true;
        count ++;

        obj[cur].forEach(child => {
            if(!visit[child] && child !== exception) {
                queue.push(child);
            }
        })
    }
    return count; // 노드 개수 반환
}
```

## 그래프

버텍스(정점) & 아크(노드 간 연결선)

 

### 구현 방식

1. 2차원 배열
    
    ![간단 but 메모리 큼](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%204.png)
    
    간단 but 메모리 큼
    
2. 연결 리스트
    
    ![복잡 bup 메모리 작음](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%205.png)
    
    복잡 bup 메모리 작음
    
- [디익스트라 알고리즘](https://www.youtube.com/watch?v=EFg3u_E6eHU&t=221s)

## 재귀함수

### 재귀적 사고

- 절차지향적 사고 버리기
- (x) 도미노가 쓰러지는 것은 1번을 쓰러뜨리면, 2번, 3번이 쓰러진다
    
    (o) k번 도미노가 쓰러짐 → 고로 k+1 도미노가 쓰러지기 때문에 다 쓰러진다는 사고 필요
    

### 기본 형태

```jsx
function recursive(인자) {
  // 조건이 충족될 때 까지 자기 자신을 호출
  if(조건 충족) {
    return 결과
  } else {
    return recursive(작업된 인자)
  }
}
```

1. 재귀 함수의 입력값과 출력값 정의하기 : 문제를 가장 추상적으로 단순하게 정의
2. 문제를 쪼개고 경우의 수를 나누기 : 입력값이나 문제의 순서와 크기를 고려
3. 단순한 문제 해결하기 : 문제를 더이상 쪼갤 수 없을 때까지 쪼개어 가장 해결하기 쉬운 문제부터 해결, 이를 base case라고 함base case : 재귀 함수 구현 시 재귀의 탈출 조건(재귀 호출이 멈추는 조건) 구성
4. 복잡한 문제 해결하기 : 남아있는 문제 해결, 이를 recursive Case라고 함recursive Case : 자신을 호출하는 함수를 포함
5. 코드 구현하기

## 다익스트라 알고리즘

그래프의 출발점에서 해당 노드까지의 최저 거리를 구하는 알고리즘

1. 출발 노드를 설정ex) 1
2. 출발 노드를 기준으로 연결된 노드의 최소 비용 저장
    
    ex) 1과 연결된 노드가 2, 4 이므로 두 노드에 최소 비용 저장 2(1), 4(2)
    
3. 방문하지 않은 노드 중에서 가장 비용이 적은 노드 선택
    
    ex) 2(1), 4(2) 중 비용이 1로 적은 2 선택
    
4. 선택한 노드와 연결된 노드의 최소 비용 저장
    
    ex) 3(4), 5(3)
    
5. 위 과정에서 3~4번 반복(가지고 있던 비용보다 작은 비용이라면, 최소로 갱신)
6. 순환을 마치면 각 노드마다 최소 비용이 나옴

- 예시 (1~N까지 K이하로 갈 수 있는 마을 구하기)
    
    ![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%206.png)
    
    마을은 `node`, 경로는 `arc`(아크), 비용은 `dist`(distance)로 표현했다.
    
    1. 배열 `dist` 생성 : 출발점부터 해당 노드로 가는 최소 비용을 저장할 배열최소값마다 갱신해야 하므로 초기값을 무한대로 설정
    2. 배열 `arcs` 생성: 해당 노드와 연결된 노드와 경로값 저장할 배열
    3. `road`를 순회하며 `arcs`에 경로 저장ex) `road[n]`마다 저장되는 형태 => `[{node: , arc: }, {node: , arc: },...]`
    4. 큐 생성 & 초기값 설정 : 출발점인 마을 1로 설정
    5. 출발점(마을 1)의 거리값을 0으로 설정
    6. 큐의 값을 순회
        1. 기존에 경로의 값보다 우회하는 값이 더 작으면 해당 값을 저장> 큐에 값을 넣고, `dist`값에 따라 오름차순으로 정렬되는 함수 실행
        2. 아니라면 다음 큐의 값으로 넘어감 (`pushQue` 함수로 인해 최소 비용을 가진 노드로 넘어감)
    7. 경로의 제한인 K보다 arc가 작은 경로의 수를 반환
    
    ```jsx
    function solution(N, road, K) {
    
        let dist = new Array(N+1).fill(Number.MAX_SAFE_INTEGER); // 1
        let arcs = Array.from(new Array(N+1), () => []); // 2
    
        for(let i = 0; i < road.length; i++) { // 3
            let [a,b,c] = road[i];
            arcs[a].push({node: b, arc: c});
            arcs[b].push({node: a, arc: c});
        }
    
        let queue = [1]; // 4
        dist[1] = 0; // 5
    
        function pushQue(v) { // 6-1
            queue.push(v);
            queue.sort((a,b) => dist[a.node] - dist[b.node]);
        }
    
        while(queue.length) { // 6
    
            let now = queue.shift();
    
            arcs[now].forEach(connect => {
    
                let next = connect.node;
                if(dist[next] > dist[now] + connect.arc) {
                    dist[next] = dist[now] + connect.arc;
                    pushQue(next);
                }
            })
        }
        return dist.filter(v => v <= K).length; // 7
    }
    ```
    

## ****다이나믹 프로그래밍 (동적 프로그래밍)****

큰 문제를 작은 문제로 쪼개 결과값을 저장 후, 재활용하여 큰 문제를 해결하는 방식

알고리즘 보다는 방법론(문제 해결 방식)에 가깝다

- **재귀와 차이점**
    
    재귀는 단순히 작은 문제들을 반복적으로 불러내어 비효율적일 수 있다. 
    
    ex) 피보나치 수열 f(n) = f(n-1) + f(n-2)
    
    여기서 f(n-1)는  f(n-2)를 호출하며 계산되고, 값을 구한 다음에는 더하는 수인 f(n-2)가 또 다시 계산된다.
    
    DP는 f(n-2)가 한 번 호출되면, 그 값이 저장되어 다음에는 계산하지 않아도 된다.
    
- **분할 정복과 차이점**
    
    분할 정복도 큰 문제를 작은 문제로 쪼개 해결하지만, 작은 문제들이 중복되지 않고 독립적이다.
    

### 사용 조건

1. **Overlapping Subproblems (겹치는 부분 문제)**
    
    동일한 작은 부분이 반복하여 나타나야 함
    
2. **Optimal Substructure (최적 부분 구조)**
    
    작은 문제의 최적 결과 값을 사용해 큰 문제의 최적 결과값을 낼 수 있는 경우
    

### 구현

1. **Bottom-up 방식**
    
    문제의 아래부터 위로 값을 쌓아올리며 최종값에 도달함
    
2. **Top-down 방식**
    
    문제의 위부터 호출을 시작하여, 아래까지 내려오면서 모든 결과값을 저장 → 저장된 결과값을 사용하는 재귀 호출
    

### 예시 문제 (땅따먹기)

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%207.png)

a까지 이르는 경로는 다양하겠지만, 일단 a에 이르고 나서 탐색되는 아래 부분은 항상 같다.

이는 a까지 어떤 경로를 선택하던지 a에서 출발해서 얻을 수 있는 최대값을 항상 같다는 것이다.

그러므로 그 값을 저장해두면 다음에 다른 경로로 a에 오더라도 사용할 수 있어 효율적이다.

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%208.png)

a, b, c, d 에서 출발했을 때 얻을 수 있는 최대값을 모두 저장해놨을 때 K지점에서 출발해 얻을 수 있는 최고 점수는 아래와 같다

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%209.png)

- K지점의 값 = `land[i][0]`
- K에서 출발해 얻을 수 있는 최대값 = `dp[i][0]`

∴ **dp[i][0] => b, c, d 각각 위치에서 출발해서 얻을 수 있는 최대값 중에서 최대값 + K 위치의 값**

```jsx
dp[i][0] = max(dp[i+1][1], dp[i+1][2], dp[i+1][3]) + land[i][0]
```

출발 위치를 달리 했을 때의 최대값은 아래와 같다.

![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%2010.png)

경로를 밑에서 위로(거꾸로) 올라가며 계산해도 값은 같음

## 타일링

### 2xn 타일링

**f(n) = f(n-1) + f(n-2)**

- 초기값 설정 : f(0) = 1  /  f(1) = 1  /  f(2) = 2

### ****가능한 타일이 2x1 & 2x2 인 경우****

**f(n) = f(n-1) + 2 * f(n-2)**

- 초기값 설정 :  f(1) = 1  /  f(2) = 3

### ****3xn 타일링****

**f(n) = f(n-2) * 3 + (f(n-4) * 2 + f(n-6) * 2 ... f(0) * 2)**

- 초기값 설정 : f(0) = 1  /  f(1) = 0  /  f(2) = 3

### ****2xn을 더 작은 타일로 채우기****

2xn넓이를 2x1, 2x2, 1x1의 타일로 채우는 경우의 수

**f(n) = f(n-2) * 3 + f(n-1) * 2 + (f(n-3) * 2 + f(n-6) * 2 ... f(0) * 2)**

- 초기값 설정 : f(0) = 1  /  f(1) = 2  /  f(2) = 7

## 피보나치

( F(0) = 0, F(1) = 1) 1 이상의 n에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 수

- 보통 큰 수로 나눈 나머지를 반환하거나 저장하라고 문제 나옴 (굉장히 수가 크기 때문에 메모리가 감당x)
    
    (A + B) % C ≡ ( ( A % C ) + ( B % C) ) % C
    
    나눈 수를 저장한 후, 그 수를 다시 더하고 나눠도 결과는 같음
    

### DP (보텀탑)

아래서 위로 값을 저장해서 쌓아 올리는 다이나믹 프로그래밍 방식

```jsx
function solution(n) {

    let arr = [0, 1];

    for (let i = 2; i <= n; i++) {
        arr.push((arr[i-1] + arr[i-2]) % 1234567);
    }
    return arr[n] ;
}
```

### 재귀 (탑다운)

오래 걸리기 때문에 잘 사용하지 않음

```jsx
function solution(n) {

    function accF(m) {
        if(m < 2) return m;
        return accF(m-1) + accF(m-2);
    }

    return accF(n) % 1234567;
}
```

## 최대공약수 / 최소공배수

 

### **유클리드 호제법**

최대공약수를 구하는 알고리즘

(큰 값 max , 작은 값 min)

1. max % min = e(1)
2. min % e(1) = e(2)
3. e(1) % e(2) = e(3)
    
    ⋮
    
    e(n-1) % e(n) = 0
    
- 최대공약수 = e(n)
- 최소공배수 = (max * min) /e(n)

```jsx
function solution(n, m) {

    // max = 큰값 , min = 작은값
    let max = Math.max(n,m);
    let min = Math.min(n,m);

    // 최대공약수 구하는 함수
    function u(max, min) {
        let e = max % min;
        if (e === 0) return min;
        return u(min, e);
        }

    // 최대공배수 반환
    alert(u(max,min));

    // 최소공배수 반환
    alert(max * min / u(max,min));
}

// 간추린 코드 (최대공약수 반환)
function solution(n, m) {
  function u(n, m) { return m % n ? u(m % n, n) : n; }
}
```

### 약수 구하기

- n/2까지 순회 (순회 후, 본인 더하기)
    
    ex) 12의 약수 = [1,2,3,4,6,12] 
    
    6과 12 사이에는 약수가 나올 수 없음
    

```jsx
function solution(n) {

    let divisor = [];

    for (let i = 1; i <= n/2; i++) {
        if (num % i === 0) divisor.push(i);
    }
    return divisor.push(n)
}
```

- n의 제곱근까지 순회
    
    n이 큰 수라서 효율성을 줄여야 할 때 필요함
    
    (제곱근이 정수인지 판단해서 중복 체크 해야함)
    

```jsx
let divisor = [];
let z = Math.sqrt(i);

for(let i = 1; i <= z; i++) {
	if (num % i === 0) divisor.push(i);
}

// 제곱근 체크해서 없애는 과정
```

---

### 두 직선의 교점 구하기

- **두 직선의 식 (유일할때)**
    - ax + by = e
    - cx + dy = f
    
    ![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%2011.png)
    
    - ax + by + e = 0
    - cx + dy +f = 0
    
    ![Untitled](codingTest-keyPoint%205160bc0094274f849be6fe9055499cd6/Untitled%2012.png)
    
    - AD-BC =0  ⇒ (기울기가 같음) 교점 없음

```jsx
function solution(line) {
    // line = [[A,B,C]...] => Ax + By + C = 0 직선 (ABC => -100,000 ~ 100,000)
    // line.legnth(선 개수) 2~1000 / 
    // x,y가 정수인 교차지점 *로 표시 -> 모두 포함 최소 사각형 return (1000x1000 이내)
    // 예외케이스 챙기기
    
    let dots = [];

    line.forEach((v,idx) => {
        
        let A = v[0];
        let B = v[1];
        let C = v[2];
        
        for(let i = idx+1; i < line.length; i++) {
            let a = line[i][0];
            let b = line[i][1];
            let c = line[i][2];
            
            let dot = [(B*c-b*C)/(A*b-a*B), -(A/B)*(B*c-b*C)/(A*b-a*B)-C/B];
            
            if(A*b - a*B === 0) continue;
            if(dot[0] % 1 === 0 && dot[1] % 1 === 0) {
                if(checkOverlap(dot)) dots.push(dot);
            }
        }
    })
    
    // dots 중복 제거
    function checkOverlap(arr) {
        for(let i = 0; i < dots.length; i++) {
            if(dots[i][0] === arr[0] && dots[i][1] === arr[1]) return false;
        }
        return true;
    }
    
    // 문자열로 출력하기
    // 최대 x, y 좌표 구하기 -> 사각형의 가로, 세로
    
    let x = dots.map(v => v[0]);
    let y = dots.map(v => v[1]);
    
    let minW = Math.min.apply(null, x);
    let maxW = Math.max.apply(null, x);
    let minH = Math.min.apply(null, y);
    let maxH = Math.max.apply(null, y);
    
    
    // 사각형 생성
    let answer = Array.from(new Array(maxH - minH + 1), () => new Array(maxW - minW + 1).fill('.'));
    
    dots.forEach(v => {
        answer[v[1]-maxH][v[0]-maxW] = '*';
    })
    return answer;
    return answer.map(v => v.map(e => e.join('')));
}
```

### [1,2,3,4…n] 배열 만들기

`Array.from({length: n}, (_,i) => i + 1);`

### 팩토리얼 만들기

위 배열의 팩토리얼 만들기

`let fac = arr.reduce((ac,v) => ac * v, 1);`