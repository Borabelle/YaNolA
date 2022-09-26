# Ya NolA~(가제)

<h2>1. Goal of the Project</h2>

:bulb: 온라인 게임으로 신나는 레크레이션을!!😆<br><br><br>

<h2>2. Team Members</h2><br>

:seedling: 천보라 - 프로젝트 설정, 게임 구현, 게임 튜토리얼, DB, admin 랭킹 관리, user 랭킹 통계, admin 회원관리, admin 몸풀기게임, store 매출 통계, 이미지 서버 구축<br>

:seedling: 문형기 - 게임 구현, 게임 튜토리얼, DB, user 마이페이지, 계정 탈퇴, 마일리지 현황, 주문 목록, 아이템 사용 현황, store 매출 통계, user 몸풀기게임<br>

:seedling: 서영석 - 프로젝트 설정, 게임 구현, 게임 튜토리얼, 이미지 서버 구축, DB, admin 아이템관리, API, admin 몸풀기게임, 주문 목록, 아이템 사용 현황<br>

:seedling: 오치헌 - 게임 구현, 게임 튜토리얼, DB, 채팅창, 마일리지 현황, 로그인, 로그아웃, 아이디/비번 찾기, user 회원 가입, user 마이페이지, 계정 탈퇴, user 몸풀기 게임<br><br><br>

<h2>3. Requirement Analysis</h2><br>

 :four_leaf_clover: 메인페이지<br>
 1) 게임/채팅/로그인/랭킹 바로가기 버튼<br>
 2) 메인페이지 배경음악<br><br>


 :four_leaf_clover: 전반적인 기능<br>
 1) 사회자id / 그룹id 나누어 구현 -> all<br><br>


 :four_leaf_clover: 채팅 기능(socket.io)<br>
 1) 사회자와의 개인 채팅(DM)<br>
 2) 다른 팀과의 채팅(사회자도 참여 가능)<br>
 3) 키보드창 팝업 구현<br><br>


 :four_leaf_clover: 게임 구현<br>
 1) 미니게임 4가지<br>
    확정 : 오목, 테트리스, 카드 게임(maybe 메모리)<br>
    후보 : 빙고, 오셀로, 행맨, 2048, 사천성, 가위바위보 하나빼기, 하우로우세븐, 월남뽕, 원카드 등<br>
 2) 게임별 배경음악<br>
 3) 플레이키 별 음<br><br>


 :four_leaf_clover: 게임 튜토리얼<br><br>


 :four_leaf_clover: 아이템 스토어 구현<br>
 -> 랭킹별 지급 마일리지 고정(?)<br>
 benefit : 본인 팀에 적용시키기 위해 구매<br>
    a) 시간연장 아이템<br>
    b) 플러스된 시간 무효화(선착순일 경우 카운트x) 아이템<br>
    c) 점수 더블 아이템<br>
 penalty : 상대 팀에 적용시키기 위해 구매<br>
    a) 제한 시간 아이템<br>
    b) 앞전 경기 무효화 아이템<br>
    c) 점수 디스카운트 아이템<br><br>

 -> 아이템 배포용 게임<br>
    a) ex) 가위바위보 게임<br>
    b) 순위별 아이템 갯수 혹은 퀄리티 차등 지급<br><br>

-> 도발용 아이템<br><br>


 :four_leaf_clover: 점수 기능<br>
 1) Rank : like 오락실 랭킹<br>
    -> id, 플레이시간(선착순 게임), ranking<br>
    -> 게임별 랭킹 및 총점 합산<br>
 2) 점수 초기화<br><br>


 :four_leaf_clover: 설정
 1) 키보드, 메인화면 등 테마 변경
 2) 다크모드 지원<br><br><br>


<h2>4. Definitions of Domain Terms</h2><br>

**:sunflower:Host 사회자**<br>
&nbsp;&nbsp;&nbsp;&nbsp; hostId 사회자 아이디(String)<br>
&nbsp;&nbsp;&nbsp;&nbsp; groupAdminId 그룹 관리 아이디(String)<br>
&nbsp;&nbsp;&nbsp;&nbsp; group 그룹 정보 (group)<br><br>

