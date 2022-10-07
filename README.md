# Ya NolA~(가제)

<h2>1. Goal of the Project</h2>

:bulb: 온라인 게임으로 신나는 레크레이션을!!😆<br><br><br>

<h2>2. Team Members</h2><br>

:seedling: 천보라 - 프로젝트 설정, 게임 구현, DB, 랭킹 서버, 이미지 서버 구축, 메인페이지 UI<br>

:seedling: 문형기 - 게임 구현, DB, 마이페이지, 로그인 세션, 이미지 서버 구축<br>

:seedling: 서영석 - 프로젝트 설정, 게임 구현, DB, 로그인, 랭킹 서버, 이미지 서버 구축<br>

:seedling: 오치헌 - 게임 구현, DB, 채팅창, 로그인 세션, 메인페이지 UI<br><br><br>

<h2>3. Requirements Analysis</h2><br>

 :four_leaf_clover: usecase Join<br>
- 설명 : 게임 플레이를 위한 회원가입<br>
- 사전 조건 : 사용자 회원 가입 미완료<br>
- 사후 상태 : 회원가입 완료, 로그인 가능<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 회원가입 요청<br>
    3. 정보(그룹아이디) 입력<br>
  - system(백엔드)<br>
     2. 회원가입 페이지<br>
     4. 가입완료 페이지<br>
- 예외 발생 : 아이디 중복 -> 경고창 띄움<br><br>


 :four_leaf_clover: usecase Login<br>
- 설명 : 게임 플레이 및 정보 조회를 위한 로그인<br>
- 사전 조건 : 회원가입 완료 상태<br>
- 사후 상태 : 로그인 완료<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 로그인 요청<br>
    3. 그룹 아이디 입력<br>
  - system(백엔드)<br>
    2. 로그인 페이지<br>
    4. 아이디 일치 여부 확인 후 세션 처리<br>
- 예외 발생 : 아이디 불일치 계정의 로그인 시도 -> 오류 문구 출력(모달)<br><br>



 :four_leaf_clover: usecase Logout<br>
- 설명 : 로그아웃<br>
- 사전 조건 : 로그인 상태<br>
- 사후 상태 : 로그아웃 완료<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 로그아웃 요청<br>
  - system(백엔드)<br>
    2. 세션 제거<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Main page<br>
- 설명 : 사이트 요약 페이지, 로그인/아웃, 랭킹, 설정, 마이페이지, 마일리지<br>
- 사전 조건 : 그룹 플레이어의 접속<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
  1. 홈페이지 접속<br>
  - system(백엔드)<br>
  2. 홈페이지 호출<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Mileage<br>
- 설명 : 마일리지 현황만 확인<br>
- 사전 조건 : 그룹 플레이어의 요청<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 홈페이지 접속<br>
    3. Mileage 선택<br>
  - system(백엔드)<br>
    2. 홈페이지호출<br>
    4. Mileage 현황만 팝업 호출<br>
- 예외 발생 : 無<br><br>


 :four_leaf_clover: usecase Ranking<br>
- 설명 : 랭킹 정보(rank, group Id, score, playtime) 확인<br>
- 사전 조건 : 로그인 상태, 그룹 플레이어의 요청<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 홈페이지 접속<br>
    3.  Ranking 선택<br>
  - system(백엔드)<br>
    2. 홈페이지 호출<br>
    4. Score 호출<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Store<br>
- 설명 : 게임 아이템 종류 확인 및 구매, 구매 후 보유 아이템 확인 바로가기, 구매 취소<br>
- 사전 조건 : 로그인 상태 및 아이템 선택 완료<br>
- 사후 상태 : 구매 완료 or 구매 취소<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. Store 페이지 요청<br>
    3. Item image 클릭 시<br>
    5. Yes 클릭 시 / No 클릭 시<br>
    7.  Item Inventory 바로가기 클릭 시<br>
  - system(백엔드)<br>
    2. 구매 가능한 Item 리스트 호출<br>
    4. 구매하시겠습니까? 팝업 호출<br>
    6. 구매 완료 페이지 호출 / Store 페이지로 콜백<br>
    8. 보유 중인 Item Iist 호출(Item Inventory)<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Mypage<br>
