# programmers Lv.2

- **자연수**
    
    1부터 무한히 증가하는 수 (1,2,3,4,5...) / 음수, 분수, 소수 미포함
    
- **정수**
    
    자연수와 비슷하지만 음수 포함 ( ... -2, -1, 0, 1, 2 ...) / 분수, 소수 미포함
    

## 완전 탐색

### 소수찾기 (미완)

```jsx
function solution(numbers) {
    // return 문자열의 숫자 조합해서 만들 수 있는 소수의 개수
    
    // numbers 배열로 변환 -> 오름차순 정렬 ex) ['7','3','1']
    numbers = numbers.split('').sort((a,b) => b - a);
    
    //변수 maxNum = numbers 문자열로 변환 -> 숫자로 변환  ex) 731
    let maxNum = + numbers.join('');
    
    //함수 makePrime(num) = 아리토스테네스의 체로 소수 개수 반환
    function makePrime(num) {
        
        let arr = new Array(num+1).fill(true);
        
        for (let i = 2; i < Math.sqrt(num); i++) {

            for (let j = i*i; j <= num; j += i) {
                arr[j] = false;
            }
            return arr;
        }
    }
    
    // 배열 primes = makePrime(maxNum) (소수index의 값은 비어있음, 소수 아니면 false)
    let primes = makePrime(maxNum);
    //  ex) [true,true,false,false ...]

    // 변수 count = 소수 개수 세는 용도
    let count = 0;
    
    // for: (2 ~ maxNum, i++)
    for (let i = 2; i <= maxNum; i++) {
        
    //      if (arr[i] === false) 통과
        if (primes[i] === false) continue;
        
    //      배열 iArr = i의 자릿수를 배열로 변환
        let iArr = String(i).split('');
        
        for(let e of numbers) {
            
            if (iArr.includes(e)) {
                iArr.splice(iArr.indexOf(e), 1);
                if(iArr.length === 0) count ++
            }
            else continue;
        }
    }
    return count;    
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

- **조합**
    
    n개 중에서 m개를 선택하는 경우의 수 (nCr = n개 중 r개의 combination)
    
    조합은 순서 상관 없음 ⇒ [1,2] & [2,1]은 같은 것으로 취급
    
    ex) Input: [1, 2, 3, 4]
    
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
        const getCombinations = function (arr, selectNumber) {
          const results = [];
        	// 1. 1개씩 택할 때, 바로 모든 배열의 원소 return (재귀함수 종료 조건)
          if (selectNumber === 1) return arr.map((value) => [value]); 
        
          arr.forEach((fixed, index, origin) => {
            const rest = origin.slice(index + 1); // 2. 해당하는 fixed를 제외한 나머지 뒤
            const combinations = getCombinations(rest, selectNumber - 1); // 3. 나머지에 대해서 조합을 구한다.
            const attached = combinations.map((combination) => [fixed, ...combination]); //  4.돌아온 조합에 떼 놓은(fixed) 값 붙이기
            results.push(...attached); // 배열 spread syntax 로 모두다 push
          });
        
          return results; // 결과 담긴 results return
        }
        
        const example = [1,2,3,4];
        const result = getCombinations(example, 3);
        console.log(result);
        // => [ [ 1, 2, 3 ], [ 1, 2, 4 ], [ 1, 3, 4 ], [ 2, 3, 4 ] ]
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
        const getPermutations= function (arr, selectNumber) {
          const results = [];
          if (selectNumber === 1) return arr.map((value) => [value]); // 1개씩 택할 때, 바로 모든 배열의 원소 return
        
          arr.forEach((fixed, index, origin) => {
            const rest = [...origin.slice(0, index), ...origin.slice(index+1)] // 해당하는 fixed를 제외한 나머지 배열 
            const permutations = getPermutations(rest, selectNumber - 1); // 여기만 수정, 나머지에 대해 순열을 구한다.
            const attached = permutations.map((permutation) => [fixed, ...permutation]); // 돌아온 순열에 대해 떼 놓은(fixed) 값 붙이기
            results.push(...attached); // 배열 spread syntax 로 모두다 push
          });
        
          return results; // 결과 담긴 results return
        };
        
        const example = [1,2,3,4];
        const result = getPermutations(example, 3);
        console.log(result);
        ```
        
        [참고링크](https://pul8219.github.io/algorithm/algorithm-permutation-and-combination/)
        

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