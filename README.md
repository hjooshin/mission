# Docker 개발환경 구축 및 Ubuntu 컨테이너 실습

## 1. 프로젝트 개요
본 과제에서는 Windows 환경에 Docker 개발환경을 구축하고, Docker Desktop이 정상적으로 동작하는지 확인하였다.  
이후 `hello-world` 이미지와 `ubuntu` 이미지를 실행하여 컨테이너 동작을 검증하였고, Ubuntu 컨테이너 내부에서 Linux 기본 명령어 및 파일/디렉토리 관리 명령어를 실습하였다.

---

## 2. 개발 환경
- OS: Windows
- Editor: Visual Studio Code
- Terminal: PowerShell
- Version Control: Git for Windows
- Container Platform: Docker Desktop
- Backend: WSL2

---

## 3. 설치 및 환경 구성

### 3.1 Visual Studio Code 설치
Markdown 문서 작성 및 개발환경 구성을 위해 Visual Studio Code를 설치하였다.

### 3.2 Git for Windows 설치
Git 명령어 사용 및 버전 관리 환경 구성을 위해 Git for Windows를 설치하였다.

### 3.3 Docker Desktop 설치
Windows 환경에서 컨테이너를 실행하기 위해 Docker Desktop을 설치하였다.  
설치 후 WSL2 기반 엔진을 사용하도록 설정하였다.

---

## 4. 문제 해결 과정

Docker Desktop 실행 과정에서 WSL2 및 Virtual Machine Platform 관련 오류가 발생하였다.  
이는 Windows에서 WSL2 기반 Docker 실행에 필요한 기능이 완전히 준비되지 않았기 때문이었다.

### 해결 방법
관리자 권한 PowerShell에서 아래 명령어를 실행하였다.

```powershell
wsl --install
```

이후 시스템을 재부팅하고 Docker Desktop을 다시 실행하여 문제를 해결하였다.

---

## 5. Docker 동작 확인

### 5.1 hello-world 이미지 실행
Docker가 정상적으로 설치되었는지 확인하기 위해 아래 명령어를 실행하였다.

```powershell
docker run hello-world
```

실행 결과, Docker가 이미지를 다운로드한 뒤 테스트 메시지를 출력하였고, 이를 통해 Docker가 정상 동작함을 확인하였다.

### 5.2 Ubuntu 컨테이너 실행
Ubuntu 컨테이너를 실행하기 위해 아래 명령어를 입력하였다.

```powershell
docker run -it ubuntu bash
```

처음 실행 시 로컬에 Ubuntu 이미지가 없었기 때문에 이미지가 자동으로 다운로드되었다.  
이후 아래와 같은 형태의 프롬프트가 출력되었다.

```bash
root@컨테이너ID:/#
```

이는 Ubuntu 컨테이너 내부에 정상적으로 접속되었음을 의미한다.

---

## 6. 컨테이너 상태 확인

실행 후 PowerShell에서 아래 명령어를 사용하여 컨테이너 상태를 확인하였다.

```powershell
docker ps -a
```

확인된 결과는 다음과 같았다.

```powershell
CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS                      PORTS     NAMES
f2a3571c4a44   ubuntu        "bash"     3 minutes ago   Exited (0) 12 seconds ago             modest_robinson
2c31a90497bb   hello-world   "/hello"   5 minutes ago   Exited (0) 5 minutes ago              stoic_poitras
```

여기서 `Exited (0)`는 에러 없이 정상적으로 종료되었음을 의미한다.

---

## 7. Ubuntu 컨테이너 실습

Ubuntu 컨테이너 내부에서 기본 Linux 명령어와 파일/디렉토리 관리 명령어를 실습하였다.

### 7.1 현재 위치 및 사용자 확인

```bash
pwd
ls
whoami
```

- `pwd`: 현재 작업 중인 디렉토리 경로를 확인한다.
- `ls`: 현재 디렉토리의 파일 및 폴더 목록을 확인한다.
- `whoami`: 현재 사용자 계정을 확인한다.

