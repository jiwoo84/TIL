# 1. basic

---

# 기본

## **git**

파일의 변경내역을 추적해주는 version control system

## **github**

git으로 관리하는 파일, 변경 내역을 올리는 공간

- repositoy: 코드의 변경내역,히스토리를 갖고 있는 폴더
    
    (이름은 공백x, 소문자)
    

## 기본 명령어

- `git version` : git의 버전 확인
- `git config (--global) user.name "<이름>"` : git관련 작업 기록에 남는 이름 설정/수정
    
    `git config (--global) user.email "<이름>"` : git관련 작업 기록에 남는 이메일 설정/수정
    
    (디렉토리 설정 전에는 `--global` 넣어야 함)
    
- `git config --list` : git 설정 확인
    
    ```jsx
    // 예시 응답
    user.email=elice@elice.io
    user.name=Elice
    log.decorate=short
    ```
    
- `echo 'content' > 파일.확장자` 파일 생성 & 파일 내용으로 content 추가

### 경로 관련 코드

- `./` : 현재 working 디렉토리
- `cd` : 경로를 변경하는 코드
- `pwd` : 작업경로를 출력하는 코드
- `ls` : 현재 디렉토리에 존재하는 파일이나 디렉토리를 확인하는 코드
    - 명령어 옵션 (`명령어-` 뒤에 붙이면 됨, 여러개 가능)
        - a : 숨김 파일 및 디렉토리 함께 표시
        - l : 파일, 디렉토리의 상세정보 함께 표시
        - r : 정렬 순서를 거꾸로 표시
        - t : 시간의 내림차순으로 표시
        
        ex) ex) `ls-al` 숨김 파일 및 디렉토리가 상세정보랑 표시
        

### 계정 만들기

```css
git config --global user.email "email"
git config --global user.name "name"

git config --list // 확인
```

### 저장소 만들기

`git init (파일명)`

성공시 ⇒ Initialized empty Git repository in/파일경로/파일명/.git/ 출력

.git 이라는 하위 디렉토리를 만듬. .git 디렉토리에는 저장소에 필요한 뼈대 파일(Skeleton)이 들어 있음

### 홈페이지에서 repository 만들기

1. 컴퓨터에 파일 생성 후 → github에 올리기
2. 처음부터 github내에 repository 만들기 (니코가 선호하는 방법)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/6eff0553-0016-4d6a-bd4d-7c78cff0dad5.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/6eff0553-0016-4d6a-bd4d-7c78cff0dad5.png)
    
    ① 계정 선택 → 이름은 공백없이 소문자
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/c7f92521-bbfb-46a4-b596-0b24ec2f4d77.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/c7f92521-bbfb-46a4-b596-0b24ec2f4d77.png)
    
    ② public으로 설정 (포트폴리오로 만들 수 있음)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/521b4f1c-348c-4ec3-ba40-a3558b266082.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/521b4f1c-348c-4ec3-ba40-a3558b266082.png)
    
    ③ 클릭
    
    + README 만들기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/544154f2-a977-4556-9d8b-58ef2665b1d7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/544154f2-a977-4556-9d8b-58ef2665b1d7.png)
    
    공지사항, 유의사항 알릴 수 있는 파일
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/c59ca8a6-92d9-4d14-9995-810702fa67a2.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/c59ca8a6-92d9-4d14-9995-810702fa67a2.png)
    
    ④ clone a rapository from the internet 클릭 → 폴더 설정
    
    + desktop
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/f250e85e-67e9-464f-9ad4-aa2ecd39be6f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/f250e85e-67e9-464f-9ad4-aa2ecd39be6f.png)
    

---

# 커밋하기

![파일의 상태 사이클](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled.png)

파일의 상태 사이클

## 처리 영역

![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%201.png)

1.  **working area** (working directory)
    
    코드를 수정하는 공간 (주로 vsc)
    
2.  **staging area**
    
    변화를 알아차리고, commit 할 파일을 고르는 공간
    
    ![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%202.png)
    
3. **repository area / commit area**
    
    수정사항의 스냅샷을 저장한 공간
    

---

## 커밋하기

### **vsc 이용**

- terminal 기본 작동법
    - vsc에서 terminal 보기: view - terminal
    - 내용 입력 안 될때: q 입력
    - 내용 지우기 : clear
    - 원격 저장소 주소 불러오기: `git remote -v`

