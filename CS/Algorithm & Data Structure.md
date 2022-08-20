# Algorithm & Data Structure

# array & object 성능평가

## 객체

정렬 되어있지 않지만, 접근하는 속도가 빠름

- 삽입 : O(1)
- 삭제 : O(1)
- 검색 : O(N)
- 접근 : O(1)
    
    ### 메서드 빅오
    
    - Object.keys : O(N)
    - Object.values : O(N)
    - Object.entries : O(N)
    - hasOwnProperty : O(N)

## 배열

정렬되어 있지만, 삽입과 삭제가 느림

- 삽입 & 삭제 : 앞쪽 인덱스에 위치할수록 느림
- 검색 : O(N)
- 접근 : O(1)

![외우지 말고 참고할 것 ](Algorithm%20&%20Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled.png)

외우지 말고 참고할 것 

# 문제해결 과정

1. 문제를 정확히 이해
2. 예시 찾기
    
    간단 → 복잡 → 빈 input → 유효하지 않은 input
    
3. 문제 세분화 (의사코드 작성)
4. 코드 작성
    
    막히는 부분이 있다면 넘어가고, 다른 부분부터 단순화하기 → 나중에 통합
    
5. 리팩토링

# 문제해결 패턴

## frequency counter (빈도 카운터)

빈도를 세는 문제

- worst : 중첩 for문
- best : 객체 사용

### 예시

A배열의 각 요소의 제곱이 B요소에 포함되었는지 확인하시오 (갯수도 같아야 함)

- worst
    
    ```jsx
    for A 순회
    	B.indexOf(n) 찾아서 삭제
    	없으면 return false
    순회 마쳤으면  return true
    ```
    
- best
    
    ```jsx
    A 순회해서 {요소: 개수, ...} 객체 만듬
    B 순회해서 {요소: 개수, ...} 객체 만듬
    A객체의 key 순회해서 B객체 값과 비교
    	같지 않으면 return false
    순회 마쳤으면 return true
    ```
    

---

## Multiple Pointers (다중 포인터)

배열 속의 값을 비교해서 답을 도출할 때 사용 (주로 쌍으로 비교)

### 예시

1. 오름차순으로 정렬된 배열 요소 중, 합치면 0이 되는 두 요소를 찾아 배열로 반환
    
    ex) `[-2,1,0,2]` ⇒ return `[-2, 2]`
    
    - best
        
        양쪽 끝에서 출발하는 포인터 설정 후, 비교하고 포인터 변경하면서 값 찾기
        
        ```jsx
        let left = 0; // 왼쪽에서 출발하는 인덱스
        let right = arr.length -1 // 오른쪽 출발 인덱스
        
        while(left < right) { // 둘이 만나기 전에 종료
        	let sum = arr[left] + arr[right];
        	if(sum === 0) return 반환값
        	else (sum > 0) right --; // arr[right]이 더 크므로 이동
        	else left ++; // 
        ```
        
    - worst
        
        ```jsx
        for 배열 순회
        	for 배열 순회 (i+1부터)
        	arr[i] + arr[j] = 0 이면 두 값 배열 반환 
        ```
        
    
2. 고유한 값의 갯수 구하기
    
    ex) `[1,1,2,3,3,3,4,4]` ⇒ `[1,2,3,4]` ⇒ return 4
    
    - 나란히 출발하는 포인터 2개 설정 → 두 값 비교해서 다르면 i의 다음 자리에 j 값 넣음 → j는 계속 전진, i는 달라야 전진
        
        ```jsx
        if(!arr.length) return 0; // 비어있으면 0 반환
        // 포인터 2개 생성
        let i = 0;
        // j는 순회하면서 증가
        for(let j = 1; j < arr.length; j++) {
            if(arr[i] !== arr[j]) { // 같지 않으면
                arr[++i] = arr[j]; // i를 오른쪽으로 옮기고 거기에 arr[j]값 넣기
            }
        }
        return i+1; 
        // 최종 arr의 모양은 [1,2,3,4,3,3,4,4] 이런식으로 됨
        // i는 인덱스 3에 멈춰있음
        ```
        
    

---

## Sliding Window (기준점 간 이동)

배열 속 연속한 값을 이용해서 답을 도출하는 문제

### 예시

배열 속 n만큼 연속한 숫자들의 합 중, 최대값 구하기

⇒ 맨 처음부터 n개의 연달은 숫자의 합을 구하고, 두 개의 포인터를 이동해가며 (i-n, i) 앞꺼는 빼고, 뒤는 더해주면서 합계 비교

