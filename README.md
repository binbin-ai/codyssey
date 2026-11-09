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

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/docker%20ubuntu/docker%20ubuntu.png

<h1>트러블슈팅 2건 이상(문제 → 원인 가설 → 확인 → 해결/대안)</h1>
<b>트러블슈팅 X</b>