- 변경사항 감지
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/c2f957b9-f9b0-4315-9464-d1a7237e8c4e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/c2f957b9-f9b0-4315-9464-d1a7237e8c4e.png)
    
    세번째 메뉴에 가면 변경된 파일이 감지되고
    
    working tree 라는 변경내역이 비교되어 뜬다
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/348c3ea7-0e13-484b-869c-e3867946ce41.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/348c3ea7-0e13-484b-869c-e3867946ce41.png)
    
    - 파란색: 수정
    - 초록색: 추가
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/505dfdbc-2006-4c2b-bcea-3f69c06e0d66.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/505dfdbc-2006-4c2b-bcea-3f69c06e0d66.png)
    
    - M : modify (수정)
    - U : untracked (git에 등록x)
- commit할 파일 stage area로 추가하기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/a0b4450b-3142-4952-ba34-e296294324b4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/a0b4450b-3142-4952-ba34-e296294324b4.png)
    
    changes에서 +를 누르면
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/fcb2a103-94b8-4456-90ea-f226fc17dd36.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/fcb2a103-94b8-4456-90ea-f226fc17dd36.png)
    
    파일이 STAGED CHANGES 로 이동함
    
    여기 있는 파일이 commit 된다
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/8793d459-73d6-4131-93ed-5a561c4afade.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/8793d459-73d6-4131-93ed-5a561c4afade.png)
    
    untracked 였던 파일을 staged changes로 옮기면
    
    untracked → add 로 변경
    
- 내용 입력 후,  ✔ 클릭 → 컴퓨터 상 commit 완료
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/4ce6187f-958b-4403-a84f-559c6c0b1032.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/4ce6187f-958b-4403-a84f-559c6c0b1032.png)
    

### 커밋 기록 확인

`git log` 

repository에 존재하는 히스토리(커밋 기록) 확인

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/4b144efd-0bc0-4a94-af5b-6fb95bd242e9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/4b144efd-0bc0-4a94-af5b-6fb95bd242e9.png)

- `HEAD -> master` : 컴퓨터에 commit
- `orgin/main` : github 코드 저장소에 올라간 커밋 (push 완료)
    
    당연히 HEAD -> master 뒤에 있다
    
- 옵션 (명령어 뒤에 붙임)
    - `-p` / `-patch` : 각 commit의 수정 결과를 보여주는 diff와 같은 역할 수행
    - `-n` : 상위 n개의 커밋만 보여줌
    - `--stat` : 어떤 파일이 commit에서 수정/변경되었는지, 파일 내 라인의 추가/삭제 여부 확인
    - `--pretty=online` : 각 commit을 한 줄로 출력
    - `--graph` : commit 간의 연결 관계를 아스키 그래프로 출력
    - `--S text` : 코드에서 추가되거나 제거된 내용 중 특정 텍스트가 포함되어 있는지 검사

### 1. staging area로 보내기

`git add 파일명.확장자`

`git add .` : 현재 폴더의 모든 파일 보내기

- `git status` : staging area의 파일 상태 확인
- `git reset 파일명.확장자` stageing area에서 파일 내리기
    
    ```jsx
    On branch master
    Changes to be committed: // 준비영역에 있음
      (use "git reset HEAD <file>..." to unstage)
    
            new file:   README.txt 
    
    Changes not staged for commit: // 수정되었지만 준비영역에 없음
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)
    
            modified:   crawling.py 
    
    Untracked files: // 준비영역에 없음
      (use "git add <file>..." to include in what will be committed)
    
            rat.py 
    ```
    

### 2. repository로 보내기 (커밋)

`git commit -m 'commit name'`

staging area의 파일들을 commit해서 repository로 옮기기

(-m : 메세지 입력을 뜻함)

- 직전 커밋 메세지 수정
    - `git commit --amend (-m) "messeage"` : 직전 message 수정
        
        (텍스트 편집기 있다면 `-m` 생략 가능)
        
    - `git commit --amend --no-edit` : message 수정x
    
    -> `git push origin main --force` : 강제 push
    
- `git diff` commit 된 파일 중 변경내용 확인

# branch

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/d7ce49b1-0212-4694-88b4-b249aeb6232d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/d7ce49b1-0212-4694-88b4-b249aeb6232d.png)

- 메인 Branch : 배포 가능한수준의 안정적인 Branch
    
    (master ⇒ 저장소 생성시 생기는 메인 Branch)
    
- 토픽 Branch : 기능 추가, 버그 수정같은 단위 작업 위한 Branch

### 현재 Branch 목록 확인

`git branch` 

### 생성

`git branch [branch name]`