```jsx
if(arr.length < n) return null;

let maxSum = 맨 처음 연달은 n개의 값의 합
let tempSum = maxSum; // 비교할 임시값

for (let i = n; i < arr.length; i++) { // maxSum에 더한 수 바로 다음 값부터 순회
	tempSum = tempSum - arr[i-n] + arr[i];
	maxSum = Math.max(maxSum, tempSum);
}

return maxSum;
```

---

## Divide & Conquer (분할정복)

문제를 작게 분할하여 해결한 후, 조합하는 방법

ex) 퀵 정렬, 합병 정렬, 이진 탐색

### 가변인자 사용 방법

1. 가변인자는 함수 내 arguments(배열 X , 객체 O)로 호출 가능
    
    ```jsx
    function sum() {
        console.log(arguments);
    }
    // 1,2,3 입력 -> { '0': 1, '1': 2, '2': 3 } 출력
    ```
    
2. spread 연산자 사용
    
    배열의 값으로 인자를 받았기 때문에, 호출값은 배열임
    
    ```jsx
    function sum(...args) {
        console.log(args);
    }
    // 1,2,3 입력 -> [1,2,3] 출력
    ```
    

# 재귀

1. 종료조건 설정
2. 올바른 리턴값 설정
- Tip - 결과값 복사해서 업데이트하는 메소드 사용
    - 배열 : `slice`(arr 자체 변경) / `concat` / spread 연산자
    - 문자열 : `slice` / `substr` / `substring`
    - 객체
        
        `Object.assign` / the spread operator
        

### Helper 메소드 재귀

외부 함수(재귀x)가 재귀 내부 함수를 호출하는 형태의 함수

→ 함수를 실행할 때마다 결과값이 초기화되서 편함

- ex) 배열 안의 홀수 요소만 배열로 만들어 반환하는 함수
    
    ```jsx
    function collectOddValue(arr) {
    	let result = [];
    
    	function helper(helperInput) {
    		if(helperInput.length < 1) return;
    
    		if(helperInput[0] % 2) result.push(helperInput[0]);
    
    		helper(helperInput.slice(1));
    	}
    
    	helper(arr);
    
    	return result;
    };
    ```
    
    - 이를 순수재귀로 작성한다면
        
        ```jsx
        function collectOddValue(arr) {
        	let newArr = [];
        
        	if(arr.length === 0) return newArr;
        
        	if(arr[0] % 2) newArr.push(arr[0]);
        
        	newArr = newArr.concat(collectOddValue(arr.slice(1)));
        
        	return newArr;
        };
        ```
        
    

# 검색

## 선형 검색 (Linear Search)

하나씩 차례대로 비교해서 찾는 방식

- 사용하는 메서드
    - indexOf
    - includes
    - find
    - findIndex

### 시간복잡도

- O(n)
- Ω(1)

### 구현

```jsx
function linearSearch(arr, n) {
    for(let i = 0; i < arr.length; i++) {
        if(arr[i] === n) return i;
    }
    return -1;
}
```

---

## 이진 검색 (Binary Search)

- 분할 정복 사용
- (선행: 데이터 정렬) 중간값 확인 후, 앞 or 뒤 이동해서 검색 반복

### 시간복잡도

- O(log n)
- Ω(1)

### 구현

두 개의 포인터를 사용하여 구현

```jsx
function binarySearch(arr, n) {
    let start = 0;
    let end = arr.length - 1;
    let middle = null;

    while(start <= end) {
        middle = Math.floor((start + end) / 2);
        if(arr[middle] === n) return middle;
        else if(n < arr[middle]) end = middle - 1;
        else if(n > arr[middle]) start = middle + 1;
    }
    return -1;
}
```

---

## 문자열 부분 검색 (Naive String Search)

문자열 앞에서부터 차례대로 비교, 일치하면 다음 글자 비교하면서 전부 일치하면 카운터 +1

### 구현

```jsx
function naiveSearch(long, short) {
    let cnt = 0;
    for(let i = 0; i < long.length; i++) {
        for(let j = 0; j < short.length; j++) {
            if(long[i+j] !== short[j]) break;
            if(j === short.length - 1) cnt ++;
        }
    }
    return cnt;
}
```

# 정렬

| Algorithm | Big-O (상한) | Big-θ (평균) | Big-Ω (하한) | 공간 복잡도 |
| --- | --- | --- | --- | --- |
| 버블 정렬 | O(n^2) | θ(n^2) | Ω(n) | O(1) |
| 삽입 정렬 | O(n^2) | θ(n^2) | Ω(n) | O(1) |
| 선택 정렬 | O(n^2) | θ(n^2) | Ω(n^2) | O(1) |
| 합병 정렬 | O(n log n) | θ(n log n) | Ω(n log n) | O(n) |
| 퀵 정렬 | O(n^2) | θ(n log n) | Ω(n log n) | O(log n) |

