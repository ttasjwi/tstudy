
## Docker에 MySQL 환경 구축하기

## TODO

- [x] 가상환경에서 MySQL을 사용하기 위해 Docker를 설치
- [ ] Docker 기반으로 MySQL 설치
- [ ] Docker 명령으로 MySQL 컨테이너 실행
- [ ] Docker 명령으로 MySQL 컨테이너에 Bash로 접속
- [ ] 셸의 환경변수와 Locale 설정, MySQL의 Config을 UTF-8로 변경

---

## 1. 가상환경에서 MySQL을 사용하기 위해 Docker 설치

![img.png](img/dockerInstall.jpg)

- Windows / MacOS
  - https://www.docker.com/get-started/ 에서 도커 설치
  - Windows WSL2 기반 도커 실행시 vmmem 메모리 소모량 이슈가 있다. 이 부분은 아래 링크를 참조하도록 하자.
    - https://meaownworld.tistory.com/160
- 설치 확인
  ```shell
  PS C:\Users\ttasjwi> docker --version
  Docker version 20.10.13, build a224086
  ```

---