- checkout 이용 : `git checkout -b branch-name`
- branch 원격 저장소에 올리기 : `git push origin branch-name`
- 과거 commit으로 돌아가 branch 만들기
    1. `git checkout commit명`
        
        돌아갈 commit명을 입력한다
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/ec573b4c-db0d-4d63-b53c-41f52148c103.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/ec573b4c-db0d-4d63-b53c-41f52148c103.png)
        
    2. branch 생성
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/8643655e-2816-4f22-81df-ba7f73ad8303.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/8643655e-2816-4f22-81df-ba7f73ad8303.png)
        
        HEAD -> branch-name : branch 이동
        
        이전 commit 잘 있음
        
    - 위 과정 통합 ⇒ `git checkout commit-name -b branch-name`
    
- github desktop에서 조작
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/0dc7ff68-ea4e-4174-bc16-a2601c250bd9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/0dc7ff68-ea4e-4174-bc16-a2601c250bd9.png)
    
    new branch 클릭
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/e9ca27cd-eee4-48ba-8d98-180e4c4a7229.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/e9ca27cd-eee4-48ba-8d98-180e4c4a7229.png)
    
    이름 설정하고 create
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/9b797839-dfa8-42a9-9042-cb005bdf13e1.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/9b797839-dfa8-42a9-9042-cb005bdf13e1.png)
    
    master(default) -> 만든 branch 누르면 이동
    

### 전환

`git cheackout [branch name]`

해당 브랜치로 브랜치로 변경

⇒ `HEAD->master` 에서 `HEAD->[branch name]` 같이 헤드포인터 변경

- `git log`로 확인한 snapshot을 넘나들때도 사용 가능
    
    ex) `git checkout <snapshot hash>`
    
    (git의 스냅샷 : git이 데이터를 저장하는 방법으로 16진수 문자열의 해쉬값으로 표현됨)
    

---

## Branch 병합

### fast-forward

master 변경 사항 x / 다른 branch의 내용만 추가

⇒ 같은 체크포인트로 병합

![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%203.png)

1. `git checkout master` 마스터 브랜치로 이동
2. `git merge [branch name]` 병합

### 갈라진 병합

master 변경 사항 o / 다른 branch의 내용도 추가

⇒ master와 병합된branch의 체크포인트가 다름

![병합 전](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%204.png)

병합 전

![병합 후](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%205.png)

병합 후

- 브랜치 구조 파악하고 싶다면 ⇒ `git log --graph --all` 을 사용해서 시각적으로 그래프 보기
    
    ![이렇게 갈라지는 모양으로 알려줌](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%206.png)
    
    이렇게 갈라지는 모양으로 알려줌
    
1. `git checkout master` 마스터 브랜치로 이동
2. `git merge [branch name]` 병합

### 브랜치 삭제

병합이 완료된 브랜치는 삭제함

`git branch -d [branch name]`

- 원격저장소도 삭제 : `git push origin --delete branch-name`

### 충돌

master & branch 의 같은 부분을 수정 후, 병합하면 발생

<aside>
💡 마스터 브랜지의 변화를 지속적으로 가져오고, 되도록이면 건들지 않는 것이 충돌을 막을 수 있음

</aside>

![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%207.png)

1. `git status`로 충돌 부분 확인
    
    ![comment.js 파일을 동시에 수정(both modified)해서 충돌](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%208.png)
    
    comment.js 파일을 동시에 수정(both modified)해서 충돌
    
2. 충돌이 일어난 파일 열어보기
    
    → 어떤 브랜치의 코드를 쓸 것인지, 적절히 혼합할 것인지 결정
    
    ![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%209.png)
    
3. 최종 적용 코드 작성 → 기호가 있는 행 삭제
    
    ![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%2010.png)
    
4. 수정 완료 → `git add`&`git commit` → 재병합
- github desktop에서 해결
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/4a7cd212-8c77-4de3-bca7-ad066cd079d7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/4a7cd212-8c77-4de3-bca7-ad066cd079d7.png)
    
    (master) merge into current branch 클릭!
    
    master에 branch 합병 시키기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/e3fc6dab-246d-4923-998c-5471ebee9e82.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/e3fc6dab-246d-4923-998c-5471ebee9e82.png)
    
    하나의 충돌 파일이 있다는 문구
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/7e916b57-b318-4512-8b83-760b45225944.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/7e916b57-b318-4512-8b83-760b45225944.png)
    
    open in visual Studio Code 누르면
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/6ec0b8d4-4886-462c-9be7-2fd44abb9423.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/6ec0b8d4-4886-462c-9be7-2fd44abb9423.png)
    
    conflict 한 부분 알려준다
    
    - current change: 현재 branch의 변경 사항 (현 master)
    - incoming change: merge 하고 싶은 곳의 변경 사항 (현 branch)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/084aca99-80f0-4b9f-8d66-511816be8a4a.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/084aca99-80f0-4b9f-8d66-511816be8a4a.png)
    
    많은 선택 사항을 제시
    
    둘을 비교해주거나, 전자로 수정해주거나… 원하는 방법 누르면 해결
    

