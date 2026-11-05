# Windows Docker 개발환경 과제

## 1. 과제 개요
이 과제는 Windows 환경에서 Docker Desktop을 설치하고 실행한 뒤, Docker 버전 확인, Docker 실행 환경 점검, Hello World 컨테이너 실행, Ubuntu 컨테이너 접속 및 Linux 명령어 실습을 수행한 결과를 정리한 것이다.

---

## 2. 개발 환경
- 운영체제: Windows
- 컨테이너 도구: Docker Desktop
- 편집기: Visual Studio Code
- 버전 관리 도구: Git

---

## 3. 프로젝트 폴더 구조
```text
docker-assignment/
├─ README.md
├─ Dockerfile
├─ index.html
└─ screenshots/
   ├─ 01-docker-version.png
   ├─ 02-docker-info.png
   ├─ 03-hello-world.png
   ├─ 04-ubuntu-run.png
   └─ 05-linux-commands.png
```

---

## 4. Docker 버전 확인

### 실행 명령
```powershell
docker --version
```

### 설명
Docker가 정상적으로 설치되었는지 확인하기 위해 버전 정보를 조회하였다.  
명령어 실행 결과를 통해 Docker 명령이 정상적으로 동작함을 확인하였다.

### 실행 화면
![Docker 버전 확인](screenshots/01-docker-version.png)

---

## 5. Docker 실행 환경 확인

### 실행 명령
```powershell
docker info
```

### 설명
Docker 클라이언트와 서버의 상태를 확인하였다.  
이 명령을 통해 Docker Desktop이 정상적으로 실행 중인지, 컨테이너 환경이 올바르게 구성되어 있는지 확인할 수 있다.

### 실행 화면
![Docker 실행 환경 확인](screenshots/02-docker-info.png)

---

## 6. Hello World 컨테이너 실행

### 실행 명령
```powershell
docker run hello-world
```

### 설명
`hello-world` 이미지를 실행하여 Docker가 이미지를 정상적으로 내려받고 컨테이너를 실행하는지 확인하였다.  
출력 결과의 `Hello from Docker!` 메시지를 통해 Docker 환경이 정상적으로 동작함을 확인하였다.

### 실행 화면
![Hello World 실행](screenshots/03-hello-world.png)

---

## 7. Ubuntu 컨테이너 실행

### 실행 명령
```powershell
docker run -it ubuntu bash
```

### 설명
Ubuntu 이미지를 기반으로 컨테이너를 실행하고 bash 셸에 접속하였다.  
이를 통해 컨테이너 내부에서 Linux 명령어를 직접 실습할 수 있는 환경을 구성하였다.

### 실행 화면
![Ubuntu 컨테이너 실행](screenshots/04-ubuntu-run.png)

---

## 8. Ubuntu 컨테이너 내부 Linux 명령어 실습

### 실행 명령 예시
```bash
pwd
ls
whoami
mkdir practice
touch practice/test.txt
cat practice/test.txt
cp practice/test.txt practice/test2.txt
mv practice/test2.txt practice/renamed.txt
chmod 755 practice
rm practice/renamed.txt
```

### 설명
Ubuntu 컨테이너 내부에서 기본적인 Linux 명령어를 실습하였다.

- `pwd`: 현재 작업 디렉터리 확인
- `ls`: 디렉터리 내부 파일 목록 확인
- `whoami`: 현재 사용자 확인
- `mkdir`: 디렉터리 생성
- `touch`: 파일 생성
- `cat`: 파일 내용 확인
- `cp`: 파일 복사
- `mv`: 파일 이동 또는 이름 변경
- `chmod`: 파일 또는 디렉터리 권한 변경
- `rm`: 파일 삭제

이 과정을 통해 컨테이너 내부에서 파일 시스템을 다루는 기본 방법을 익혔다.

### 실행 화면
![Linux 명령어 실습](screenshots/05-linux-commands.png)

---

## 9. Dockerfile 및 HTML 파일 생성

### 설명
과제 폴더 안에 `Dockerfile`과 `index.html` 파일을 생성하여 Docker 기반 웹 실습을 위한 기본 파일 구조를 준비하였다.  
이 단계는 이후 컨테이너 이미지 작성 및 웹 페이지 실행 실습에 활용할 수 있도록 구성한 것이다.

---

## 10. 결론
이번 과제를 통해 Windows 환경에서 Docker Desktop을 설치하고 실행하는 과정을 확인하였다.  
또한 Docker 버전 확인, 실행 환경 점검, Hello World 컨테이너 실행, Ubuntu 컨테이너 접속 및 Linux 명령어 실습을 수행하였다.  
이를 통해 Docker의 기본 사용법과 컨테이너 내부에서 Linux 명령어를 다루는 방법을 학습할 수 있었다.
