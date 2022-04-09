
## Docker에 MySQL 환경 구축하기

## TODO

- [x] 가상환경에서 MySQL을 사용하기 위해 Docker를 설치
- [x] Docker로 ko_KR.UTF-8 로케일을 적용한 MySQL 이미지 만들기
- [ ] Docker 명령으로 MySQL 컨테이너 실행
- [ ] Docker 명령으로 MySQL 컨테이너에 Bash로 접속

---

## 1. 가상환경에서 MySQL을 사용하기 위해 Docker 설치

![dockerInstall](img/dockerInstall.jpg)

- Windows / MacOS
  - https://www.docker.com/get-started/ 에서 도커 설치
  - Windows WSL2 기반 도커 실행시 vmmem 메모리 소모량 이슈가 있다. 이 부분은 아래 링크를 참조하도록 하자.
    - https://meaownworld.tistory.com/160
    - Settings > General > Start Docker Desktop when you log in 을 끄자.
- 설치 확인
  ```shell
  PS C:\Users\ttasjwi> docker --version
  Docker version 20.10.13, build a224086
  ```

---

## 2. Docker로 ko_KR.UTF-8 로케일을 적용한 MySQL 이미지 만들기

```shell
mkdir dockerbuild
cd dockerbuild
```
```dockerfile
# 적당한 폴더를 만들어서 그 안에서 Dockerfile 생성
FROM mysql:latest
RUN apt-get update && apt-get install -y locales
RUN localedef -f UTF-8 -i ko_KR ko_KR.UTF-8
ENV LC_ALL ko_KR.UTF-8
```
```shell
# 현재 경로의 Dockerfile 기반으로 
docker build -t mysql:적당한태그명 .
```
- pull 명령어로 MySQL 이미지를 땡겨올 경우, locale 설정이 POSIX로 되어있다.
- 여기서 명령어를 적당히 입력하면 `ko_KR.UTF-8` 로케일을 적용할 수 있지만, 다시 동일 이미지로 컨테이너를 생성해보면 설정이 날아간다.
- `ko_KR.UTF-8`이 기본 설정으로 적용된 이미지를 빌드하는 것이 재사용에 있어 현명하다.
- `mysql:latest`를 기반으로 몇 가지 설정을 덧붙여 이미지를 정의한 DockerFile을 작성한 뒤 이미지를 새로 빌드한다.
- 해당 이미지를 기반으로 실행 시 터미널에서 한글을 입력할 수 있다.
- 참고자료 : [도커(Docker) 컨테이너 로케일 설정 데비안(Debian), 우분투(Ubuntu) 이미지에서 한글 입력 문제](https://www.44bits.io/ko/post/setup_linux_locale_on_ubuntu_and_debian_container#%EB%93%A4%EC%96%B4%EA%B0%80%EB%A9%B0-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88%EC%99%80-%EB%A6%AC%EB%88%85%EC%8A%A4-%EB%A1%9C%EC%BC%80%EC%9D%BC-%EC%84%A4%EC%A0%95)


<details>
<summary>실험 결과</summary>
<div markdown="1">

```shell
docker run -it mysql:ttasjwi bash
root@410ca2fa6632:/# locale
```
![UTF-8_MySQL_Image.jpg](img/UTF-8_MySQL_Image.jpg)

- 실제로 해당 이미지로 도커 컨테이너를 실행했을 때 locale 설정이 ko_KR.UTF-8로 된 MySQL 이미지가 빌드된 것을 확인할 수 있다.

</div>
</details>

---