---

# Clone

## 원격-로컬 저장소 연결

### 원격→로컬

원격 저장소를 로컬로 받아오기

1. Clone with HTTPS의 url 복사
    
    ![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%2011.png)
    
2. 로컬 저장소에 클론하기 : `git clone url`
    
    ![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%2012.png)
    
- 명령어 실행 → 현재 폴더 내에 새폴더 생성 (현재 폴더= 저장소x)
    
    ⇒ 현재 폴더를 저장소로 쓰고 싶다면 마지막에 `.` 입력
    

### 로컬→원격

원격 저장소 추가

`git remote add origin http://웹호스트/그룹명/프로젝트명`

⇒ 원격저장소의 단축이름을 origin으로 지정한다는 의미 

(기본값=origin, 다른 의미도 가능)

![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%2013.png)

- `git remote` 연결된 원격저장소 확인
    
    `git remote -v` : 지정한 저장소의 이름과 주소 볼 수 있음
    

### 원격저장소 살펴보기

- `git remote show origin` 원격저장소 살펴보기
    
    ![Untitled](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/Untitled%2014.png)
    

### 원격저장소 이름 변경

`git remote rename origin [name]`

### 원격 저장소 삭제

`git remote rm 저장소이름`

---

## 원격→로컬 동기화

### Pull

`git pull origin master`

원격 저장소에서 데이터 가져오기 + 로컬데이터와 병합(merge)

⇒ master(로컬저장소)와 origin(원격저장소)가 병합, 커밋되어 같은 체크포인트를 가짐

![pull 후 `git log`로 확인한 모습](1%20basic%20bfe5dec398fc4dde8da049cb69106dd9/2022-09-16_203216.png)

pull 후 `git log`로 확인한 모습

### Fetch

`git fecth origin master`

1. `git log`로 변경된 파일 확인 : `git log origin/master`
2. 확인 후, 병합 : `git merge origin/master`

---

## 로컬→원격 동기화(Push)

로컬 저장소에서 작업한 내용을 원격 저장소에 반영

<aside>
💡 다른 사람이 먼저 push한 상태에서 push 불가
⇒ 다른 사람이 작업한 것을 merge부터 해야함

</aside>

(terminal) `git push origin master`

변경사항 원격에 전달

↳ push 할 곳 (origin = 원격코드 저장소)

↳ push 하고 싶은 브랜치

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/db490342-b5fc-4aca-ab81-62c48545d4b3.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/db490342-b5fc-4aca-ab81-62c48545d4b3.png)

push 완료되면 HEAD -> master, orgin/main 같이 입력됨

---

# 정리가 다시 필요한 내용

- `git rm 파일명.확장자 --cached` 원격저장소에 잘못된 파일 올렸을 때, 원격저장소에서 삭제하고, staging area에서도 파일 내리기
    
    (폴더) `git rm -r 폴더명/ --cached`
    
- 이미 origin에 올린 파일 숨기고 싶다면
    
    git상에서 먼저 삭제해야 한다
    
    = gitignore에 추가→ stage에서 삭제
    

## git이 무시할 파일 지정

1. .gitignore 이라는 파일을 만들어서
2.  `파일이름` 입력 → git이 지정파일 읽지 않음
    - 폴더라면 `/폴더명` 입력ㅣ
        
        ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/564966e0ed5740d29dfd84368ef3168d/1eecd947-512a-4767-b31f-5adfb69a9609.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/564966e0ed5740d29dfd84368ef3168d/1eecd947-512a-4767-b31f-5adfb69a9609.png)
        

```
# : comments

# no .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in the build/ directory
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory
doc/**/*.pdf
```

# 이전 commit으로 돌아가기

head에서 돌아간 것이기 때문에, 원격저장소에 저장하려면 강제 push 필수

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/dd79f003-871e-4b6e-bd46-e176acdf7b0e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/dd79f003-871e-4b6e-bd46-e176acdf7b0e.png)

