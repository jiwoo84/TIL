# coding test

# 프로그래머스

## Level 1

1. **가운데 글자 가져오기**
    
    단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.
    
    - 제한사항
        
        s는 길이가 1 이상, 100이하인 스트링입니다.
        
    
    - 해답
        
        ```c
        function solution(s) {
            return s.substr(Math.ceil(s.length / 2) - 1, s.length % 2 === 0 ? 2 : 1);
        }
        ```
        
        s.substr 을 사용하면 된다는 것을 캐치하고 공통된 부분을 찾아 적는게 중요할듯...
        
2. **같은 숫자는 싫어**
    
    배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,
    
    arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
    
    arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
    
    배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.
    
    - 제한사항
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
    

1. **나누어 떨어지는 숫자 배열**
    
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
    
    ![Untitled](coding%20tes%20f41b2/Untitled.png)
    

- 다른 풀이
    
    ```jsx
    function solution(arr, divisor) {
        var answer = arr.filter(v => v%divisor == 0);
        return answer.length == 0 ? [-1] : answer.sort((a,b) => a-b);
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%201.png)
    
    효율성은 내가 쓴 코드가 더 좋음
    
1. **두 정수 사이의 합**
    
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
        
    

1. **문자열 내 마음대로 정렬하기**
    
    문자열로 구성된 리스트 strings와, 정수 n이 주어졌을 때, 각 문자열의 인덱스 n번째 글자를 기준으로 오름차순 정렬하려 합니다. 예를 들어 strings가 ["sun", "bed", "car"]이고 n이 1이면 각 단어의 인덱스 1의 문자 "u", "e", "a"로 strings를 정렬합니다.
    
    - 제한 조건
        - strings는 길이 1 이상, 50이하인 배열입니다.
        - strings의 원소는 소문자 알파벳으로 이루어져 있습니다.
        - strings의 원소는 길이 1 이상, 100이하인 문자열입니다.
        - 모든 strings의 원소의 길이는 n보다 큽니다.
        - 인덱스 1의 문자가 같은 문자열이 여럿 일 경우, 사전순으로 앞선 문자열이 앞쪽에 위치합니다.

- 풀이
    
    ```jsx
    function solution(strings, n) {
        
        return strings.sort((a,b) => a[n] == b[n] ? a.localeCompare(b) : a[n].localeCompare(b[n]));
        
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%202.png)
    
1. **문자열 내 p와 y의 개수**
    
    대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.
    
    예를 들어 s가 "pPoooyY"면 true를 return하고 "Pyy"라면 false를 return합니다.
    

- 제한사항
    - 문자열 s의 길이 : 50 이하의 자연수
    - 문자열 s는 알파벳으로만 이루어져 있습니다.

- 나의 풀이
    
    ```jsx
    function solution(s){
        // s를 소문자로 변경하고 배열 만들기
        let arr = s.toLowerCase().split("");
        
        // if p의 개수 = y의 개수 => return true
        // 개수 계산 : array.reduce로 요소 발견 시마다 sum += 1
        let p = arr.reduce((sum,value) => value == "p" ? sum + 1: sum, 0);
        let y = arr.reduce((sum,value) => value == "y" ? sum + 1: sum, 0);
        
        
        if(p == y) {
            return true;
        } 
        // else if => return false
        return false;
        
        // p,y의 개수 = 0 일 때, 에러 발생하면 맨 위에 경우의 수 추가
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%203.png)
    

- 다른 풀이
    
    ```jsx
    function numPY(s){
      //함수를 완성하세요
        return s.toUpperCase().split("P").length === s.toUpperCase().split("Y").length;
    }
    ```
    

1. **문자열 내림차순으로 배치하기**
    
    문자열 s에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수, solution을 완성해주세요.s는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.
    
    - 제한 사항
        
        str은 길이 1 이상인 문자열입니다.
        

- 나의 풀이
    
    ```jsx
    function solution(s) {
        // 소문자만 배열 -> 사전순 정렬 -> 역순 정렬
        let lowerArr = s.split("").filter(v => v == v.toLowerCase()).sort((a,b) => a.localeCompare(b)).reverse();
        
        // 대문자만 배열 -> 사전순 정렬 -> 역순 정렬
        let upperArr = s.split("").filter(v => v == v.toUpperCase()).sort((a,b) => a.localeCompare(b)).reverse();
        
        return lowerArr.concat(upperArr).join("");
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%204.png)
    
