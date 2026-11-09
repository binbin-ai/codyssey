<h1>프로젝트 개요(미션 목표 요약)</h1>
<li> 컴퓨터 관련 종사자가 아니라면 잘 사용하지 않는 리눅스라는 운영체제의 활용법을 숙지할수있다. </li>
<li> 도커를 활용하여 편리하고 간단하게 서비스를 구축하고 배포할수있다. </li>
<li> git/github를 활용하여 개발 소프트웨어의 버전 관리 및 협업도구로써 이용할수있다. </li>

<h1>실행 환경(OS/쉘/터미널, Docker 버전, Git 버전)</h1>
<b>Host OS : win11<br></b>
<b>VM OS : kali<br></b>
<b>Docker ver : 28.5.2+dfsg4<br></b>
<b>git ver : 2.56.0.windows.3<br></b>

<h1>수행 항목 체크리스트(터미널/권한/Docker/Dockerfile/포트/볼륨/Git/GitHub)</h1>
<b>[O] 터미널 기본 조작 및 폴더 구성<br></b>
<b>[O] 권한 변경 실습<br></b>
<b>[O] Docker 설치/점검<br></b>
<b>[O] hello-world 실행<br></b>
<b>[O] Dockerfile 빌드/실행<br></b>
<b>[O] 포트 매핑 접속(2회)<br></b>
<b>[O] 바인드 마운트 반영<br></b>
<b>[O] 볼륨 영속성<br></b>
<b>[O] Git 설정 + VSCode GitHub 연동<br></b>

<h1>검증(수행 로그 발췌 및 캡쳐 이미지 첨부)</h1>
<b>터미널 기본 조작(파일 및 폴더 관련)<br></b>

```bash
# pwd
/root/codyssey/docker/front
# ls
dockerfile index.html
# vim test.txt
# ls
dockerfile index.html test.txt
# mv test.txt ../
# cd ..
# ls
front test.txt
# rm test.txt
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/terminal/terminal.png

<b>권한 변경<br></b>

```bash
# ls
test_c.cpp  test_c.out
# ls -l
total 20
-rw-r--r-- 1 root root   102 Nov  6 01:34 test_c.cpp
-rwxr-xr-x 1 root root 16280 Nov  6 01:34 test_c.out
# chmod -r test_c.cpp
# ls -l
total 20
--w------- 1 root root   102 Nov  6 01:34 test_c.cpp
-rwxr-xr-x 1 root root 16280 Nov  6 01:34 test_c.out
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/authority/1.png

<b>Docker 정보 및 버전 확인<br></b>

도커 정보 확인
```bash
# docker info
Client:
Version:    28.5.2+dfsg4
Context:    default
Debug Mode: false
Plugins:
buildx: Docker Buildx (Docker Inc.)
Version:  0.29.1+ds1
Path:     /usr/libexec/docker/cli-plugins/docker-buildx

Server:
 Containers: 1
  Running: 1
  Paused: 0
  Stopped: 0
 Images: 1
 Server Version: 28.5.2+dfsg4
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: systemd
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 
 runc version: 1.3.6+ds1-1
 init version: 
 Security Options:
  apparmor
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.16.8+kali-amd64
 Operating System: Kali GNU/Linux Rolling
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 7.724GiB
 Name: kali
 ID: 6866a4df-63fa-4759-8a4e-87b5cceddd24
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
```

도커 버전 확인
```bash
# docker --version
Docker version 28.5.2+dfsg4, build 9cc6dea35e9a963f281434761c656fba4ac43aed
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/tree/main/docker%20basic

<b>hello-world<br></b>

```bash
# docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/hello%20world/hello%20world.png

<b>Dockerfile 작성/빌드/실행<br></b>

작성
```bash
FROM httpd:latest

COPY . /usr/local/apache2/htdocs/

EXPOSE 80
```

