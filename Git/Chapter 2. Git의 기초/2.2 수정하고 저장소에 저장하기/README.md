---

# <a href = "../../README.md" target="_blank">Git</a>
## <a href = "../README.md" target="_blank">Chpater 2. Git의 기초</a>
### 2.2 수정하고 저장소에 저장하기
1) 파일의 라이프 사이클
2) 파일의 상태 확인하기 (git status)
3) 파일 상태를 짤막하게 확인하기 (git status -s, git status --short)
4) 파일을 새로 추적하기 (git add)
5) Modified 상태의 파일을 Stage하기 (git add)
6) 파일 무시하기 (.gitignore)
7) Staged와 Unstaged 상태의 변경 내용을 보기 (git diff)
8) 변경사항 커밋하기 (git commit)
9) Staging Area 생략하기 (git commit -a)
10) 파일 삭제하기 (git rm, git commit)
11) 파일 이름 변경하기 (git mv)

---

# 2.2 수정하고 저장소에 저장하기

## 1) 파일의 라이프 사이클

### Working Directory (Unstaged)의 구조
<center><p><img src="img/FileLifeCycle.jpg" /></p></center>

- Untracked (관리대상이 아닌) : 스냅샷 내역에 저장되어 있지 않고, Staging Area에 포함되지 않은 파일
- Tracked (관리대상인)
  - Modified (수정된) : 이미 스냅샷에 올려진 파일들
  - Staged (커밋으로 저장소에 기록할) : 수정된 파일 또는 Untracked 파일이 add를 통해 `Staged` 상태가 됨. 커밋하면 스냅샷이 git에 의해 관리되고, Unmodified 상태가 됨.
  - Unmodified (수정되지 않은) : 마지막 커밋 이후 아직 아무 것도 수정하지 않은 상태

---

## 2) 파일의 상태 확인하기 (git status)
> git status
- 현재 git 저장소의 상태를 확인하기 위해 `git status` 명령을 사용
- 현재 브랜치명, Untracked 파일은 무엇이 있는지, Modified 파일은 무엇이 있는지 등 Working Directory의 대강의 상태 정보를 제공
- `.gitignore`에 의해 tracking에서 열외된 파일들은 상태가 뜨지 

---

## 3) 파일 상태를 짤막하게 확인하기 (git status -s, git status --short)
> git status -s  
> git status --short

- 변경상태를 더 짤막하게 보여줌
- ?? : Untracked
- A : 새로 생성된 파일이 `git add` 되어 staged 상태가 됨
- `_M(앞자리 공백, 뒷자리 M)` : 수정했지만, git add되지 않음
- `M_(앞자리 M, 뒷자리 공백)` : 수정하고, git add된 Modified 파일
- MM : Stage 되어 있으나, 다시 한번 수정 후 git add되지 않음.
- AM : 파일을 새로 생성하여 `git add`되었으나, 다시 한번 수정 후 git add되지 않음

---

## 4) 파일을 새로 추적하기 (git add)
> git add
- Untracked 파일을 Stage에 올림

---

## 5) Modified 상태의 파일을 Stage하기 (git add)
> git add
- Modified 파일을 Stage에 올림
- `add`라는 단어를 Stage에 파일을 추가하기보다, 다음 커밋에 변경을 추가한다는 의미로 받아들이면 됨.
- Modified 상태의 파일을 add하고(1차 수정), 다시 또 수정하면(2차수정) 2차수정 내역이 반영되지 않은 상태가 됨.
  - 이 상태에서 그냥 `commit`하면, 1차 수정 내역만 히스토리에 반영됨  
  - 이 상태에서 2차 수정 내역을 다시 add하면 1,2차 수정 내역이 모두 반영된 상태로 스테이지에 올려짐.

---

## 6) 파일 무시하기 (.gitignore)
로그 파일이나, 빌드 시스템이 자동으로 생성한 파일 등은 Git이 관리할 필요가 없는데, 이런 파일들을 무시하기 위해서는 `.gitignore` 파일을 작성하고, 무시할 파일 패턴을 적으면 된다.

- `.gitignore` 자동 제공 사이트 : <a href="https://www.toptal.com/developers/gitignore" target="_blank"> 링크</a>

### 패턴

