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

<h1>검증</h1>
<b>터미널 기본 조작(파일 및 폴더 관련)<br></b>

- INPUT : `# pwd`
- OUTPUT : `/root/codyssey/docker/front`
- INPUT : `# ls`
- OUTPUT : `dockerfile index.html`
- INPUT : `# vim test.txt`
- INPUT : `# ls`
- OUTPUT : `dockerfile index.html test.txt`
- INPUT : `# mv test.txt ../`
- INPUT : `# cd ..`
- INPUT : `# ls`
- OUTPUT : `front test.txt`
- INPUT : `# rm test.txt`

캡쳐 이미지 = https://github.com/binbin-ai/codyssey/blob/main/terminal/terminal.png


- `docker info`를 통해 도커 정보 확인
- `docker images`를 통해 도커에 설치된 이미지 리스트 확인
- `docker ps -a`를 통해 도커에서 실행중 혹은 실행이 종료된 프로세스 리스트 확인
- `vim dockerfile`를 통해 도커파일 작성
- `docker build -t my-custom-image .`를 통해 작성된 도커파일을 커스텀 이미지로 빌드

<h1>트러블슈팅 2건 이상(문제 → 원인 가설 → 확인 → 해결/대안)</h1>
<b>트러블슈팅 X</b>
