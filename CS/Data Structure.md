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