1. **checkout**
    
    `git **checkout** commit-name`
    
    지정한 commit으로 돌아가기 (head 옮기기)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/8c853c82-20d3-4410-8356-439bde60fbb7.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/8c853c82-20d3-4410-8356-439bde60fbb7.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/e20ed684-3af8-46d6-9058-0b1e670ac6bf.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/4b77bae7b0994250aed077f8c4988cb4/e20ed684-3af8-46d6-9058-0b1e670ac6bf.png)
    
    head가 해당 commit으로 옮겨진다
    
    - 실제로 commit을 삭제하거나 수정한 것은 아님
    - `git **checkout** main` : 다시 원래 상태로 돌아옴
    
2. **reset**
    
    주로 hard, mix 사용
    
    - **** hard
        
        `git **reset** HEAD^ **--hard**`
        
        - ^개수마다 이전 commit으로 돌아감
        - 위 commit을 완전히 삭제 & 변경사항도 삭제
        - `-head` 는 HEAD 앞에 써도 상관x
        - ex) 한 commit 전으로 돌아가기
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/ff3a930e-bdc2-4ab7-91f7-208e4afa8d38.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/ff3a930e-bdc2-4ab7-91f7-208e4afa8d38.png)
            
            git reset –hard HEAD^ 실행
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/532242f4-e138-40d6-8ca9-f3da4771eac9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/532242f4-e138-40d6-8ca9-f3da4771eac9.png)
            
            한 커밋 전으로 head 이동
            
    - **** Mix
        
        `git **reset** HEAD^`
        
        - commit을 삭제, 하지만 변경사항은 남아있음 (unstaged)
            
            : 삭제된 commit의 변경사항들은 changes(변경내역 감지된 상태)로 남아있음
            
        - 완료되지 않은 파일을 commit 했을 때 주로 사용함
            
            ex) 세 개의 commit이 있는 상태
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/470b9a0c-81d8-40eb-a8cc-80c4dbddb291.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/470b9a0c-81d8-40eb-a8cc-80c4dbddb291.png)
            
            `git reset HEAD^^` 입력하고, git 내역 확인
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/a10efdb1-209c-4846-97e5-02347dab42d9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/a10efdb1-209c-4846-97e5-02347dab42d9.png)
            
            의도한대로 위 두 개 commit 삭제되고
            
            ‘안녕하세요’ commit 만 남아있음
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/770fbe01-6a3c-4b8e-9efc-3d61d194769f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/770fbe01-6a3c-4b8e-9efc-3d61d194769f.png)
            
            그리고 위 두 commit의 변경 내역은 삭제되지 않고
            
            changes (변경사항을 감지한 상태, 여기서 stage area로 옮겨야 commit 된다)
            
            - 직전 commit의 변경사항만 남아있는 것이 아니다
            
        
    - **** soft
        
        `git **reset** HEAD^ **--soft**`
        
        - commit을 삭제, 하지만 변경사항은 남아있음 (staged)
            
            : 삭제된 commit의 변경사항들이 staged changes에 남음
            
        - ex) 파일 ’second’를 수정하고, commit한 상황
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/9595e04b-8521-4a41-be01-0cae7f82746c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/9595e04b-8521-4a41-be01-0cae7f82746c.png)
            
            `git **reset** HEAD^ **--soft**` 를 입력
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/de4bf750-7857-4517-b59c-4f40581e3bcb.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/de4bf750-7857-4517-b59c-4f40581e3bcb.png)
            
            최근 commit이 사라짐
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/60c34ac4-cf2c-47a4-a33d-cfb3e92b455e.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/60c34ac4-cf2c-47a4-a33d-cfb3e92b455e.png)
            
            수정사항이 staged changes 에 남아있음
            
    - 강제로 push 하기
        
        `git push origin main **--force**`
        
        위 작업들은 컴퓨터 상에서 head를 옮기는 것이므로
        
        원격 저장소에 저장하려면 강제로 push 해야함
        
        - 강제로 push 안 할 시, 생기는 오류
            
            (head) mix reset을 실행, 최근 2개의 commit 삭제 → 새 commit
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/228df99b-0e51-462c-9397-0cb234b6f061.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/228df99b-0e51-462c-9397-0cb234b6f061.png)
            
            (origin) 2개의 commit 삭제되지 않음
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/53a19f84-e664-4d4a-bc7e-fb5d225e274f.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/53a19f84-e664-4d4a-bc7e-fb5d225e274f.png)
            
            git pull origin main (origin의 내용 불러오기) 실행 → 오류
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/d5b572a0-6f1f-43ee-9a30-a82949427398.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/d5b572a0-6f1f-43ee-9a30-a82949427398.png)
            
            부딪히는 부분이 나옴. 위에 다양한 선택지를 눌러 해결하면 된다
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/4b77bae7b0994250aed077f8c4988cb4/fc7878bb-9be4-4a06-8355-b5a8e3320ada.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/image_upload/4b77bae7b0994250aed077f8c4988cb4/fc7878bb-9be4-4a06-8355-b5a8e3320ada.png)
            
            head 의 수정내용을 선택한 경우, 저장해주고→ add → commit →push 까지 마침
            
            ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/2d299eb1-4364-458e-be60-8736bf670bca.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/4b77bae7b0994250aed077f8c4988cb4/2d299eb1-4364-458e-be60-8736bf670bca.png)
            
            origin을 확인해보면, 강제로 push 하지 않아 남아있던 파랑색과
            
            head에서 commit하고 병합한 분홍색 모두 저장되어 있음
            
            ∴ 강제로 push 하는 것이 가장 쉽고 깔끔하다
            
            또한 head에서만 commit 한 상태라면 (push 안했다면) 굳이 합병시키고 그럴 필요 없음
            
        