---

### 7.2 디렉토리 생성 및 이동

```bash
mkdir practice
cd practice
pwd
```

- `mkdir practice`: `practice` 디렉토리를 생성한다.
- `cd practice`: 생성한 디렉토리로 이동한다.
- `pwd`: 현재 위치가 변경되었는지 확인한다.

---

### 7.3 파일 생성 및 내용 작성

```bash
touch test.txt
ls
echo "hello docker" > test.txt
cat test.txt
```

- `touch test.txt`: 빈 파일을 생성한다.
- `ls`: 파일 생성 여부를 확인한다.
- `echo "hello docker" > test.txt`: 파일에 문자열을 저장한다.
- `cat test.txt`: 파일 내용을 출력하여 저장 결과를 확인한다.

---

### 7.4 파일 복사 및 이름 변경

```bash
cp test.txt copy.txt
ls
mv copy.txt moved.txt
ls
```

- `cp test.txt copy.txt`: `test.txt`를 `copy.txt`로 복사한다.
- `ls`: 복사된 파일이 생성되었는지 확인한다.
- `mv copy.txt moved.txt`: `copy.txt`의 이름을 `moved.txt`로 변경한다.
- `ls`: 이름 변경 결과를 확인한다.

---

### 7.5 파일 권한 변경

```bash
chmod 644 test.txt
ls -l
```

- `chmod 644 test.txt`: 파일 권한을 변경한다.
- `ls -l`: 파일 권한 정보를 자세히 확인한다.

`644`의 의미는 다음과 같다.

- 소유자(owner): 읽기, 쓰기 = `rw-`
- 그룹(group): 읽기 = `r--`
- 기타 사용자(others): 읽기 = `r--`

권한 숫자의 의미는 다음과 같다.

- `4` = 읽기(read)
- `2` = 쓰기(write)
- `1` = 실행(execute)

따라서:
- `7` = `rwx`
- `6` = `rw-`
- `5` = `r-x`
- `4` = `r--`

---

### 7.6 파일 삭제

```bash
rm moved.txt
ls
```

- `rm moved.txt`: 파일을 삭제한다.
- `ls`: 삭제 여부를 확인한다.

---

## 8. 컨테이너 재시작 및 재접속

Ubuntu 컨테이너에서 `exit` 명령어를 입력하면 컨테이너가 종료된다.  
종료된 컨테이너는 아래 명령어로 다시 시작하고 접속할 수 있다.

```powershell
docker start -ai modest_robinson
```

- `start`: 중지된 컨테이너를 다시 시작한다.
- `-a`: 표준 출력에 연결한다.
- `-i`: 입력이 가능하도록 연결한다.

이를 통해 기존에 생성한 컨테이너를 재사용할 수 있었다.

---

## 9. 실습을 통해 배운 점

이번 실습을 통해 Docker 이미지와 컨테이너의 개념을 직접 확인할 수 있었다.  
특히 `hello-world`를 통해 Docker 설치 상태를 검증하고, `ubuntu` 컨테이너 내부에서 Linux 명령어를 실행하면서 컨테이너 기반 환경에 익숙해질 수 있었다.

또한 파일 생성, 복사, 이동, 삭제와 같은 기본 명령어뿐 아니라 `chmod`를 이용한 권한 변경까지 실습하면서 Linux 파일 시스템과 권한 구조에 대한 이해를 높일 수 있었다.  
Windows 환경에서도 WSL2를 활용하면 Docker를 원활하게 사용할 수 있다는 점을 확인하였다.

---

## 10. 결론

Docker Desktop, WSL2, Ubuntu 컨테이너를 활용하여 Windows 환경에서 기본적인 컨테이너 개발환경을 성공적으로 구축하였다.  이후 Linux 명령어 실습을 통해 컨테이너 내부 환경을 직접 다뤄봄으로써 Docker 사용의 기초를 익힐 수 있었다.
