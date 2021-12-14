---

# <a href = "../../README.md" target="_blank">Git</a>
## <a href = "../README.md" target="_blank">Chpater 2. Git의 기초</a>
### 2.5 리모트 저장소
1) 리모트 저장소 확인하기
2) 리모트 저장소 추가하기
3) 리모트 저장소에서 데이터 가져오기 (fetch, pull)
4) 리모트 저장소에 Push하기
5) 리모트 저장소 살펴보기
6) 리모트 저장소 이름 변경
7) 리모트 저장소 삭제

---

# 2.5 리모트 저장소
인터넷, 네트워크 어딘가에 있는 원격 저장소

## 1) 리모트 저장소 확인하기
> git remote
- 저장소에 등록된 리모트 저장소를 조회하고, 그 저장소 명을 출력함
- 저장소를 Clone하면, 자동으로 origin 리모트 저장소가 등록되기 때문에 `origin`이라는 이름으로 보임 
> git remote -v
- 단축 이름과, URL을 함께 볼 수 있음.
- 리모트 저장소가 여러개일 경우 모든 리모트 저장소를 보여줌.
- 각 저장소별 push 권한 여부는 알 수 없음.

### 예시>
```
$ git remote
origin

$ git remote -v
origin  https://github.com/ttasjwi/Note (fetch)
origin  https://github.com/ttasjwi/Note (push)
```

---

## 2) 리모트 저장소 추가하기
> git remote add 단축이름 url
- 지정 url을 지정 단축이름으로 하여, 리모트 저장소로 지정함.

---

## 3) 리모트 저장소에서 데이터 가져오기 (fetch, pull)
> git fetch 단축이름
- 지정 리모트 저장소에 있는 데이터를 모두 가져옴.

> git pull 단축이름 브랜치명
- 지정 리모트 저장소에 있는 데이터를 가져오고, 로컬 브랜치의 현재 작업 코드와, 지정 브랜치를 merge 시킴

---

## 4) 리모트 저장소에 Push하기
> git push 리모트저장소명 브랜치명
- Clone한 remote 저장소에 쓰기 권한이 있고, Clone한 이후 아무도 Upstream 저장소에 push하지 않았을 때만 사용 가능.
- Clone한 사람이 여러명 있고, 다른 사람이 push한 후에 push할 수 없다.
  - push 데이터를 가져와서 merge한 뒤에 push할 수 있음.
---

## 5) 리모트 저장소 살펴보기
> git remote show 리모트저장소명
- 리모트 저장소의 구체적인 정보 확인
- 리모트 저장소의 URL, 추적 브랜치 출력
- pull 명령에서 브랜치명을 생략시, 어떤 리모트 브랜치를 어느 브랜치에 pull 해오는지 출력
- push 명령에서 브랜치명을 생략시, 어떤 브랜치가 어떤 브랜치로 push 되는 지 출력
- 아직 로컬로 가져오지 않은 리모트 저장소의 브랜치들 출력
- 서버에서는 삭제됐지만 아직 가지고 있는 브랜치들 출력

예시>
```
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/ttasjwi/Algorithm
  Push  URL: https://github.com/ttasjwi/Algorithm
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

---

## 6) 리모트 저장소 이름 변경
> git remote rename 기존저장소명 변경저장소명
- 이후 리모트 저장소를 호출 시 변경저장소명으로 불러야함.

---

## 7) 리모트 저장소 삭제
> git remote rm 저장소명
- 저장소의 리모트 저장소 연결관계를 제거함.
- 서버 정보가 바뀌었거나, 별도의 미러가 필요하지 않을 때, 더는 기여자가 활동하지 않을 때 사용

---