빌드 && 실행
```bash
# docker build -t my-custom-image .
[+] Building 0.1s (7/7) FINISHED                                                        docker:default
 => [internal] load build definition from dockerfile                                              0.0s
 => => transferring dockerfile: 101B                                                              0.0s
 => [internal] load metadata for docker.io/library/httpd:latest                                   0.0s
 => [internal] load .dockerignore                                                                 0.0s
 => => transferring context: 2B                                                                   0.0s
 => [internal] load build context                                                                 0.0s
 => => transferring context: 61B                                                                  0.0s
 => [1/2] FROM docker.io/library/httpd:latest                                                     0.0s
 => CACHED [2/2] COPY . /usr/local/apache2/htdocs/                                                0.0s
 => exporting to image                                                                            0.0s
 => => exporting layers                                                                           0.0s
 => => writing image sha256:2bb7e0690e0d2b652bb3037731ba381606a953919d67484e07d7b00e439d9b70       0.0s
 => => naming to docker.io/library/my-custom-image                                                0.0s
# docker images
REPOSITORY        TAG       IMAGE ID       CREATED        SIZE
my-custom-image   latest    2bb7e0690e0d   10 days ago    117MB
httpd             latest    8110099cc30b   12 days ago    117MB
ubuntu            latest    febc1a2eec1f   56 years ago   102MB
# docker run -d -p 8080:80 --name custom-apache my-custom-image
c5d2d72f603c8f6c04ff5c4399ef1f9d8190b76e66f5df2a3736950447e48051
# docker ps -a
CONTAINER ID   IMAGE             COMMAND              CREATED         STATUS                      PORTS                                   NAMES
c5d2d72f603c   my-custom-image   "httpd-foreground"   7 seconds ago   Up 6 seconds                0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   custom-apache
dfcf4349696b   ubuntu            "bash"               5 days ago      Exited (127) 5 days ago                                             objective_feistel
ad432a5cf3c1   ubuntu            "bash"               5 days ago      Exited (0) 5 days ago                                               happy_golick
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/tree/main/dockefile%20and%20custom%20image

<b>포트 매핑 접속<br></b>

```bash
# docker run -d -p 8080:80 --name apache-8080 my-custom-image
eb84ee63f6eeb0de39305c5eadb3914f81812b7c8741769ba68d379a15b69d64
# docker run -d -p 8081:80 --name apache-8081 my-custom-image
128de4f947556b6050420b7da1b1512a63157ec8d4bca7213606dbfec8f943bd
```

접속 결과는 캡쳐 이미지에

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/tree/main/docker%20port%20mapping

<b>바인드 마운트와 도커 볼륨(데이터 영속성 관련)<br></b>

바인드 마운트
```bash
# docker run -d -p 8080:80 -v ~/codyssey/docker/front:/usr/local/apache2/htdocs/ --name vol-apache my-custom-image
ae29e7b78820321e58e8b4cf0262e9e53e571271a702b41bc3434c727ec6df8c
# vim index.html
# cat index.html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>docker-apache web server</title>
</head>
<body>
    <h1>local vol change index.html</h1>
</body>
</html>
```

도커 볼륨
```bash
# docker run -d -p 8081:80 -v vol-data:/usr/local/apache2/htdocs/ --name vol2-apache my-custom-image
e2d0424796f0fe5c06f69bbffc870b6ce2a25548fd946d9e4e6a7d07c58f3df6
# cd /
# cd var/lib/docker/volumes/vol-data
# ls
_data
# cd _data
# ls
dockerfile  index.html
# vim index.html
# cat index.html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>docker-apache web server</title>
</head>
<body>
    <h1>Volume Persistence</h1>
</body>
</html>
# docker rm -f vol2-apache
vol2-apache
# ls /var/lib/docker/volumes/vol-data/_data
dockerfile  index.html
# cat /var/lib/docker/volumes/vol-data/_data/index.html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>docker-apache web server</title>
</head>
<body>
    <h1>Volume Persistence</h1>
</body>
</html>
```

호스팅 결과는 캡쳐 이미지에

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/tree/main/docker%20vol

<b>Git 설정 + VSCode GitHub 연동<br></b>

git 설정 정보
```bash
PS C:\Users\BININI\Desktop\코디세이\도커\git 연동> git config user.name
박현빈
PS C:\Users\BININI\Desktop\코디세이\도커\git 연동> git config user.email
245053196+binbin-ai@users.noreply.github.com
PS C:\Users\BININI\Desktop\코디세이\도커\git 연동>
```

git 로그
```bash
PS C:\Users\BININI\Desktop\코디세이\도커\git 연동\codyssey> git remote -v
origin  https://github.com/binbin-ai/codyssey.git (fetch)
origin  https://github.com/binbin-ai/codyssey.git (push)
PS C:\Users\BININI\Desktop\코디세이\도커\git 연동\codyssey> git log -3
commit f2a51168e7ad1673d1378f649e1f49d237f160cb (HEAD -> main, origin/main, origin/HEAD)
Author: 박현빈 <245053196+binbin-ai@users.noreply.github.com>
Date:   Tue Nov 10 03:24:46 2026 +0900

    수정

commit ce5ebbac57048238e94bdf24c94aada5e389d12a
Author: 박현빈 <245053196+binbin-ai@users.noreply.github.com>
Date:   Tue Nov 10 02:47:33 2026 +0900

    end
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/vscode-git%20connect/gir%20%26%20vscode%20connect.png

<h1>트러블슈팅</h1>
<b>트러블슈팅 X</b>
