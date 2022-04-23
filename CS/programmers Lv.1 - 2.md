# programmers Lv.1 - 2

### 하샤드 수

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

- 나의 풀이
    
    ```jsx
    function solution(a, b) {
        // new date()로 날짜 얻기 -> getDay()로 요일 -> 글자로 반환
        let week = ["SUN","MON","TUE","WED","THU","FRI","SAT"];
        return week[new Date(2016, a-1, b).getDay()];
    }
    ```
    

- 다른 풀이
    
    ```jsx
    function getDayName(a,b){
      let date = new Date(2016, (a - 1), b);
        return date.toString().slice(0, 3).toUpperCase();
    }
    ```
    

## 숫자열과 영단어

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
    
    ![Untitled](programmers%20Lv%201%20-%202%208c92c1b40f1149a1a2796321fd7f5685/Untitled.png)
    
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
    
    ![Untitled](programmers%20Lv%201%20-%202%208c92c1b40f1149a1a2796321fd7f5685/Untitled%201.png)
    
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
    
    ![Untitled](programmers%20Lv%201%20-%202%208c92c1b40f1149a1a2796321fd7f5685/Untitled%202.png)
    

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
    
    ![Untitled](programmers%20Lv%201%20-%202%208c92c1b40f1149a1a2796321fd7f5685/Untitled%203.png)
    
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

![Untitled](programmers%20Lv%201%20-%202%208c92c1b40f1149a1a2796321fd7f5685/Untitled%204.png)

## 체육복

- 

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

    for(let i = 1; i <= n; i++) {
        
        if(arr[i] === 0 && arr[i-1] === 2) {
            arr[i]++;
            arr[i-1]--;
        }
        else if (arr[i] === 0 && arr[i+1] === 2) {
            arr[i]++;
            arr[i+1]--;
        }
    }
    
    return arr.filter(e => e > 0).length -1;
    
}
```

### 다트게임

카카오톡 게임별의 하반기 신규 서비스로 다트 게임을 출시하기로 했다. 다트 게임은 다트판에 다트를 세 차례 던져 그 점수의 합계로 실력을 겨루는 게임으로, 모두가 간단히 즐길 수 있다.갓 입사한 무지는 코딩 실력을 인정받아 게임의 핵심 부분인 점수 계산 로직을 맡게 되었다. 다트 게임의 점수 계산 로직은 아래와 같다.

1. 다트 게임은 총 3번의 기회로 구성된다.
2. 각 기회마다 얻을 수 있는 점수는 0점에서 10점까지이다.
3. 점수와 함께 Single(`S`), Double(`D`), Triple(`T`) 영역이 존재하고 각 영역 당첨 시 점수에서 1제곱, 2제곱, 3제곱 (점수 , 점수 , 점수 )으로 계산된다.
    
    1
    
    2
    
    3
    
4. 옵션으로 스타상(`*`), 아차상(`#`)이 존재하며 스타상(`*`) 당첨 시 해당 점수와 바로 전에 얻은 점수를 각 2배로 만든다. 아차상(`#`) 당첨 시 해당 점수는 마이너스된다.
5. 스타상`` 첫 번째 기회에서도 나올 수 있다. 이 경우 첫 번째 스타상(``)의 점수만 2배가 된다. (예제 4번 참고)
6. 스타상(``)의 효과는 다른 스타상(``)의 효과와 중첩될 수 있다. 이 경우 중첩된 스타상(``) 점수는 4배가 된다. (예제 4번 참고)
7. 스타상(``)의 효과는 아차상(`#`)의 효과와 중첩될 수 있다. 이 경우 중첩된 아차상(`#`)의 점수는 -2배가 된다. (예제 5번 참고)
8. Single(`S`), Double(`D`), Triple(`T`)은 점수마다 하나씩 존재한다.
9. 스타상(``), 아차상(`#`)은 점수마다 둘 중 하나만 존재할 수 있으며, 존재하지 않을 수도 있다.

0~10의 정수와 문자 S, D, T, *, #로 구성된 문자열이 입력될 시 총점수를 반환하는 함수를 작성하라.

- **입력 형식**
    
    "점수|보너스|[옵션]"으로 이루어진 문자열 3세트.예) `1S2D*3T`
    
    - 점수는 0에서 10 사이의 정수이다.
    - 보너스는 S, D, T 중 하나이다.
    - 옵선은 *이나 # 중 하나이며, 없을 수도 있다.
    
- **출력 형식**
    
    3번의 기회에서 얻은 점수 합계에 해당하는 정수값을 출력한다.예) 37
    

```jsx
function solution(s) {
    // ** 정리 **
    
    // 한 번에 얻을 수 있는 점수 : 0~10점 / 3번의 기회

    // S = 1, D = 2, T = 3제곱 (점수마다 있음)
    // * = 직전 점수 x 2, 해당 점수 x 2
    // # = 해당 점수 x -1
    
    // <체크사항>
    // * 중첩 시, x 4
    // *# 중첩 시, x -2
    // 숫자 10에 주의
    
    // 문자열 => return 총점수
    //---
        
    // 계산 값 배열 생성 arr = []
    let arr = []
    
    //  숫자값 변수 생성 let num 
    let num = 0;
    
    // for문
    for (let i = 0; i < s.length; i++) {
    //  if (s[i] = 숫자) => num = s[i]
        if (i === s.length) arr.push(num);
        
        else if(!isNaN(s[i])) {
            arr.push(num);
            
            num = s[i] === "1" && s[i+1] === "0" ? 10 : Number(s[i]); 
        }
    //  else if (s[i] = S,D,T) => (삼항연산자) num = Math.pow(num,s[i]);
        else if(s[i] === "S") num = num;
        else if(s[i] === "D") num = Math.pow(num,2);
        else if(s[i] === "T") num = Math.pow(num,3);
        
    //  else if (s[i] = "*") => arr[arr.length -1] *= 2 / num * 2
        else if(s[i] === "*") {
            arr[arr.length -1] *= 2;
            num *= 2;

    //          (s[i] = "#") => num * -1
        } else if (s[i] === "#") num *= -1;
        
    }
              
    // 총합 반환
    return arr.reduce((sum,e) => sum += e, 0);
}
```

