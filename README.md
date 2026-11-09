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
...
```

도커 버전 확인
```bash
# docker --version
Docker version 28.5.2+dfsg4, build 9cc6dea35e9a963f281434761c656fba4ac43aed
```

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/tree/main/docker%20basic

<b>hello-world 실행(우분투 컨테이너)<br></b>

```bash
# docker run -it ubuntu bash
root@dfcf4349696b:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@dfcf4349696b:/# echo Hello World
Hello World
```

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
```

호스팅 결과는 캡쳐 이미지에

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/tree/main/docker%20vol

<b>Git 설정 + VSCode GitHub 연동<br></b>

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/vscode-git%20connect/gir%20%26%20vscode%20connect.png

<h1>트러블슈팅</h1>
<b>트러블슈팅 X</b>
