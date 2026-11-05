# Docker 실습 보고서

## 1. 실습 개요
본 문서는 Windows 환경에서 Docker Desktop을 설치하고, 컨테이너 및 이미지 실습, Dockerfile 빌드, 포트 매핑, 볼륨 마운트, GitHub 업로드까지 수행한 결과를 정리한 보고서이다.

---

## 2. 개발 환경
- 운영체제: Windows
- 편집기: VS Code
- 형상관리: Git, GitHub
- 컨테이너 도구: Docker Desktop (WSL2 기반)

---

## 3. 프로젝트 구조

```text
docker-assignment/
├─ README.md
├─ Dockerfile
├─ index.html
└─ screenshots/
```

- `README.md`: 실습 과정과 실행 결과를 정리한 문서
- `Dockerfile`: 사용자 정의 이미지를 빌드하기 위한 설정 파일
- `index.html`: 포트 매핑 테스트용 웹 페이지
- `screenshots/`: 실행 결과 캡처 이미지 저장 폴더

---

## 4. Docker 버전 및 실행 환경 확인

### 실행 명령

```powershell
docker --version
docker info
```

### 실행 결과

```powershell
[여기에 실제 출력 붙여넣기]
```

![Docker 버전 확인](screenshots/01-docker-version.png)
![Docker 정보 확인](screenshots/02-docker-info.png)

### 설명
- `docker --version`은 Docker CLI 버전을 확인하는 명령이다.
- `docker info`는 Docker 데몬이 정상 동작 중인지 확인하는 데 사용하였다.

---

## 5. hello-world 실행 결과

### 실행 명령

```powershell
docker run hello-world
```

### 실행 결과

```powershell
[여기에 실제 출력 붙여넣기]
```

![hello-world 실행 결과](screenshots/03-hello-world.png)

### 설명
`hello-world` 이미지는 Docker 설치와 실행이 정상인지 가장 간단하게 확인할 수 있는 테스트용 이미지이다.

---

## 6. Docker 이미지 목록 확인

### 실행 명령

```powershell
docker images
```

### 실행 결과

```powershell
[여기에 실제 출력 붙여넣기]
```

![Docker 이미지 목록](screenshots/04-docker-images.png)

### 설명
이 명령으로 현재 로컬에 저장된 이미지 목록을 확인하였다.

---

## 7. Ubuntu 컨테이너 실습

### 실행 명령

```powershell
docker run -it --name ubuntu-practice ubuntu bash
```

컨테이너 내부에서 아래 명령을 실행하였다.