- 다른 풀이
    
    ```jsx
    function solution(s) {
      return s
        .split("")
        .sort()
        .reverse()
        .join("");
    }
    ```
    
    `sort()` : 대문자, 소문자 순으로 정렬
    
    `sort((a,b) ⇒ a.localeCompare(b))` : 소문자, 대문자 순으로 정렬
    
    ```jsx
    function solution(s) {
      return s.split('').sort((prev, cur) => cur.charCodeAt() - prev.charCodeAt()).join('');
    }
    ```
    
1. **문자열 다루기 기본**
    
    문자열 s의 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수, solution을 완성하세요. 예를 들어 s가 "a234"이면 False를 리턴하고 "1234"라면 True를 리턴하면 됩니다.
    
    - 제한 사항
        
        `s`는 길이 1 이상, 길이 8 이하인 문자열입니다.
        
    - 나의 풀이
        
        ```jsx
        function solution(s) {
            // 문자열 길이 == 4 or 6 확인
            if (s.length == 4 || s.length == 6) {
                for(let v of s) {
                    if(isNaN(v) == true) return false;
                } return true;
            } return false;
        }
        ```
        
        ![Untitled](coding%20tes%20f41b2/Untitled%205.png)
        
    - 다른 풀이
        
        ```jsx
        function solution(s) {
          return /^[0-9]+$/.test(s) && [4,6].includes(s.length);
        }
        ```
        
        `(s.length === 4 || s.length === 6)`
         대신 includes로 짧게 줄일 수 있다!!
        
2. **소수 찾기**
    
    1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.
    
    소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.(1은 소수가 아닙니다.)
    
    - 제한 조건
        
        n은 2이상 1000000이하의 자연수입니다.
        
    - 나의 풀이
        
        ```jsx
        function solution(n) {
            // 배열 생성 (2이상이므로 1개 확보)
            let result = 1;
            
            // for문 (3~n까지 하나씩 대입)
            for (let i = 3; i <= n; i++) {
                
            // for문 (i 나누기 2~n-1 => 나머지 0이면 빠져나감)
                for (let j = 2; j < i; j++) {
                    if(i % j == 0) break;
                    // n-1까지 나눴는데 나머지가 있다면 배열에 추가
                    else if(j == i-1) result ++;
                }
            }
            return result;
        
        ```
        
        ![Untitled](coding%20tes%20f41b2/Untitled%206.png)
        
    
    - 다른 풀이
        
        ```jsx
        function solution(n) {
            // n+1 길이/ true로 채운 배열 생성
            let arr = new Array(n+1).fill(true);
            
            // let end = n의 제곱근
            let end = Math.sqrt(n);
            
            let result = 0;
            
            // for(let i=2; i <= end; i++)
            for(let i = 2; i <= end; i++) {
                
                // if arr[i] == false -> 넘어감
                if(arr[i] === false) continue;
                
            // for(let j = i*i; j <= n; j += i) -> arr[j] = false
                for(let j = i*i; j <= n; j += i) {
                    arr[j] = false;
                }
            }
        
            // 소수의 갯수를 구한다.
            for(let i = 2; i <= n; ++i){
                if(arr[i] === true){
                    result++;
                }
            }
            return result;
        }
        ```
        

**11. 행렬의 덧셈**

행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

- 제한조건
    
    행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.
    
- 다른 풀이
    
    ```jsx
    function solution(arr1, arr2) {
        var answer = [];
        for (var i=0; i<arr1.length; i++){
            answer[i] =[];
            for(var j=0; j<arr1[i].length; j++){
                answer[i].push(arr1[i][j] + arr2[i][j]);
            }
        }
        return answer;
    }
    ```
    
    머릿속에서 그려보는데 굉장히 고생했다...
    
    ![Untitled](coding%20tes%20f41b2/Untitled%207.png)
    
    ![Untitled](coding%20tes%20f41b2/Untitled%208.png)
    
    화살표 함수로 간단히 줄이면,,,
    
    ```jsx
    function sumMatrix(A,B){
    
        return A.map((a,i) => a.map((b, j) => b + B[i][j]));
    }
    ```
    
1. 시저암호

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

- 제한 조건
    - 공백은 아무리 밀어도 공백입니다.
    - s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
    - s의 길이는 8000이하입니다.
    - n은 1 이상, 25이하인 자연수입니다.

