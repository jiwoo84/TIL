# 코테 키포인트

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

![Untitled](%E1%84%8F%E1%85%A9%E1%84%90%E1%85%A6%20%E1%84%8F%E1%85%B5%E1%84%91%E1%85%A9%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%205160bc0094274f849be6fe9055499cd6/Untitled.png)

- 중복순열 : 중복을 허용하여 r개 선택 ⇒ $n^r$

### **조합**

n개 중에서 r개를 선택하는 경우의 수 (순서 상관 x)

![Untitled](%E1%84%8F%E1%85%A9%E1%84%90%E1%85%A6%20%E1%84%8F%E1%85%B5%E1%84%91%E1%85%A9%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%205160bc0094274f849be6fe9055499cd6/Untitled%201.png)

⇒ $n! /(n-r)!*r!$

- 중복조합: 중복을 허용하여 r개 선택 ⇒ n+r-1Cr

### 같은 것이 있는 경우

![Untitled](%E1%84%8F%E1%85%A9%E1%84%90%E1%85%A6%20%E1%84%8F%E1%85%B5%E1%84%91%E1%85%A9%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%205160bc0094274f849be6fe9055499cd6/Untitled%202.png)

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

![Untitled](%E1%84%8F%E1%85%A9%E1%84%90%E1%85%A6%20%E1%84%8F%E1%85%B5%E1%84%91%E1%85%A9%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%205160bc0094274f849be6fe9055499cd6/Untitled%203.png)

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
    
    ![간단 but 메모리 큼](%E1%84%8F%E1%85%A9%E1%84%90%E1%85%A6%20%E1%84%8F%E1%85%B5%E1%84%91%E1%85%A9%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%205160bc0094274f849be6fe9055499cd6/Untitled%204.png)
    
    간단 but 메모리 큼
    
2. 연결 리스트
    
    ![복잡 bup 메모리 작음](%E1%84%8F%E1%85%A9%E1%84%90%E1%85%A6%20%E1%84%8F%E1%85%B5%E1%84%91%E1%85%A9%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%90%E1%85%B3%205160bc0094274f849be6fe9055499cd6/Untitled%205.png)
    
    복잡 bup 메모리 작음
    
- [디익스트라 알고리즘](https://www.youtube.com/watch?v=EFg3u_E6eHU&t=221s)

## 재귀함수

절차지향적 사고 버리기

도미노가 쓰러지는 것은 1번을 쓰러뜨리면, 2번, 3번이 쓰러진다가 아닌

k번 도미노가 쓰러짐 → 고로 k+1 도미노가 쓰러지기 때문에 다 쓰러진다는 사고 필요

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