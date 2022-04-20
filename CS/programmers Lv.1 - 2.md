# programmers Lv.1 - 2

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
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled.png)
    

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
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%201.png)
    
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
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%202.png)
    
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
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%203.png)
    
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
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%204.png)
    

## K번째 수

배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

- 제한사항
    - array의 길이는 1 이상 100 이하입니다.
    - array의 각 원소는 1 이상 100 이하입니다.
    - commands의 길이는 1 이상 50 이하입니다.
    - commands의 각 원소는 길이가 3입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(arr, commands) {
        // 2차원 command = [[i, j, k], ... ]
        // arr를 j~j까지 자르고 -> 정렬 -> k번째 반환 = [k, k, k...]
        
        // arr에 [i, j, k] 적용하는 식
        // arr.slice(i-1,j+1).sort((a,b) => a-b)[k-1]
        
        // 위 식을 배열로 묶기
        return commands.map(e => arr.slice(e[0]-1,e[1]).sort((a,b) => a-b)[e[2]-1]);
        
    }
    ```
    

## 두 개 뽑아서 더하기

정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    - numbers의 길이는 2 이상 100 이하입니다.
    - numbers의 모든 수는 0 이상 100 이하입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(nums) {
        // 배열의 두 수 더한 값 배열
        
        // for: nums[i] + nums[j] -> arr 중복검사 -> 없으면 추가
        let arr = [];
        
        for(let i = 0; i < nums.length; i++) {
            for(let j = i + 1; j < nums.length; j++) {
                
                let sum = nums[i] + nums[j];
                if (!arr.includes(sum)) arr.push(sum);
            }
        }
        
        return arr.sort((a,b) => a-b);
    }
    ```
    

## 음양 더하기

어떤 정수들이 있습니다. 이 정수들의 절댓값을 차례대로 담은 정수 배열 absolutes와 이 정수들의 부호를 차례대로 담은 불리언 배열 signs가 매개변수로 주어집니다. 실제 정수들의 합을 구하여 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    - absolutes의 길이는 1 이상 1,000 이하입니다.
        - absolutes의 모든 수는 각각 1 이상 1,000 이하입니다.
    - signs의 길이는 absolutes의 길이와 같습니다.
        - `signs[i]` 가 참이면 `absolutes[i]` 의 실제 정수가 양수임을, 그렇지 않으면 음수임을 의미합니다.
        
- 나의 풀이
    
    ```jsx
    function solution(ab, s) {
        // absolutes => 절대값 배열
        // signs => 양(true), 음(false) 배열
        // 실제 정수의 합 반환
        
        // ab.map(e => s[i] 에 따라 +/ -)
        // return 배열의 합
        return ab.map((e, i) => s[i] ? +e : -e).reduce((sum,e) => sum += e, 0);
    }
    ```
    
- 다른 풀이
    
    ```jsx
    function solution(absolutes, signs) {
    
        return absolutes.reduce((acc, val, i) => acc + (val * (signs[i] ? 1 : -1)), 0);
    }
    ```
    

## 약수의 개수와 덧셈

두 정수 `left`와 `right`가 매개변수로 주어집니다. `left`부터 `right`까지의 모든 수들 중에서, 약수의 개수가 짝수인 수는 더하고, 약수의 개수가 홀수인 수는 뺀 수를 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    
    1 ≤ `left` ≤ `right` ≤ 1,000
    
