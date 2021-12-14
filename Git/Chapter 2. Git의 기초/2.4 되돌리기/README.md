---

# <a href = "../../README.md" target="_blank">Git</a>
## <a href = "../README.md" target="_blank">Chpater 2. Git의 기초</a>
### 2.4 되돌리기
1) 완료된 커밋 다시 수정하기(커밋 덮어쓰기)
2) 파일을 Unstaged 상태로 변경하기
3) Modified 파일 되돌리기

---

# 2.4 되돌리기

## 1) 완료된 커밋 다시 수정하기(커밋 덮어쓰기)
> git commit -amend
- 이전의 커밋 위에 덮어 씌움
- 너무 일찍 커밋했거나, 어떤 파일을 빼먹었을 경우, 혹은 커밋 메시지를 잘못 입력했을 때 사용
- Staged Area를 이용해서 커밋. 마지막 커밋 이후 수정한 것이 없으면 커밋 메시지만 수정

---

## 2) 파일을 Unstaged 상태로 변경하기
> get reset HEAD 파일명
- staged 상태가 된 파일을 Unstaged 파일로 변경함

---

## 3) Modified 파일 되돌리기
> git checkout -- 파일명
- 현재 HEAD의 히스토리로부터 지정 파일을 가져와 현재 수정된 파일 위에 덮어씌움.
- 원래 파일로 덮어썼기 때문에 수정 내용이 전부 사라짐.
- 주의 : 커밋하지 않고 잃어버린 것은 절대 복구할 수 없음. 다른 방법을 쓰도록 하길 권장

---

