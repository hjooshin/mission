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
PS C:\Users\hjoos> docker --version
Docker version 29.9.2, build a82e528

PS C:\Users\hjoos> docker info
Client:
 Version:    29.9.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.98.0
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.35
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-pass.exe
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-sandbox.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     C:\Users\hjoos\.docker\cli-plugins\docker-scout.exe

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.54.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 12
 Total Memory: 7.43GiB
 Name: docker-desktop
 ID: ec7c45c7-02e5-4a74-bc10-afaeebc246e9
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
```

![Docker 버전 확인](screenshots/01-docker-version.png)
![Docker 정보 확인](screenshots/02-docker-info.png)

### 설명
- `docker --version` 명령을 통해 설치된 Docker 버전을 확인하였다.
- `docker info` 명령을 통해 Docker 클라이언트와 서버 정보, 실행 환경, 운영체제, 커널 버전 등을 확인하였다.
- 출력 결과를 통해 Docker Desktop이 정상적으로 실행 중이며, WSL2 기반 Linux 환경에서 동작하고 있음을 확인하였다.

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
