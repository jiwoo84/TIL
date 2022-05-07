# programmers Lv.2

- **자연수**
    
    1부터 무한히 증가하는 수 (1,2,3,4,5...) / 음수, 분수, 소수 미포함
    
- **정수**
    
    자연수와 비슷하지만 음수 포함 ( ... -2, -1, 0, 1, 2 ...) / 분수, 소수 미포함
    

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