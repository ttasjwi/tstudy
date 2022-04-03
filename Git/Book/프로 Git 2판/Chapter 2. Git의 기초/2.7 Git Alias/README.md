---

# <a href = "../../README.md" target="_blank">Git</a>
## <a href = "../README.md" target="_blank">Chpater 2. Git의 기초</a>
### 2.7 Git Alias
1) Alias 만들기
2) 긴 명령을 Alias로 만들기
3) 외부 명령 실행하기
---

## 1) Alias 만들기
- Alias : 자주 사용하는 명령을 축약어로 대체해서 간단하게 사용하는 방법
    ```
    예시>
        git config --global alias.co checkout
        git config --global alias.br branch
        git config --global alias.st status
    ```

---

## 2) 긴 명령을 Alias로 만들기
여러 옵션들의 조합으로 되어 있는 긴 명령을 새로운 명령으로 정의할 수 있음. 따옴표로 감싸서 처리하면 됨
```
// 최근 커밋 확인
git config --global alias.last 'log -1 HEAD'

// 뒤에 오는 File을 HEAD의 git directory로부터 떼어내 unstage 상태로 만듬.
git config --global alias.unstage 'reset HEAD --'
```

---

## 3) 외부 명령 실행하기  
명령 앞에 '!'을 붙이면, 외부 명령을 시행할 수 있게 할 수 있다.
```
// git에서 gitk 실행 Alias 만들기
git config --global alias.visual '!gitk'
```

---