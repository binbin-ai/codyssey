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
<b>[O] 터미널 조작 로그<br></b>
<b>[O] 권한 실습<br></b>
<b>[O] Docker 설치 및 기본 점검<br></b>
<b>[O] Docker 기본 운영 명령 수행<br></b>
<b>[O] 컨테이너 실행 실습<br></b>
<b>[O] 기존 Dockerfile 기반 커스텀 이미지 제작<br></b>
<b>[O] 포트 매핑<br></b>
<b>[O] Docker 볼륨<br></b>
<b>[O] Git 설정 및 GitHub 연동<br></b>

<h1>검증 방법(어떤 명령으로 무엇을 확인했는지)</h1>
<b>[모든 증명을 스크린샷을 통해 이루어졌으며 해당 리포지토리에 존재함을 알립니다.]<br></b>
<li>`docker --version`을 통해 도커 버전 확인</li>
<li>`docker info`를 통해 도커 정보 확인</li>
<li>`docker images`를 통해 도커에 설치된 이미지 리스트 확인</li>
<li>`docker ps -a`를 통해 도커에서 실행중 혹은 실행이 종료된 프로세스 리스트 확인</li>
<li>`vim dockerfile`를 통해 도커파일 작성</li>
<li>`docker build -t my-custom-image .`를 통해 작성된 도커파일을 커스텀 이미지로 빌드</li>

<h1>트러블슈팅 2건 이상(문제 → 원인 가설 → 확인 → 해결/대안)</h1>
<b>트러블슈팅 X</b>b>