:sunflower:**Group 플레이어 그룹**<br>
&nbsp;&nbsp;&nbsp;&nbsp; groupId 그룹 아이디(String)<br>
&nbsp;&nbsp;&nbsp;&nbsp; groupRank 그룹 랭킹(int)<br>
&nbsp;&nbsp;&nbsp;&nbsp; groupScore 그룹 점수(int)<br>
&nbsp;&nbsp;&nbsp;&nbsp; groupMileage 그룹 마일리지(var)<br>
&nbsp;&nbsp;&nbsp;&nbsp; groupItem 구입한 아이템(itemInfo)<br>
&nbsp;&nbsp;&nbsp;&nbsp; purchaseDateOfItem 아이템 구입일시(date)<br>
&nbsp;&nbsp;&nbsp;&nbsp; usedDateOfItem 아이템 사용일시(date)<br><br>

:sunflower:**gameItem 아이템**<br>
&nbsp;&nbsp;&nbsp;&nbsp; category 아이템 종류(String)<br>
&nbsp;&nbsp;&nbsp;&nbsp; price 아이템 가격(마일리지와 연동)(int)(<br>
&nbsp;&nbsp;&nbsp;&nbsp; itemUsage 아이템 용도(아이템과 연동)(boolean)<br><br>

:sunflower:**itemInfo 아이템 정보**(all method)<br>
&nbsp;&nbsp;&nbsp;&nbsp; annulTimeItem 1등 팀과 비교해 플러스된 시간 무효화 아이템<br>
&nbsp;&nbsp;&nbsp;&nbsp; doublingScoreItem 점수 2배 베네핏 아이템<br>
&nbsp;&nbsp;&nbsp;&nbsp; limitTimeItem 시간제한 아이템<br>
&nbsp;&nbsp;&nbsp;&nbsp; annulMatchItem 경기 무효화 아이템<br>
&nbsp;&nbsp;&nbsp;&nbsp; discountScoreItem 점수 디스카운트 아이템<br>
&nbsp;&nbsp;&nbsp;&nbsp; fasterSpeedItem 테트리스 블록 속도 빠르게<br>
&nbsp;&nbsp;&nbsp;&nbsp; slowerSpeedItem 테트리스 블록 속도 느리게<br><br><br>

<h2>5. DB ERD</h2><br>

<h2>6. Stack</h2><br>
<div>
<p>
<h3>Front</h3>
<img src="https://img.shields.io/badge/html-E34F26?style=for-the-badge&logo=html5&logoColor=white">
<img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white">
<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black">
<img src="https://img.shields.io/badge/next.js-4FC08D?style=for-the-badge&logo=next.js&logoColor=white">
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
<img src="https://img.shields.io/badge/Tailwind CSS-06B6D4?style=for-the-badge&logo=Tailwind CSS&logoColor=black">
<img src="https://img.shields.io/badge/PostCSS-DD3A0A?style=for-the-badge&logo=PostCSS&logoColor=black">
</p>
</div>
<div>
<p>
<h3>Backend</h3>
<img src="https://img.shields.io/badge/JAVA-007396?style=for-the-badge&logo=java&logoColor=white">
<img src="https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=SpringBoot&logoColor=white">
<img src="https://img.shields.io/badge/oracle-FF9E0F?style=for-the-badge&logo=oracle&logoColor=white">
<img src="https://img.shields.io/badge/apache tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=white">
</p>
</div>
<div>
 <p>
  <h3>Collaboration Tools</h3>
 <img src="https://img.shields.io/badge/slack-4A154B?style=for-the-badge&logo=slack&logoColor=white">
 <img src="https://img.shields.io/badge/zoom-1C9AD6?style=for-the-badge&logo=zoom&logoColor=white">
 <img src="https://img.shields.io/badge/github-589465?style=for-the-badge&logo=github&logoColor=white">
 <img src="https://img.shields.io/badge/discord-5865F2?style=for-the-badge&logo=discord&logoColor=white">
 </p>
</div>
<div>
 <p>
  <h3>IDE</h3>
 <img src="https://img.shields.io/badge/Eclipse IDE-2C2255?style=for-the-badge&logo=Eclipse IDE&logoColor=white">
 <img src="https://img.shields.io/badge/Visual Studio Code-007ACC?style=for-the-badge&logo=Visual Studio Code&logoColor=white">
 <img src="https://img.shields.io/badge/IntelliJ IDEA-254685?style=for-the-badge&logo=IntelliJ IDEA&logoColor=black">
 <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=SQLite&logoColor=white">
 </p>
</div>