- 나의 풀이
    
    (1차 풀이)
    
    ```jsx
    function solution(s, n) {
        // 유니코드 A = 65 / Z = 90 / a = 97 / z = 122
        let arr = [];
        
        for(let i = 0; i < s.length; i++) {
    
            let unicode = s.charCodeAt(i) + n;
            
            if ( (unicode > 64 || unicode < 91) || (unicode > 96 || unicode < 123)) {
                
            //    arr.push(unicode -> str)
                arr.push(String.fromCharCode(unicode));
                
            } else if ( (unicode > 90 || unicode < 97) || (unicode > 122 || unicode < 148)) {
            //    arr.push(unicode-26 -> str)
                arr.push(String.fromCharCode(unicode-26));
                
            } 
            else arr.push(" ")
        }
        
        // return arr -> str
        return arr.join("");
        
    }
    ```
    
    에러 발생
    
    (복잡한 조건문이 원인으로 추정)
    
    유니코드 A = 65 / Z = 90 / a = 97 / z = 122
    
    - 예외사항
        1. “” ⇒ “” 반환
        2. 90 < uni + n || 122 < uni+n ⇒ uni -26 하고 배열 추가
    
1. 약수의 합

정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

- 제한 사항
    
    `n`은 0 이상 3000이하인 정수입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(n) {
        
        let arr = [];
        // n % i == 0 인 값으로 배열 생성
        // 1. for문 -> n % i == o ? arr.push : continue;
        for(let i = 0; i <= n; i++) {
            if (n % i === 0) arr.push(i);
            else continue;
        }
        // 배열값 모두 더하기
        // 1. reduce로 더하기
        return arr.reduce((sum, el) => sum + el, 0)
    }
    ```
    

1. 이상한 문자 만들기

문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

- 제한 사항
    - 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
    - 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.
    
- 나의 풀이
    
    ```jsx
    function solution(s) {
        // s = 한 개 이상의 단어 str
        // 각 단어 = 하나 이상의 공백문자
        // 함수 (단어의 짝수번째 -> 대문자 / 홀수번째 -> 소문자)
        
        // s를 단어별로 나눈 arr 생성
        //  1. arr.split(" ") => [Hello, world]
        let arr = s.split(" ");
        
        // arr[i]를 또 배열로 => 짝수인덱스 -> 대문자 / 홀수인덱스 -> 소문자 => str
        //  1. arr[i].split("").map((e, i => i%2 === 0 ? ~)).join
        //  arr[i].split("").map((e,i) => i%2 ===0? e.toUpperCase() : e).join("")
        
        // arr[i]를 공백 있게 str으로 합침
        //  2. for문으로 돌리지 말고 합치기 (map시도)
        return arr.map(e => e.split("").map((e,i) => i%2 ===0? e.toUpperCase() : e.toLowerCase()).join("")).join(" ");
        
    }
    ```
    
1. 자릿수 더하기

자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

- 제한사항
    
    N의 범위 : 100,000,000 이하의 자연수
    
- 나의 풀이

```jsx
function solution(n)
{
    // n = 자연수
    // 함수(return n의 각 자릿수의 합)
    
    return String(n).split("").reduce((sum,e) => sum + +e, 0);
}
```

1. 자연수 뒤집어 배열로 만들기

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

- 제한 조건
    
    n은 10,000,000,000이하인 자연수입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(n) {
        // n -> 문자열 -> 배열 -> reverse -> 요소를 숫자로 변경
        return String(n).split("").reverse().map(e => +e);
    }
    ```
    
1. 정수 내림차순으로 배치하기

함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