```jsx
function solution(s) {
    // ** 정리 **
    
    // 한 번에 얻을 수 있는 점수 : 0~10점 / 3번의 기회

    // S = 1, D = 2, T = 3제곱 (점수마다 있음)
    // * = 직전 점수 x 2, 해당 점수 x 2
    // # = 해당 점수 x -1
    
    // <체크사항>
    // * 중첩 시, x 4
    // *# 중첩 시, x -2
    // 숫자 10에 주의
    
    // 문자열 => return 총점수
    //---
        
    // 계산 값 배열 생성 arr = []
    let arr = []
    
    //  숫자값 변수 생성 let num 
    let num = 0;
    
    // for문
    for (let i = 0; i < s.length; i++) {
        
    //  if (s[i] = 숫자) => num = s[i]
        if(!isNaN(s[i])) {
            
            num = s[i-1] === "1" ? 10 : Number(s[i]); 
        }
    //  else if (s[i] = S,D,T) => (삼항연산자) num = Math.pow(num,s[i]);
        else if(s[i] === "S") arr.push(num);
        else if(s[i] === "D") arr.push(Math.pow(num,2));
        else if(s[i] === "T") arr.push(Math.pow(num,3));
        
    //  else if (s[i] = "*") => arr[arr.length -1] *= 2 / num * 2
        else if(s[i] === "*") {
            arr[arr.length -1] *= 2;
            arr[arr.length -2] *= 2;

    //          (s[i] = "#") => num * -1
        } else if (s[i] === "#") arr[arr.length -1] *= -1;
        
    }
              
    // 총합 반환
    return arr.reduce((sum,e) => sum + e, 0);
}
```

## 모의고사

- 나의 풀이

```jsx
function solution(answers) {
    // 1 = [1,2,3,4,5] ...
    // 2 = [2, 1, 2, 3, 2, 4, 2, 5]...
    // 3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5]...
    
    // 1 ~ 3의 배열 만들기
    
   let makeArr = (pattern, arr = []) => {

        for(let i = 0; i < answers.length; i++) {
            arr.push(pattern[i % pattern.length]);
        }
        return arr;
    }
    
    let arr1 = makeArr([1, 2, 3, 4, 5]);
    let arr2 = makeArr([2, 1, 2, 3, 2, 4, 2, 5]);
    let arr3 = makeArr([3, 3, 1, 1, 2, 2, 4, 4, 5, 5]);

    // 정답 수 세기
    
    let result1 = arr1.reduce((acc, e, i) => acc += answers[i] === e ? 1 : 0 , 0);
    let result2 = arr2.reduce((acc, e, i) => acc += answers[i] === e ? 1 : 0 , 0);
    let result3 = arr3.reduce((acc, e, i) => acc += answers[i] === e ? 1 : 0 , 0);
    
    // 가장 큰 값 반환 (여러명이면 오름차순)
    let results = [result1, result2, result3];
    let maxIndexs = [];
    
    for (let i = 0; i < 3; i++) {
        
        if (results[i] === Math.max.apply(null, results)) maxIndexs.push(i + 1);
    }
    
    return maxIndexs;
    
}
```

- 모범 답안

```jsx
function solution(answers) {
    var answer = [];
    var a1 = [1, 2, 3, 4, 5];
    var a2 = [2, 1, 2, 3, 2, 4, 2, 5]
    var a3 = [ 3, 3, 1, 1, 2, 2, 4, 4, 5, 5];

    var a1c = answers.filter((a,i)=> a === a1[i%a1.length]).length;
    var a2c = answers.filter((a,i)=> a === a2[i%a2.length]).length;
    var a3c = answers.filter((a,i)=> a === a3[i%a3.length]).length;
    var max = Math.max(a1c,a2c,a3c);

    if (a1c === max) {answer.push(1)};
    if (a2c === max) {answer.push(2)};
    if (a3c === max) {answer.push(3)};

    return answer;
}
```

![Untitled](programmers%20Lv%201%20-%202%208c92c1b40f1149a1a2796321fd7f5685/Untitled%205.png)

```jsx
function solution(answers) {
    var answer = [];
    const man1 = [1, 2, 3, 4, 5];
    const man2 = [2, 1, 2, 3, 2, 4, 2, 5];
    const man3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5];
    let count = [0, 0, 0];

    for(let i = 0; i < answers.length; i++) {
        if(answers[i] == man1[i % man1.length]) count[0]++;
        if(answers[i] == man2[i % man2.length]) count[1]++;
        if(answers[i] == man3[i % man3.length]) count[2]++;
    }

    const max = Math.max(count[0], count[1], count[2]);
    for(let i = 0; i < count.length; i++) {
        if(max == count[i]) answer.push(i + 1);
    }

    return answer;
}
```

1. 문제 정리
2. 떠오르는 방법 모두 적기
3. 가장 효율 좋을 것 같은거 해보기