- 주석 `#` : 아무 것도 없는 라인이나, #으로 시작하는 라인은 무시 (주석)
- 표준 Glob 패턴을 사용한다.
  - Glob 패턴 : 정규표현식을 단순하게 만든 것.
- 슬래시(/)로 시작하면 그 디렉토리의 하위 디렉토리에 적용되지 않는다.
  ```
  # 현재 디렉토리의 하위에 있는 TODO.txt는 무시하고 나머지는 무시하지 않음.
  /TODO.txt
  ```
- 느낌표로 시작하는 패턴의 파일은 무시하지 않는다.
    ```
    # 확장자가 .a인 파일 무시 
    .a
    
    # 확장자가 .a인 파일이 무시됐지만, lib.a는 무시하지 않음.
    !lib.a
    ```
- 디렉토리는 슬래시(/)를 끝에 사용하는 것으로 표현
  ```
  # build 디렉토리에 있는 모든 파일은 무시
  build/
  
  # doc 디렉토리 아래의 모든 .pdf 파일을 무시
  doc/**/*.pdf
  ```

---

## 7) Staged와 Unstaged 상태의 변경 내용을 보기 (git diff)
> git diff
- 파일의 어떤 내용이 변경되었는지를 확인하기 위한 명령어
- 워킹 디렉토리에 있는 것과 Staging Area에 있는 것을 비교
  - staged되지 않았을 때 : Unstaged - 히스토리 비교
  - staged되고 수정이 생겼을 때 : Unstaged - staged 비교
- Untracked 파일은 변경 사항이 아니므로 집계되지 않음
> git diff --staged  
> git diff --cached
- staged된 것과 히스토리(저장소에 커밋한 것)를 비교
- Untracked 파일이 staged됐을 때, new File로 집계함

### 표시되는 내역
- a/파일명 : 변경전
- b/파일명 : 변경후
- 수정된 라인.
- 추가되거나 수정된 라인 내역


### git difftool
- 변경내역을 config에서 지정한 difftool로 확인
- difftool을 vscode로 지정하는 방법은 다음과 같다.
  ```
  [diff]
  tool = vscode
  [difftool "vscode"]
  cmd = code --wait --diff $LOCAL $REMOTE
  ```
---

## 8) 변경사항 커밋하기 (git commit)
> git commit
- `core.editor`로 지정된 편집기가 열리고 커밋메시지를 작성할 수 있음.
- add를 통해 Staging Area에 올려진 파일을 스냅샷을 찍어 버전으로 관리함.
- 커밋이 완료되면 Staging Area에 올려진 파일을은 `Unstaged - Unmodified` 상태가 됨.
- 커밋하기 전에 `git status` 명령을 통해 변경점을 확인하고 커밋하는 버릇을 들이는 것이 좋음
> git commit -m
- 편집기를 열지 않고, 뒤에 오는 문자열을 커밋메시지로 하여 바로 커밋함.

### 커밋이 가진 정보
- 해쉬코드
- 작성자 (Author) 및 이메일
- 변경내역(diff)
- 커밋 시점의 날짜, 시각
- 커밋 메시지

---

## 9) Staging Area 생략하기 (git commit -a)
> git commit -a
- Tracked 상태의 파일들을 모두 Staging Area에 올리고 바로 `Commit`함.

---

## 10) 파일 삭제하기 (git rm, git commit)
> git rm 파일명
- 지정 파일을 git에서 제거(Staging Area에서 삭제)
- 워킹 디렉토리에서도 삭제하므로, 실제 파일도 제거됨
- 파일이 제거되면 제거된 상태가 staged됨.
> git rm --cached 파일명
- Staging Area에서 제거하고, 워킹디렉토리에 있는 파일은 지우지 않고 남겨두기
- 파일을 git이 추적하지 않게함.
> git rm \*~
- ~로 끝나는 파일 모두 삭제
  - 예> git rm log/\*.log : log 디렉토리 하위에 있는 .log 파일 제거

---

## 11) 파일 이름 변경하기 (git mv)
> git mv 변경전파일명 변경후파일명
- 파일 이름을 변경하고, 이름 변경 내역이 staged됨
- 실제 원리
  - mv 변경전파일명 변경후파일명 : 파일 이름은 변경
  - git rm 변경전파일명 : git 저장소에서 변경전 파일을 제거
  - git add 변경후파일명 : git 저장소에 변경후 파일을 stage함

---