- 나의 풀이
    
    ```jsx
    function solution(left, right) {
        // left ~ right 중
        // 약수 짝수인 수 = +n
        // 약수 홀수인 수 = -n
        // 모두 더한 숫자 반환
        
        let arr = [];
        
        // for: 숫자 하나씩 루프
        //  for: 숫자 2~n까지 나눔 -> 나머지=0 -> sum +1
        // sum % 2 = 0 -> arr.push(+i)
        // sum % 2 != 0 -> arr.push(-i)
        //arr 모든 후 합 반환
        
        for(let i = left; i <= right; i++) {
            
            let sum = 0;
            
            for(let j = 1; j <= i; j++) {
                
                if(i % j === 0) sum++; 
            }
            
            arr.push(sum % 2 ? -i : i);
        }
        
        return arr.reduce((ac,e) => ac += e, 0);
    }
    ```
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%205.png)
    
    ```jsx
    function solution(left, right) {
      let answer = 0;
    
      for (let i = left; i <= right; i++) {
        let count = 0;
        for (let j = 1; j <= i; j++) {
          if (i % j === 0) count++;
        }
        if (count % 2) answer -= i;
        else answer += i;
      }
    
      return answer;
    }
    ```
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%206.png)
    
    ```jsx
    function solution(left, right) {
        var answer = 0;
        for (let i = left; i <= right; i++) {
            if (Number.isInteger(Math.sqrt(i))) {
                answer -= i;
            } else {
                answer += i;
            }
        }
        return answer;
    }
    ```
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%207.png)
    

## 3진법 뒤집기

자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    
    n은 1 이상 100,000,000 이하인 자연수입니다.
    
- 나의 풀이
    
    ```jsx
    function solution(n) {
        // n (3진법) -> 뒤집음 -> 10진법
        return parseInt(n.toString(3).split("").reverse().join(""), 3);
    }
    ```
    
    ![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%208.png)
    
    ```jsx
    const solution = (n) => {
        return parseInt([...n.toString(3)].reverse().join(""), 3);
    }
    ```
    
    ```jsx
    function solution(n) {
        const answer = [];
        while(n !== 0) {
            answer.unshift(n % 3);
            n = Math.floor(n/3);
        }
        return answer.reduce((acc,v,i) => acc + (v * Math.pow(3, i)),0);   
    }
    ```
    

## 최소직사각형

명함 지갑을 만드는 회사에서 지갑의 크기를 정하려고 합니다. 다양한 모양과 크기의 명함들을 모두 수납할 수 있으면서, 작아서 들고 다니기 편한 지갑을 만들어야 합니다. 이러한 요건을 만족하는 지갑을 만들기 위해 디자인팀은 모든 명함의 가로 길이와 세로 길이를 조사했습니다.

아래 표는 4가지 명함의 가로 길이와 세로 길이를 나타냅니다.

| 명함 번호 | 가로 길이 | 세로 길이 |
| --- | --- | --- |
| 1 | 60 | 50 |
| 2 | 30 | 70 |
| 3 | 60 | 30 |
| 4 | 80 | 40 |

가장 긴 가로 길이와 세로 길이가 각각 80, 70이기 때문에 80(가로) x 70(세로) 크기의 지갑을 만들면 모든 명함들을 수납할 수 있습니다. 하지만 2번 명함을 가로로 눕혀 수납한다면 80(가로) x 50(세로) 크기의 지갑으로 모든 명함들을 수납할 수 있습니다. 이때의 지갑 크기는 4000(=80 x 50)입니다.

모든 명함의 가로 길이와 세로 길이를 나타내는 2차원 배열 sizes가 매개변수로 주어집니다. 모든 명함을 수납할 수 있는 가장 작은 지갑을 만들 때, 지갑의 크기를 return 하도록 solution 함수를 완성해주세요.

- 제한사항
    
    sizes의 길이는 1 이상 10,000 이하입니다.
    
    - sizes의 원소는 [w, h] 형식입니다.
    - w는 명함의 가로 길이를 나타냅니다.
    - h는 명함의 세로 길이를 나타냅니다.
    - w와 h는 1 이상 1,000 이하인 자연수입니다.
    
- 나의 풀이

```jsx
function solution(sizes) {
    // sizes = [w,h] 
    // 긴 길이 => size[0] / 짧은 길이 => size[1]
    // return size[0] 중 max * size[1] 중 max
    
    // w 배열 = sizes.map(size[0]의 최대값)
    // h 배열 = sizes.map(size[1]의 최소값)
    // return w의 배열의 최대값 * h배열의 최대값
    
    let w = sizes.map(e => Math.max.apply(null, e));
    let h = sizes.map(e => Math.min.apply(null, e));
    
    return Math.max.apply(null, w) * Math.max.apply(null, h);
}
```