- 제한 조건
    
    `n`은 1이상 8000000000 이하인 자연수입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(n) {
        // 정수의 자릿수 큰 -> 작은 순서대로 정렬한 새 정수 반환
        
        // n -> str -> arr -> sort(역순) -> str -> num
        return + String(n).split("").sort((a,b) => b - a).join('');
    }
    ```
    
1. 정수 제곱근 판별

임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

- 제한 사항
    
    n은 1이상, 50000000000000 이하인 양의 정수입니다.
    
- 나의 풀이

```jsx
function solution(n) {
    // n = 양의 정수 / x = 임의의 양의 정수
    // if (n = x의 제곱) => (x+1)^2 반환
    // else -1 반환
    
		//예외처리
		if (n == 1) return 4;

    // for(2부터 n까지, i++)
    for(let i = 2; i < n; i++) {
        
    // if ( i * i === n) => return (i+1)^2
        if(i*i === n) return (i+1) * (i+1);
        
    // if ( i * i > n) break;
        else if(i*i > n) break;
    }
    // else -1 반환
    return -1;
}
```

![Untitled](coding%20tes%20f41b2/Untitled%209.png)

- 해답

```jsx
function solution(n) {
    // n = 양의 정수 / x = 임의의 양의 정수
    // if (n = x의 제곱) => (x+1)^2 반환
    // else -1 반환
    
    // if (n의 제곱근 === n의 제곱근.floor) => (n의 제곱근+1)^2
    // else return -1
    let x = Math.sqrt(n);
    return (x === Math.floor(x)) ? (x+1)*(x+1) : -1;
}
```

![Untitled](coding%20tes%20f41b2/Untitled%2010.png)

1. 제일 작은 수 제거하기

정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

- 제한 조건
    - arr은 길이 1 이상인 배열입니다.
    - 인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(arr) {
        
        // return 제일작은수 삭제한 배열
        // 빈 배열 => return -1
        let result = arr.slice(0);
    
        // arr = arr.filter((정렬->가장작은값)아닌 요소)
        result = result.filter(i => i !== arr.sort((a,b) => a - b)[0]);
        
        // if (arr.length === 0) return [-1];
        if (result.length === 0) return [-1];
        
        // else return arr;
        return result;
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2011.png)
    
    ```jsx
    function solution(arr) {
        
        // return 제일작은수 삭제한 배열
        // 빈 배열 => return -1
        
        // 최소값 = Math.min(arr요소)
        // return arr.filter(최소값 아닌 수)
        arr = arr.filter(e => e !== Math.min.apply(null, arr));
        
        return arr.length === 0 ? [-1] : arr;
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2012.png)
    

1. 최소공배수와 최대공배수
    
    두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.
    
    - 제한 사항
        
        두 수는 1이상 1000000이하의 자연수입니다.
        
    - 유클리드 호제법
        
        최대공약수를 구하는 알고리즘
        
        (큰 값 max , 작은 값 min)
        
        1. max % min = e(1)
        2. min % e(1) = e(2)
        3. e(1) % e(2) = e(3)
            
            ⋮
            
            e(n-1) % e(n) = 0
            
        - 최대공약수 = e(n)
        - 최소공배수 = (max * min) /e(n)
            
            
    - 나의 풀이
    
    ```jsx
    function solution(n, m) {
        // 두 수의 [최대공약수, 최소공배수] 배열 반환
        
        // max = 큰값 , min = 작은값
        let max = Math.max(n,m);
        let min = Math.min(n,m);
        // a = 최대공약수 , b = 최소공배수
        
        // 최대공약수 (유클리드의 호제법)
        function u(i, j) {
            let e = i % j;
            if (e === 0) return j;
            return u(j, e);
            }
        
        // 최대공배수
        // max * min / u(max, min)
        
        return [u(max,min), max * min / u(max,min)];
    }
    ```
    
    - 간단한 풀이
    
    ```jsx
    function solution(n, m) {
      function u(n, m) { return m % n ? u(m % n, n) : n; }
      const gcd = u(n, m);
      return [gcd, n * m / gcd];
    }
    ```
    

### 콜라츠 추측

1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될때까지 다음 작업을 반복하면, 모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다.

`1-1. 입력된 수가 짝수라면 2로 나눕니다. 
1-2. 입력된 수가 홀수라면 3을 곱하고 1을 더합니다.
2. 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다.`

예를 들어, 입력된 수가 6이라면 6→3→10→5→16→8→4→2→1 이 되어 총 8번 만에 1이 됩니다. 위 작업을 몇 번이나 반복해야하는지 반환하는 함수, solution을 완성해 주세요. 단, 작업을 500번을 반복해도 1이 되지 않는다면 –1을 반환해 주세요.

- 제한 사항
    
    입력된 수, `num`은 1 이상 8000000 미만인 정수입니다.
    