## 버블 정렬 (Bubble Sort)

두 개의 인접한 자료 값을 비교하면서 위치를 교환하는 방식

중첩 루프를 돌며, n개의 값이 주어졌을 때 루프가 n-1번, n-2번 반복되므로 (n-1)*(n-2) = n^2 -3n +2번의 비교·교환이 필요함

![Untitled](Algorithm%20&%20Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled%201.png)

### 시간복잡도

- **O(n^2)** : 최악의 경우 n^2 -3n +2번 모두 진행
- **Ω(n)** : (최적화 설정 & 정렬된 경우) n-1번만 비교

### 구현

```jsx
function swap(arr, i, j) {
	[arr[i], arr[j]] = [arr[j], arr[i]];
}

function bubbleSort(arr) {
	for(let i = arr.length; i > 0 ; i --) {
		for(let j = 0; j < i - 1; j++) {
			if(arr[j] > arr[j+1]) swap(arr, j, j+1);
		}
	}
	return arr;
}
```

- 최적화 추가 : 순회 중, 교환이 발생하지 않았다면 과정을 끝냄
    
    ```jsx
    function swap(arr, i, j) {
    	[arr[i], arr[j]] = [arr[j], arr[i]];
    }
    
    function bubbleSort(arr) {
    	let noSwap;
    	for(let i = arr.length; i > 0 ; i --) {
    		let noSwap = true;
    		for(let j = 0; j < i - 1; j++) {
    			if(arr[j] > arr[j+1]) {
    				swap(arr, j, j+1);
    				noSwap = false; // swap 발생 시, false로 변경
    			}
    		}
    		if(noSwap) break;
    	}
    	return arr;
    }
    ```
    

---

## 삽입 정렬 (Insertion Sort)

두 번째 자료부터 시작하여 앞의 자료들과 비교해 삽입할 위치를 지정한 후, 자료를 뒤로 옮기고 삽입되는 과정을 반복한 정렬

### 시간복잡도

- O(n^2)
- Ω(n) : 이미 정렬된 경우

### 구현

```jsx
function insertionSort(arr) {
    for (let i = 1; i < arr.length; i++) {
        let currentValue = arr[i]; // 현재 비교할 값 저장 (arr가 계속 바뀌기 때문에 저장해야함)
        for (let j = i - 1; j >= 0 && arr[j] > currentValue; j--) { // 앞에 큰 값 있다면
            [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]]; // 이전 값, 현재 값 변경
        }
    }
    return arr;
}
```

---

## 선택 정렬 (Selection Sort)

배열 안의 자료 중 가장 작은 수(혹은 가장 큰 수)를 찾아 첫 번째 위치(혹은 가장 마지막 위치)의 수와 교환해주는 방식

### 시간복잡도

- O(n^2) : n + (n-1) + (n-2) + … = n(n-1)/2
- Ω(n^2) : 정렬 여부 상관없이 모두 실행

### 구현

```jsx
function selectionSort(arr) {

    for(let i = 0; i < arr.length; i++) {
        let lowest= i; // 최소값 설정
        for(let j = i+1; j < arr.length; j++) {
            if(arr[j] < arr[lowest]) lowest = j; // 최소값 업데이트
        }
				// 만약 최소값에 변동이 있다면 바꿔주기
        if(i !== lowest) [arr[i], arr[lowest]] = [arr[lowest], arr[i]];
    }

    return arr;
}
```

---

## 합병 정렬 (Merge Sort)

배열을 요소가 하나가 될 때까지 분할 → 맨 앞 값을 하나씩 비교해 정렬하면서 합병 → 반복

![Untitled](Algorithm%20&%20Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled%202.png)

![Untitled](Algorithm%20&%20Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled%203.png)

![Untitled](Algorithm%20&%20Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled%204.png)

![Untitled](Algorithm%20&%20Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled%205.png)

### 시간복잡도

- O(n log n) : 분할하면서 logn, 비교하면서 n
- Ω(n log n)

### 구현

- 정렬
    
    맨 앞부터 시작해서 작은 값은 result에 넣고, 포인터를 이동해가면서 비교 → 한 배열이 모두 result에 들어갔다면 나머지 배열의 남은 값 모두 넣기
    
- 합병
    
    재귀를 이용해서 끝까지 나눴다가 합병
    