## 파일명 수정

`git mv 현재파일명.확장자 변경파일명.확장자`

(공백 앞에는 `\` 붙이기)

mkdir 파일명 : 파일 생성

ls : 현재 존재하는 파일들 확인

cd 파일명 : 해당 파일로 이동

그 상태에서 vsc에서 파일 수정 후, 커밋

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/9ff79c75-0a22-4525-8d3d-46d32a2fc1e4.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/9ff79c75-0a22-4525-8d3d-46d32a2fc1e4.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/53140ae4-d531-4ce0-9c91-024395302804.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/53140ae4-d531-4ce0-9c91-024395302804.png)

이렇게 하면 master이 아닌 branch에 저장된다

master의 내용은 변동 없음

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/905c265e-36f7-4911-bb00-8b75c5d18e95.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/905c265e-36f7-4911-bb00-8b75c5d18e95.png)

![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/87c90b8c-9f39-4d66-872a-38611c3da5b0.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/87c90b8c-9f39-4d66-872a-38611c3da5b0.png)

git으로 main, branch 왔다갔다 하면

파일도 알아서 바뀐다!

## Github으로 배포하기

1. **gh-pages** 라는 이름의 **public**한 branch 만들기
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/b2294da7-b9ee-4817-b874-dbb232d9a319.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/b2294da7-b9ee-4817-b874-dbb232d9a319.png)
    
2. 내 repository 들어가기 → branch 클릭
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/1266865f-910d-4057-b46d-62c41e60482d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/1266865f-910d-4057-b46d-62c41e60482d.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/068d978a-a200-41ad-9397-8defff73bf6c.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/068d978a-a200-41ad-9397-8defff73bf6c.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/2882c15a-7848-49cf-b09d-6d1ca16a8c7b.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/2882c15a-7848-49cf-b09d-6d1ca16a8c7b.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/a411901c-0c0d-4913-912a-350ecdc3f349.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/a411901c-0c0d-4913-912a-350ecdc3f349.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/4ccbebe1-2e2d-48ab-ad46-a2b3deb683e9.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_markup_images/564966e0ed5740d29dfd84368ef3168d/4ccbebe1-2e2d-48ab-ad46-a2b3deb683e9.png)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/52f8b3fc-7362-4760-ab05-78f010350af8.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/52f8b3fc-7362-4760-ab05-78f010350af8.png)
    
    url :
    
    username.github.io/repository-name
    
    wldn0804.github.io/kokoa-clone-2021
    

## 배포 수정**하기 (수정하기)**

1. master (default) 로 가서 수정사항 commit (push까지)
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/96cdb9a3-0064-4253-ab46-b9a56ebbbc5d.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/96cdb9a3-0064-4253-ab46-b9a56ebbbc5d.png)
    
2. gh-pages로 이동 → branch > update from master → push
    
    ![https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/8ee47087-e801-4b42-b164-bfc8aa76da19.png](https://slid-capture.s3.ap-northeast-2.amazonaws.com/public/capture_images/564966e0ed5740d29dfd84368ef3168d/8ee47087-e801-4b42-b164-bfc8aa76da19.png)