

```md
# Docker Assignment

## 1. 과제 개요
이 저장소는 Docker 기본 실습 과제를 정리한 프로젝트입니다.  
Windows 환경에서 Docker Desktop을 설치하고, Docker 명령어 실행 및 Ubuntu 컨테이너 내부에서 Linux 기본 명령어를 실습했습니다.

## 2. 개발 환경
- OS: Windows
- Editor: VS Code
- Version Control: Git
- Container Tool: Docker Desktop

## 3. Docker 설치 및 확인

### Docker 버전 확인
```bash
docker --version
```

### Docker 상세 정보 확인
```bash
docker info
```

## 4. 컨테이너 실행 실습

### hello-world 실행
```bash
docker run hello-world
```

### Ubuntu 컨테이너 실행
```bash
docker run -it ubuntu bash
```

## 5. Ubuntu 컨테이너 내부 Linux 명령어 실습

Ubuntu 컨테이너 안에서 아래 명령어들을 실습했습니다.

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
rm moved.txt
```

### 실습 내용
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

## 6. 파일 권한 실습

### 예시
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

## 7. 프로젝트 폴더 구조

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

## 8. 스크린샷

### Docker Version
![Docker Version](./screenshots/01-docker-version.png)

### Docker Info
![Docker Info](./screenshots/02-docker-info.png)

### Hello World
![Hello World](./screenshots/03-hello-world.png)

### Ubuntu Run
![Ubuntu Run](./screenshots/04-ubuntu-run.png)

### Linux Commands
![Linux Commands](./screenshots/05-linux-commands.png)

## 9. 학습 내용 정리
이번 과제를 통해 다음 내용을 학습했습니다.

- Docker Desktop 설치 및 실행
- Docker 버전 및 상태 확인
- `hello-world` 컨테이너 실행
- Ubuntu 컨테이너 접속
- Linux 기본 명령어 실습
- 파일 권한(`chmod`) 개념 이해
- 프로젝트 구조 정리 및 README 작성

## 10. 느낀 점
Docker를 직접 설치하고 컨테이너를 실행해 보면서 로컬 환경과 분리된 실행 환경을 만드는 방식이 매우 유용하다는 것을 배웠습니다.  
또한 Ubuntu 컨테이너 안에서 Linux 명령어를 직접 사용해 보며 기본적인 파일 및 권한 관리 방법도 함께 익힐 수 있었습니다.
```

붙여넣은 뒤에는:

1. `Ctrl + S` 저장
2. `Ctrl + Shift + V` 미리보기
3. 이미지 5장 보이는지 확인

원하면 다음엔 제가 **GitHub 업로드 명령어도 한 번에 복붙용으로** 정리해드릴게요.