```jsx
// 정렬 함수
function merge(arr1, arr2) {
    let p1 = 0; // arr1의 포인터
    let p2 = 0; // arr2의 포인터
    let result = [];

    while(p1 < arr1.length && p2 < arr2.length) {
        if(arr1[p1] < arr2[p2]) { // 값 비교해서 작은 값 result에 넣기
            result.push(arr1[p1]);
            p1++;
        }
        else {
            result.push(arr2[p2]);
            p2++;
        }
    }

    // 남은 배열의 값이 있다면, 나머지 다 넣기
    if(p1 < arr1.length) result.push(...arr1.slice(p1));
    else if(p2 < arr2.length) result.push(...arr2.slice(p2));

    return result;
}

function mergeSort(arr) {
    if(arr.length <= 1) return arr;

    let mid = Math.floor(arr.length/2);
    let left = mergeSort(arr.slice(0, mid));
    let right = mergeSort(arr.slice(mid));

    return merge(left, right);
}
```

---

## 퀵 정렬 (Quick Sort)

피벗값(파티션) 하나를 설정해서 이보다 작은 값은 왼쪽, 큰 값은 오른쪽으로 옮김 → 피벗을 다시 설정 → 반복

- 피벗 설정 : 편의상 맨 첫 번째 인덱스로 설정

### 시간복잡도

- Ω(n log n) : 피벗이 작은 값은 왼쪽, 큰 값은 오른쪽에 놓고 중앙에 위치하면서, 배열이 분할되고, 재귀 logn, 비교하면서 n
- O(n^2) : 정렬된 상태에서 맨 앞 값이나 맨 뒤 값을 피벗으로 선택하면 n번 피벗이 설정되고, 매번 n번 비교되니 n^2의 시간이 들어감
    
    → 이를 방지하기 위해서 피벗을 중간값이나 무작위로 설정해야함
    

### 구현

<aside>
💡 추가 공간없이 배열 그 자체를 수정해나갈 것

</aside>

1. 피벗값(파티션) 하나를 설정
2. 피벗과 다른 값들의 크기를 비교 → 작은 값은 왼쪽, 큰 값은 오른쪽으로 옮김 (피벗을 중앙으로 옮김)
    - 비교해서 옮기는 자세한 과정
        1. 포인터 설정 = 1
        2. 피벗의 다음 값부터 피벗과 비교
        3. 피벗 > 값 ⇒  포인터의 값과 해당 값을 바꾸고 포인터+1
        4. 피벗 < 값 ⇒ 그냥 놔둠
        5. 맨 끝까지 비교했다면, 최종적인 포인터의 값과 피벗 교체 
3. 피벗의 왼쪽, 오른쪽 부분에 재귀함수 호출
4. 반복하며 범위가 요소 하나가 될 때까지 비교되다가, 최종 배열 반환

```jsx
// array의 두 값을 교환하는 swap 함수
function swap(arr, i, j) {
    [arr[i], arr[j]] = [arr[j], arr[i]];
}

// -----------------------------------------------
// pivot의 알맞은 위치인덱스를 반환하는 함수
function pivot(arr, start = 0, end = arr.length-1) { 

    let pivot = arr[start]; // arr[0]을 피벗으로 설정
    let swapIdx = start; // 업데이트 될 반환값

    for(let i = start + 1; i <= end; i++) { // 피벗 다음 위치부터 시작
        if(pivot > arr[i]) { // 만약 피벗보다 작은 값 발견했다면
            swapIdx ++; // 위치를 하나 뒤로 옮기고
            swap(arr, i, swapIdx); // 둘이 바꿈
        }
    }

    swap(arr, start, swapIdx); // 피벗과 마지막으로 바꿨던 값이랑 swap 
    return swapIdx; // 피벗이 최종적으로 찾아간 위치 반환
}

// 피벗을 사용해 최종적으로 배열을 정렬하는 함수
function quickSort(arr, left = 0, right = arr.length-1) {
    if(left < right) { // 함수를 실행하는 부분이 값 하나가 되면 실행x
        let pivotIdx = pivot(arr, left, right); // 피벗의 위치 구해서
        quickSort(arr, left, pivotIdx-1); // 그 왼쪽 부분을 다시 재귀
        quickSort(arr, pivotIdx+1, right); // 오른쪽 부분을 다시 재귀
    }
    return arr; // 최종으로 재귀를 마친 배열 반환
}
```

`quickSort()`는 재귀의 반환값으로 뭔가를 실행하는 형태가 아니기 때문에 계속 깊게 재귀되다가 마지막 함수가 호출될 때, 반환되도록 설정해줘야 한다.