- 설명 : 그룹명, Mileage 내역/현황, Score, playtime, 보유 Item 확인<br>
- 사전 조건 : 로그인 상태, 그룹 플레이어의 요청<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 홈페이지 접속<br>
    3. Mypage 선택<br>
  - system(백엔드)<br>
    2. 홈페이지 호출<br>
    4. Score list, playtime list, Item Inventory, Mileage 내역 호출<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Mypage - Mileage<br>
- 설명 : 마일리지 내역 조회<br>
- 사전 조건 : 로그인 상태, 마이페이지 선택<br>
- 사후 상태 : 마일리지 내역 확인<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 마이페이지 -> 마일리지 내역 요청<br>
  - system(백엔드)<br>
    2. 마일리지 정보 호출<br>
       (마일리지 획득일, 마일리지 사용일, 마일리지 현황)<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Mypage - Item Inventory<br>
- 설명 : 아이템 보유 현황<br>
- 사전 조건 : 로그인 상태, 마이페이지 선택<br>
- 사후 상태 : 아이템 보유 현황 확인<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 마이페이지 -> 아이템 보유 현황 요청<br>
  - system(백엔드)<br>
    2. 로그인한 계정의 아이템 보유 내역 호출<br>
- 예외 발생 : 無<br><br>


 :four_leaf_clover: usecase Item 구매 후 Mileage<br>
- 설명 : Item 구매 후 Mileage 현황 확인<br>
- 사전 조건 : 로그인 상태, 메뉴<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. Store 페이지 요청<br>
    3. Item image 클릭 시<br>
    5. Yes 클릭 시 / No 클릭 시<br>
    7.  Item Inventory 바로가기 클릭 시<br>
  - system(백엔드)<br>
    2. 구매 가능한 Item 리스트 호출<br>
    4. 구매하시겠습니까? 팝업 호출<br>
    6. 구매 완료 페이지 호출 / Store 페이지로 콜백<br>
    8. 보유 중인 Item Iist 호출(Item Inventory)<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase 도발하러 가기<br>
- 설명 : 실시간 채팅<br>
- 사전 조건 : 그룹 플레이어의 요청<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 홈페이지 접속<br>
    3.  도발하러 가기 선택<br>
  - system(백엔드)<br>
    2. 홈페이지 호출<br>
    4. 채팅 페이지 팝업 호출<br>
예외 발생 : 無<br><br>


 :four_leaf_clover: usecase 게임을 시작해볼까?<br>
- 설명 : 게임 실행<br>
- 사전 조건 : 그룹 플레이어의 요청<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 홈페이지 접속<br>
    3.  게임을 시작해볼까? 클릭 시<br>
    5. Start 클릭 시<br>
  - system(백엔드)<br>
    2. 홈페이지 호출<br>
    4. Tetris Start 모달 호출<br>
    6. Tetris 게임 페이지 호출<br>
- 예외 발생 : 無<br><br>



 :four_leaf_clover: usecase Setting<br>
- 설명 : 다크모드로 테마 변경, 글씨체 변경<br>
- 사전 조건 : 그룹 플레이어의 요청<br>
- 사후 상태 : 그룹 플레이어 정보 습득<br>
- 기본 흐름 :<br>
  - actor(유저화면)<br>
    1. 홈페이지 접속<br>
    3.  Setting 선택<br>
    5. Dark mode/산세체 클릭 시<br>
  - system(백엔드)<br>
    2. 홈페이지 호출<br>
    4. Setting 페이지 호출<br>
    6. 전체 페이지에 다크모드/산세체 적용<br>
- 예외 발생 : 無<br><br>



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
<img src="https://img.shields.io/badge/apache tomcat-382856?style=for-the-badge&logo=apachetomcat&logoColor=white">
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
 <img src="https://img.shields.io/badge/Eclipse IDE-456789?style=for-the-badge&logo=Eclipse IDE&logoColor=white">
 <img src="https://img.shields.io/badge/Visual Studio Code-007ACC?style=for-the-badge&logo=Visual Studio Code&logoColor=white">
 <img src="https://img.shields.io/badge/IntelliJ IDEA-254685?style=for-the-badge&logo=IntelliJ IDEA&logoColor=white">
 <img src="https://img.shields.io/badge/SQLite-543879?style=for-the-badge&logo=SQLite&logoColor=white">
 </p>
</div>

