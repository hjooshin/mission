좋아요! 이제 **최종 제출용 `README.md` 전체 내용**을 한 번에 복붙할 수 있게 정리해드릴게요.  
아래 내용을 그대로 `README.md` 파일에 붙여넣으면 됩니다. 👍

```md
# Docker Assignment

## 1. 과제 개요
이 프로젝트는 Docker 기본 실습 과제를 정리한 저장소입니다.  
Windows 환경에서 Docker Desktop을 설치하고, Docker 명령어를 실행한 뒤 Ubuntu 컨테이너 내부에서 Linux 기본 명령어를 실습했습니다.

---

## 2. 개발 환경
- OS: Windows
- Editor: VS Code
- Version Control: Git
- Container Tool: Docker Desktop

---

## 3. Docker 설치 및 실행 확인

### Docker 버전 확인
```bash
docker --version
```

### Docker 상세 정보 확인
```bash
docker info
```

Docker가 정상적으로 설치되었는지 확인한 후, 컨테이너 실행 실습을 진행했습니다.

---

## 4. 컨테이너 실행 실습

### hello-world 실행
```bash
docker run hello-world
```

### Ubuntu 컨테이너 실행
```bash
docker run -it ubuntu bash
```

위 명령어를 통해 Docker가 정상적으로 동작하는지 확인하고, Ubuntu 컨테이너 내부에서 실습을 진행했습니다.

---

## 5. Ubuntu 컨테이너 내부 Linux 명령어 실습

Ubuntu 컨테이너 안에서 아래 명령어들을 실행했습니다.

```bash
pwd
ls
whoami
mkdir practice
touch test.txt
cat test.txt
cp test.txt copy.txt
mv copy.txt moved.txt
chmod 755 moved.txt
chmod 644 test.txt
rm moved.txt
```

### 명령어 설명
- `pwd` : 현재 작업 디렉터리 확인
- `ls` : 파일 및 폴더 목록 확인
- `whoami` : 현재 사용자 확인
- `mkdir` : 새 디렉터리 생성
- `touch` : 빈 파일 생성
- `cat` : 파일 내용 확인
- `cp` : 파일 복사
- `mv` : 파일 이동 또는 이름 변경
- `chmod` : 파일 권한 변경
- `rm` : 파일 삭제

---

## 6. 파일 권한 실습

### 사용한 명령어
```bash
chmod 755 moved.txt
chmod 644 test.txt
```

### 권한 의미
- `755`
  - 소유자: 읽기, 쓰기, 실행
  - 그룹: 읽기, 실행
  - 기타 사용자: 읽기, 실행

- `644`
  - 소유자: 읽기, 쓰기
  - 그룹: 읽기
  - 기타 사용자: 읽기

이번 실습을 통해 Linux 파일 권한의 숫자 표기 방식을 이해할 수 있었습니다.

---

## 7. 프로젝트 구조

```bash
docker-assignment/
├── README.md
├── Dockerfile
├── index.html
└── screenshots/
    ├── 01-docker-version.png
    ├── 02-docker-info.png
    ├── 03-hello-world.png
    ├── 04-ubuntu-run.png
    └── 05-linux-commands.png
```

---

## 8. 스크린샷

### 1) Docker Version
![Docker Version](./screenshots/01-docker-version.png)

### 2) Docker Info
![Docker Info](./screenshots/02-docker-info.png)

### 3) Hello World
![Hello World](./screenshots/03-hello-world.png)

### 4) Ubuntu Run
![Ubuntu Run](./screenshots/04-ubuntu-run.png)

### 5) Linux Commands
![Linux Commands](./screenshots/05-linux-commands.png)

---

## 9. 학습 내용 정리
이번 과제를 통해 다음 내용을 학습했습니다.

- Docker Desktop 설치 및 실행
- Docker 버전 및 상태 확인
- `hello-world` 컨테이너 실행
- Ubuntu 컨테이너 접속
- Linux 기본 명령어 실습
- 파일 권한(`chmod`) 개념 이해
- 프로젝트 구조 정리 및 README 작성

---

## 10. 느낀 점
이번 실습을 통해 Docker가 로컬 환경과 분리된 독립적인 실행 환경을 제공한다는 점을 직접 확인할 수 있었습니다.  
또한 Ubuntu 컨테이너 내부에서 Linux 명령어를 실행해 보면서 파일 생성, 복사, 이동, 삭제, 권한 변경과 같은 기본적인 시스템 작업을 실습할 수 있었습니다.  
처음에는 Docker 환경 설정 과정이 익숙하지 않았지만, 직접 명령어를 실행하고 결과를 확인하면서 Docker 사용 방식에 대한 이해를 높일 수 있었습니다.
```

---

## 붙여넣은 뒤 확인할 것
1. `README.md` 저장
2. VS Code에서 미리보기 열기 (`Ctrl + Shift + V`)
3. 이미지 5장이 모두 보이는지 확인
4. 안 보이면 파일명이 정확히 아래와 같은지 확인
   - `01-docker-version.png`
   - `02-docker-info.png`
   - `03-hello-world.png`
   - `04-ubuntu-run.png`
   - `05-linux-commands.png`

원하면 다음엔 제가 바로 이어서  
**GitHub 업로드 명령어도 복붙용으로 한 번에** 정리해드릴게요.
