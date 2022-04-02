# 코딩테스트

# 프로그래머스

## Level 1

1. **가운데 글자 가져오기**
    
    단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.
    
    - s는 길이가 1 이상, 100이하인 스트링입니다.
    
    - 해답
        
        ```c
        function solution(s) {
            return s.substr(Math.ceil(s.length / 2) - 1, s.length % 2 === 0 ? 2 : 1);
        }
        ```
        
        s.substr 을 사용하면 된다는 것을 캐치하고 공통된 부분을 찾아 적는게 중요할듯...
        
2. **같은 숫자는 싫어**
    
    
    배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,
    
    - arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
    - arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
    
    배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.
    
    - **제한사항**
        - 배열 arr의 크기 : 1,000,000 이하의 자연수
        - 배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수

- 나의 풀이
    
    ```jsx
    function solution(arr)
    {
        // newArr 생성
        let newArr = [];
        // newArr에 savedValue 저장
        newArr.push(arr[0]);
        
        // if 다음 값 = savedValue -> 다음값으로 넘어감
        // if else 다음 값 != saverValue -> arr에 저장
         for (let i=1; i < arr.length; i++) {
            if(arr[i] !== arr[i-1]){
                newArr.push(arr[i]);
            }
        }
        return newArr;
    }
    ```
    

- 다른 풀이
    
    ```jsx
    function solution(arr)
    {
        return arr.filter((val,index) => val != arr[index+1]);
    }
    ```
    
1. 나누어 떨어지는 숫자 배열

- **문제 설명**

array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

- 제한사항
    - arr은 자연수를 담은 배열입니다.
    - 정수 i, j에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.
    - divisor는 자연수입니다.
    - array는 길이 1 이상인 배열입니다.

- 나의 풀이
    
    ```jsx
    function solution(arr, divisor) {
        
        // arr[i] % divisor == 0 인 값만 남기기 // newArr 오름차순 정령
        let newArr = arr.filter(value => value %divisor == 0).sort((a,b) => a-b);
    
        // if(newArr 비어있으면) => return [-1]
        if (newArr.length == 0) {
            return [-1];
        } 
        return newArr;
    }
    ```
    
    ![Untitled](%E1%84%8F%E1%85%A9%E1%84%83%E1%85%B5%E1%86%BC%E1%84%90%E1%85%A6%E1%84%89%E1%85%B3%E1%84%90%20f41b2/Untitled.png)
    
- 해답
    
    ```jsx
    function solution(arr, divisor) {
        var answer = arr.filter(v => v%divisor == 0);
        return answer.length == 0 ? [-1] : answer.sort((a,b) => a-b);
    }
    ```
    
    ![Untitled](%E1%84%8F%E1%85%A9%E1%84%83%E1%85%B5%E1%86%BC%E1%84%90%E1%85%A6%E1%84%89%E1%85%B3%E1%84%90%20f41b2/Untitled%201.png)
    
    효율성은 내가 쓴 코드가 더 좋음
    
1. 두 정수 사이의 합

- **문제 설명**

두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

- 제한 조건
    - a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
    - a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
    - a와 b의 대소관계는 정해져있지 않습니다.

- 나의 풀이
    
    ```jsx
    function solution(a, b) {
        
        // 작은 수(small)와 큰 수(big) 구분 후, 변수 생성
        let small = Math.min(a,b);
        let big = Math.max(a,b);
        
        // sum = 0
        let sum = 0;
        
        for(let i = small; i <= big; i++) {
            
            // small <= big 까지 sum += small 반복
            sum += i;
            }
        
        // 결과값 반환
        return sum;
    }
    ```
    
- 해답
    
    ```jsx
    function adder(a, b, s = 0){
      for (var i = Math.min(a, b); i <= Math.max(a, b); i++) s += i;
      return s;
    }
    ```