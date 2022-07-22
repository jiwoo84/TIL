# Data Structure

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

![외우지 말고 참고할 것 ](Data%20Structure%20cc363cc228734795b269e43efcdf93ea/Untitled.png)

외우지 말고 참고할 것 

---

# 문제해결 과정

1. 문제를 정확히 이해
2. 예시 찾기
    
    간단 → 복잡 → 빈 input → 유효하지 않은 input
    
3. 문제 세분화 (의사코드 작성)
4. 코드 작성
    
    막히는 부분이 있다면 넘어가고, 다른 부분부터 단순화하기 → 나중에 통합
    
5. 리팩토링

---

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
    	B.indexOf(A[i]**2) 찾아서 삭제
    	없으면 return false
    순회 마쳤으면  return true
    ```
    
- best
    
    ```jsx
    A 순회해서 {요소: 개수, ...} 객체 만듬
    B 순회해서 {요소: 개수, ...} 객체 만듬
    A객체의 key 순회해서 B객체[key**2] 값과 비교
    	같지 않으면 return false
    순회 마쳤으면 return true
    ```
    

## Multiple Pointers (다중 포인터)

배열 속의 값을 비교해서 답을 도출할 때 사용 (주로 쌍으로 비교)

### 예시

1. 오름차순으로 정렬된 배열 요소 중, 합치면 0이 되는 두 요소를 찾아 배열로 반환
    
    ex) `[-2,1,0,2]` ⇒ return `[-2, 2]`
    
    - worst
        
        ```jsx
        for 배열 순회
        	for 배열 순회 (i+1부터)
        	arr[i] + arr[j] = 0 이면 두 값 배열 반환 
        ```
        
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
        
    
2. 고유한 값의 갯수 구하기
    
    ex) `[1,1,2,3,3,3,4,4]` ⇒ `[1,2,3,4]` ⇒ return 4
    
    - best
        
        나란히 출발하는 포인터 2개 설정 → 두 값 비교해서 다르면 i의 다음 자리에 j 값 넣음 → j는 계속 전진, i는 달라야 전진
        
    
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
    

## Sliding Window (기준점 간 이동)

배열 속 연달은 값을 이용해서 답을 도출하는 문제

### 예시

배열 속 n만큼 연달은 숫자들의 합 중, 최대값 구하기

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

## Divide & Conquer (분할정복)

문제를 작게 분할하여 해결한 후, 조합하는 방법

ex) 퀵 정렬, 합병 정렬, 이진 탐색