- 나의 풀이
    
    ```jsx
    function solution(num) {
        
      // let sum = 0; 
      // 함수 p
      // 과정마다 sum + 1;
      // if (num === 1) return sum;
      // if (num 짝수) => return p(num / 2)
      // if (num 홀수) => return p(num * 3 + 1)
    
      let sum = -1;
      
      function p(num) {
    
          sum++;
    
          if (sum === 500) return -1;
          else if (num === 1) return sum;
          else if (num % 2 === 0) return p(num / 2);
          else if (num % 2 !== 0) return p(num * 3 + 1);
          }
      
      return p(num);
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2013.png)
    
- 다른 풀이
    
    ```jsx
    function solution(num, count = 0) {
        return count === 500 
            ? -1 
            : num === 1
                ? count
                : solution(num % 2 ? num * 3 + 1 : num / 2, count + 1);
    }
    ```
    

### 하샤드 수

양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.

- 제한 조건
    
    `x`는 1 이상, 10000 이하인 정수입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(x) {
        
        // 자릿수 합 / X = 0 => true
        
        // 자릿수 합 구하기
        // // x -> 문자열 -> 배열 -> 모든값 더하기
        // x % 자릿수 합 == 0 => return true;
        return x % String(x).split("").reduce((sum, e) => sum + (+e), 0) ? false : true;
        
    }
    ```
    
    e를 꼭 숫자형으로 바꿔줘야 한다
    
- 다른 풀이
    
    ```jsx
    function solution(x) {
        return !(x % String(x).split('').reduce((a, c) => a + c * 1, 0));
    }
    ```
    

### 핸드폰 번호 가리기

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 `*`으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

- 제한 조건
    
    phone_number는 길이 4 이상, 20이하인 문자열입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(num) {
        // 뒤 4자리만 빼고 *처리한 문자열 반환
        
        // str -> arr -> 인덱스 -5부터 -arr.length까지 *로 변경 -> str
        let arr = num.split('')
        
        for (let i = -5; i >= -arr.length; i--) {
           arr.splice(i, 1 , "*");
        }
        
        return arr.join("");
    }
    ```
    

### x만큼 간격이 있는 n개의 숫자

함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

- **제한 조건**
    - x는 -10000000 이상, 10000000 이하인 정수입니다.
    - n은 1000 이하인 자연수입니다.

- 나의 풀이
    
    ```jsx
    function solution(x, n) {
        //  return 배열[x의 배수 n개]
        
        // reduce. (1 < i <= n) * x 배열에 push
        let arr = [];
        
        for(let i = 1; i <= n; i++) {
            arr.push(x * i);
        }
       
        return arr;
    }
    ```
    

### 2016년

2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각 `SUN,MON,TUE,WED,THU,FRI,SAT`

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.

- 제한 조건
    - 2016년은 윤년입니다.
    - 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)
    
- 나의 풀이
    
    ```jsx
    function solution(a, b) {
        // new date()로 날짜 얻기 -> getDay()로 요일 -> 글자로 반환
        let week = ["SUN","MON","TUE","WED","THU","FRI","SAT"];
        return week[new Date(2016, a-1, b).getDay()];
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2014.png)
    

- 다른 풀이
    
    ```jsx
    function getDayName(a,b){
      let date = new Date(2016, (a - 1), b);
        return date.toString().slice(0, 3).toUpperCase();
    }
    ```
    

## 숫자열과 영단어

네오와 프로도가 숫자놀이를 하고 있습니다. 네오가 프로도에게 숫자를 건넬 때 일부 자릿수를 영단어로 바꾼 카드를 건네주면 프로도는 원래 숫자를 찾는 게임입니다.다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다.

- 1478 → "one4seveneight"
- 234567 → "23four5six7"
- 10203 → "1zerotwozero3"

이렇게 숫자의 일부 자릿수가 영단어로 바뀌어졌거나, 혹은 바뀌지 않고 그대로인 문자열 `s`가 매개변수로 주어집니다. `s`가 의미하는 원래 숫자를 return 하도록 solution 함수를 완성해주세요.

참고로 각 숫자에 대응되는 영단어는 다음 표와 같습니다.

- 제한사항
    - 1 ≤ `s`의 길이 ≤ 50
    - `s`가 "zero" 또는 "0"으로 시작하는 경우는 주어지지 않습니다.
    - return 값이 1 이상 2,000,000,000 이하의 정수가 되는 올바른 입력만 `s`로 주어집니다.
    