![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%209.png)

```jsx
function solution(sizes) {
    let w = 0;
    let h = 0;
    sizes.forEach(s => {
        const [a, b] = s.sort((a,b) => a-b);
        if (a > h) h = a;
        if (b > w) w = b;
    });

    return w * h;
}
```

## 부족한 금액 계산하기

```jsx
function solution(price, money, count) {
    // count번째 요금 = count * price
    
    // 합계 금액 sum = 0
    // for 1<= i <= count
    // sum += price * i
    // money - sum => 양수 -> 0 / 음수 -> +음수
    
    let sum = 0;
    
    for(let i = 1; i <= count; i++) {
        sum += price * i;
    }
    
   return sum > money ? sum - money : 0;
}
```

![Untitled](programmers%20Lv%201%20-%202%20b336b660ba4f434b97a1d8a40fa2b7ee/Untitled%2010.png)

## 체육복

```jsx
function solution(n, lost, reserve) {
    // 전체 학생 2<= n <= 30
    // 도난 학생 1 <= lost <= n
    // 여벌 학생 1<= reserve <= n
    // 도난x, 여벌x => n - lost.length - reserve.length
    
    // 기본적으로 수업 듣기 가능한 수 => let sum = n - lost.length
    // for문 : 0 < i < reserve.length
    //      if (lost에 reserve[i] -1 포함)
    //          lost.splice(해당 인덱스, 1)
    //          sum ++
    //      else if(lost에 reserve[i] +1 포함)
    //          lost.splice(해당 인덱스, 1)
    //          sum ++
    //      else if(lost.length == 0) break;
    // return sum;
    
    let sum = n - lost.length;
    
    for (let i = 0; i < reserve.length; i++) {
        
        let minus = reserve[i] - 1;
        let plus = reserve[i] + 1;
        
        if(lost.length === 0) break;
        
        else if(lost.includes(reserve[i])) {
            lost.splice(lost.indexOf(reserve[i]),1);
        }
        
        else if(lost.includes(minus)) {
            lost.splice(lost.indexOf(minus),1);
            sum ++;
        } 
        else if(lost.includes(plus)) {
            lost.splice(lost.indexOf(plus),1);
            sum ++;
        }
        }
    return sum;
    }
```

```jsx
function solution(n, lost, reserve) {
    // 전체 학생 2<= n <= 30
    // 도난 학생 1 <= lost <= n
    // 여벌 학생 1<= reserve <= n
    // 도난x, 여벌x => n - lost.length - reserve.length
    
    // 여벌 있으면서 도난 맞은 사람 제외하고 새 배열 만들기
    let Lost = lost.filter(e => !reserve.includes(e));
    let Reserve = reserve.filter(e => !lost.includes(e));
    
    // 수업 듣기 확정 학생수
    let sum = n - Lost.length; 3
    
    for(let i = 0; i < Reserve.length; i++) {
        
        let rent = Lost.find(e => Math.abs(e - reserve[i]) === 1);
        
        if(rent) {
            Lost.filter(e => e !== rent);
            sum ++;
        }
            
    }
    
    return sum;
    }
```

```jsx
function solution(n, lost, reserve) {
    let arr = new Array(n+1).fill(1);
    
    // 주의 사항: arr[0] = 1 이니까 끝에 빼주기
    // 여분 학생 +1
    reserve.forEach(e => arr[e]++);
    
    // 도난 학생 -1
    lost.forEach(e => arr[e]--);
    
    // 도난 학생의 앞 = 2 -> 앞 = 1, 도난 학생 = 1
    // 도난 학생의 뒤 = 2 -> 뒤 = 1, 도난 학생 = 1
    
    for(let i = 0; i < n; i++) {
        
        if(arr[i] === 0 && arr[i+1] === 2) {
            arr[i] = 1;
            arr[i+1] = 1;
        }
        else if (arr[i] === 0 && arr[i-1] === 2) {
            arr[i] = 1;
            arr[i-1] = 1;
        }
    }
    
    return arr.filter(e => e > 0).length - 1;
        
        
    
    
}
```