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
&nbsp; Host_id 사회자 아이디<br>
&nbsp; Host_pw 사회자 비밀번호<br>
&nbsp; User_id 그룹 아이디<br>
&nbsp; Host_admin 사회자 관리<br>
&nbsp; Item_admin 아이템 관리<br>
&nbsp; User_info 그룹 정보<br><br>


:sunflower:**User 그룹**<br>
&nbsp; User_Id 그룹 아이디<br>
&nbsp; User_Pw 그룹 비밀번호<br>
&nbsp; User_Name 그룹 닉네임<br>
&nbsp; User_Rank 랭킹<br>
&nbsp; User_Mileage 마일리지<br> 
&nbsp; User_registerDate 가입일<br>
&nbsp; User_Item 구입한 아이템<br>
&nbsp; User_buyItem 아이템 구입일시<br>
&nbsp; User_useItem 아이템 사용일시<br><br>
  
:sunflower:**ItemInfo 아이템 정보**<br>
&nbsp; Item_category 아이템 종류<br>
&nbsp; Item_price 아이템 가격  
&nbsp; Item_usage 아이템 용도<br><br>

:sunflower:**Item 아이템**<br>
&nbsp; AnnulTime_Item 플러스된 시간 무효화 아이템<br>
&nbsp; DoublingScore_Item 점수 2배 베네핏 아이템<br>
&nbsp; LimitTime_Item 시간제한 아이템<br>
&nbsp; AnnulMatch_Item 경기 무효화 아이템<br>
&nbsp; DiscountScore_Item 점수 디스카운트 아이템<br>
&nbsp; FasterSpeed_Item 테트리스 블록 속도 빠르게<br>
&nbsp; SlowerSpeed_Item 테트리스 블록 속도 느리게<br><br>

:sunflower:**UserMileage**<br>
&nbsp; Mileage_status 마일리지 현황<br>
&nbsp; User_Mileage 마일리지<br> 
&nbsp; Used_Mileage 사용된 마일리지<br>
&nbsp; Gain_Mileage 획득한 마일리지
&nbsp; UsedTime_Mileage <br><br>

:sunflower:**HostAdmin**<br>
&nbsp; Host_admin 사회자 관리<br><br>

:sunflower:**UserInfo**<br>
&nbsp; User_info 그룹 정보<br><br>

:sunflower:**ItemAdmin**<br>
&nbsp; Item_admin 아이템 관리<br><br><br>

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