- 풀이
    
    ```jsx
    function solution(s) {
        
        let numbers = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"];
        
        // 변수에 초기 s 저장
        let result = s;
        
        // for문
        for(let i = 0; i < numbers.length; i++) {
            
        // 문자열 찾아서 분리된 배열 생성
            let arr = result.split(numbers[i]);
            
        // 배열 -> 문자열 result에 저장
            result = arr.join(i);
        }
    
        return Number(result);
        }
    ```
    

## 없는 숫자 더하기

0부터 9까지의 숫자 중 일부가 들어있는 정수 배열 `numbers`가 매개변수로 주어집니다. `numbers`에서 찾을 수 없는 0부터 9까지의 숫자를 모두 찾아 더한 수를 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    
    1 ≤ `numbers`의 길이 ≤ 9
    
    - 0 ≤ `numbers`의 모든 원소 ≤ 9
    - `numbers`의 모든 원소는 서로 다릅니다.
    
- 나의 풀이
    
    ```jsx
    function solution(numbers) {
        // 0~9 중 없는 숫자 더한 값 반환
        let list = [0,1,2,3,4,5,6,7,8,9]
        
        // list에서 numbers의 값 하나씩 지우기
        for (let i = 0; i < numbers.length; i++) {
                    
            list.splice(list.indexOf(numbers[i]), 1)
    
            }
        
        // 요소 전체 더하기
        return list.reduce((sum,e) => sum += e, 0);
        }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2015.png)
    
- 다른 풀이
    
    ```jsx
    function solution(numbers) {
        return 45 - numbers.reduce((cur, acc) => cur + acc, 0);
    }
    ```
    
    총 합을 빼주면 됐었는데... 이럴수가
    
    ```jsx
    function solution(numbers) {
        let answer = 0;
    
        for(let i = 0; i <= 9; i++) {
            if(!numbers.includes(i)) answer += i;
        }
    
        return answer;
    }
    ```
    

## 소수 만들기

주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    - nums에 들어있는 숫자의 개수는 3개 이상 50개 이하입니다.
    - nums의 각 원소는 1 이상 1,000 이하의 자연수이며, 중복된 숫자가 들어있지 않습니다.
    
- 나의 풀이
    
    ```jsx
    function solution(nums) {
        
        let answer = 0;
        // for: 세 개의 숫자 더하기 (모든 경우의 수 반복)
        //  변수 => index
        for(let i = 0; i < nums.length; i++) {
            for(let j = i + 1; j < nums.length; j++) {
                for (let k = j + 1; k < nums.length; k++) {
                    
                    let sum = nums[i] + nums[j] + nums[k];
                    
                    // 더한 수가 소수인지 확인
                    for(let l = 2; l < sum; l++) {
                        //  소수x -> continue;
                        if (sum % l === 0) break;
                         //  소수 -> answer + 1
                        else if (l === sum -1) answer+= 1;
                    }
                }
            }
        }
        return answer;
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2016.png)
    
    ```jsx
    function solution(nums) {
        
        let answer = 0;
        // for: 세 개의 숫자 더하기 (모든 경우의 수 반복)
        //  변수 => index
        for(let i = 0; i < nums.length; i++) {
            for(let j = i + 1; j < nums.length; j++) {
                for (let k = j + 1; k < nums.length; k++) {
                    
                    let sum = nums[i] + nums[j] + nums[k];
                    
                    // 더한 수가 소수인지 확인
                    if(isPrime(sum)) answer += 1;
                    }
                }
            }
    		return answer;
        
        function isPrime(n) { // 소수 판별 함수
            for(let i = 2; i < n; i++) {
                if(n % i === 0) return false;
            }
            return true;
        }
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2017.png)
    
    ```jsx
    function solution(nums) {
        
        let answer = 0;
        // for: 세 개의 숫자 더하기 (모든 경우의 수 반복)
        //  변수 => index
        for(let i = 0; i < nums.length; i++) {
            for(let j = i + 1; j < nums.length; j++) {
                for (let k = j + 1; k < nums.length; k++) {
                    
                    let sum = nums[i] + nums[j] + nums[k];
                    
                    // 더한 수가 소수인지 확인
                    if(isPrime(sum)) answer += 1;
                    }
                }
            }
    		return answer;
        
        function isPrime(n) { // 소수 판별 함수
            for(let i = 2; i <= Math.sqrt(n); i++) {
                if(n % i === 0) return false;
            }
            return true;
        }
    }
    ```
    
    ![Untitled](coding%20tes%20f41b2/Untitled%2018.png)