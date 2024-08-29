**프로젝트 요약**

- 직업을 구하는 취업 준비생과 역량을 강화 하고 싶은 청년, 이직을 원하는 근로자, 
인재를 채용을 원하는 기업 모두가 한 곳에서 원하는 정보를 얻을 수 있는 사이트

**역할**

- 총 6명 | Project Leader
- 콘텐츠 기획 및 제작 (기여도 65%)

**기간**

- 2022.02 - 2023.04 (약 3개월)

**기술.**

- Spring Framework, Java, JSP, HTML5, CSS, JavaScript, Oracle, Ajax, JSTL, JSON, slf4j, mybatis
Bootstrap, jQuery, hibernate-validator, SVN, redmine, github, Apache Tomcat

**개발 사항.**

- bootstrap5 기반 UI 디자인
- 로그인 및 회원 가입/SNS 로그인 및 회원 가입 기능 개발
- 아이디 찾기, 비밀번호 변경 기능 개발
- SMTP서버 기반 메일 인증 기능 개발
- SMS API를 이용한 문자 인증 기능 개발
- WebSocket 기반 실시간 채팅 기능 개발
- WebSocket 기반 챗봇 기능 개발
- 일반 회원 마이페이지 정보 관리 및 수정 기능 개발
- 파일 업로드/다운로드 모듈화 기능 개발
- 커뮤니티 및 Ajax를 이용한 비동기 게시판 기능 개발
- 기업 회원 채용공고 등록 및 관리 기능 개발
- 기업 회원 지원자 관리 기능 개발
- 기업 회원과 일반 회원 매칭 시스템 기능 개발

- **소개.**
    
    JAVA줄게(잡아줄게)는 구직을 원하는 일반 회원과 구인이 필요한 기업 회원에게 원하는 조건에 맞는 기능들을 직관적이고 편리하게 정보를 얻을 수 있도록 서비스를 제공하는 웹 서비스를 기반으로 한 프로젝트 입니다.
    
    구직을 원하는 일반 회원에게 **채용 정보**를 제공하고 그 외에 **교육·특강·인턴십 프로그램**, 소통을 위한 **커뮤니티**를 제공합니다.
    인재를 채용하길 원하는 기업 회원에게 **채용 공고**를 등록하거나 멤버십 가입 시 **매칭**을 통해 조건에 맞는 **인재를 추천** 받을 수 있고,  **인턴십**을 등록해 원하는 **인재를 선발** 할 수 있습니다.
    
    저희는 사이트 이용자들이 한 사이트에서 다양한 정보를 얻을 수 있게 하여 **구직 및 구인 시간을 효율적으로 단축** 시킬 것으로 예상합니다.
    

---

### 📝bootstrap5 를 이용한 UI 디자인

- 일반 회원, 기업 회원의 메인 페이지를 각각의 특성에 맞게 불러올 리스트를 출력하고 화면 구성을 하였습니다.
- 

### 📝회원 가입

- 일반 회원 가입과 SNS 회원 가입 두 가지를 구현하였고, 일반 회원 가입의 경우 이메일을 입력하여 존재하는 경우 로그인 페이지로, 존재하지 않는 이메일인 경우 회원 가입 페이지로 이동하게 하였습니다.
- 일반 회원 가입 시 사용자가 필수 입력 사항을 미 입력 하거나 올바른 입력 형태가 아닐 시 hibernate-validation api를 사용하여 validation체크를 해주었고, 사용자에게는 오류 메시지를 출력해주었습니다.
- SNS 회원 가입 시 가입이 완료 되면서 필수 입력 사항을 추가로 입력할 수 있도록 추가 정보 등록 페이지로 이동하게 하였습니다.

### 📝로그인

- 일반 로그인과 SNS 로그인 두 가지를 구현하였고, SNS로 가입한 경우 일반 로그인으로 접속하려 할 경우 사용자에게 alert창으로 ‘SNS로 로그인해주세요’ 라는 메세지를 출력해주었습니다.
- 일반 로그인의 경우 아이디는 이메일 형태가 아닐 시 hibernate-validation api를 사용하여 validation체크를 해주었고 사용자에게는 오류 메시지를 출력해주었습니다.
- 아이디는 이메일 형식으로 입력 해야 하고, 입력한 아이디가 존재하지 않는 경우 회원 가입 페이지로, 존재하는 아이디인 경우 비밀번호 입력 페이지로 이동하게 구현하였습니다.
- 비밀번호 역시 hibernate-validation api를 사용하여 validation체크를 해주었고 사용자에게는 '' 오류메시지를 출력해주었습니다.

### 📝로그인 Security

- xml에 Security dependency를 정의하였습니다. 실질적으로 security를 움직이는 건 security-core이며 나머지 jar들은 자동으로 들어오도록 구현하였습니다.
- AuthenticationProvider을 implements한 CustomAuthenticationProvider클래 스를 생성하고, User를 extends한 CustomUser클래스를 생성했습니다.
- User 클래스에서 우리가 설정한 MemberVO의 enabled 상태를 참고하여 메서드를 간단하게 오버라이딩하였습니다.
- CustomAuthenticationProvider 클래스에서 authenticate 메서드를 오버라이딩하였습니다.
- 앞서 만든 User클래스의 메서드로 로그인 체크를 진행하고 Spring Security 내부 클래스로 인증 토큰을 생성한 뒤 전달할 내용 (id,pwd,auth)을 설정한 후 리턴시켰으며, 성공 시 CustomLoginSuccessHandler로, 실패 시

CustomLoginFailureHandler로 가도록 구현하였습니다.

- LoginSuccessHandler에서는 CustomAuthenticationProvider에서 파라미터로 받은 authentication에서 토큰을 꺼내 session에 MemberVO와 auth(권한)를 set하고 session의 기본 유지 시간을 1시간으로 설정했습니다.
- CustomLoginSuccessHandler에서 권한에 따른 메뉴를 뽑아 권한에 따라 메뉴를 다르게 출력하였습니다.

### 📝일반 회원 - 마이페이지

- 마이페이지에서 지원 현황, 프로필 사진, 회원 정보를 조회할 수 있도록 구현하였습니다.
- 저장된 사진이 없는 경우 기본 이미지가 보이도록 구현하였습니다.

**1) 프로필**

- 프로필 수정 페이지에서 프로필 사진을 클릭하는 경우 등록, 변경할 수 있도록 하였습니다.
- 연락처를 수정하려는 경우 SMS 인증을 받아야 변경할 수 있도록 구현하였습니다.
- 직업을 변경하려는 경우 DB에 등록해 놓은 직군 및 직무를 SELECT BOX에서 검색하거나 선택하여 변경할 수 있도록 구현하였습니다.

**2) 이력서**

- 이력서 페이지에서는 <c:forEach> 태그 안에 <div>를 사용해 현재 등록된 이력서(제목, 등록일) 목록을 확인할 수 있고, <c:if> 태그를 사용하여 대표 이력서로 설정한 경우 별 표시가 보이도록 구현하였습니다.
- 이력서를 등록하는 경우 입력 요소들의 Name을 배열 형태로 담아둔 변수를 선언하고, 각 Name에 해당하는 value값을 배열 형태로 담아둔 변수를 선언하여 <input>태그를 만들어 그 안에 Name에는 Name배열을, value에는 value배열을 입력해 form태그에 append 한 뒤 submit 하도록 구현하였습니다.

**3) 면접제안**

- 면접 제안 페이지에서는 현재 회원의 등록된 이력서들을 조회한 기업이 면접을 제안한 목록을 조회할 수 있도록 구현하였습니다. 면접 제안 <button>을 클릭해 수락하는 경우 서류 합격으로 변경되도록 구현하였습니다.

**4) 프리미엄**

- 프리미엄 페이지에서는 현재 회원이 신청한 강의, 특강 그리고 신청한 인턴십 중 선발되어 참가할 수 있는 인턴십들의 목록을 확인할 수 있도록 구현하였습니다.
- 내 강의 탭에서 신청한 목록을 확인하여, 원하는 강의실 입장 <button>을 클릭하면 강의 소개와 함께 시리즈들을 확인할 수 있고, 강의 수강하기 <button>을 클릭하면 해당 강의 번를 키 값으로 하여 ajax를 통해 첨부파일 목록을 가져와 상단 <div> 영역에 <video> 태그가 보이도록 구현하였습니다
- 내 인턴십 탭에서 신청한 목록을 확인하여, 원하는 커뮤니티 <button>을 클릭하면 인턴십 소개, 참여자, 공지사항, 채팅, 일정을 확인할 수 있도록 구현하였습니다.

### 📝기업회원 - 지원자 관리

- 기업 회원으로 로그인하면 가장 먼저 지원자 관리 페이지로 이동하게 됩니다.
- 기업 회원이 올린 공고에 지원한 지원자에 대한 정보를 지원자의 이력서 번호를 기준으로 그룹을 묶어, 그룹 안에서 지원상태 번호가 가장 큰 값만 가져와 조회할 수 있는 쿼리문을 작성하여 Map형태로 받아 <Table>에 <tr>로 행을 만들어 내용을 조회할 수 있도록 구현하였습니다.
- tr을 클릭하는 경우 ajax를 통해 memId, jobPstgNo, rsmNo, emplClfcNo를 파라미터로 받아 해당 회원의 정보와 공고에 지원한 이력서 데이터를 model에 addAttribute해주었고, JSP로 이동하여 원하는 형태로 화면과 데이터를 구성한 뒤 해당 JSP 코드를 가져와 <div>에 html() 하도록 구현해주었습니다.
- 지원자의 이력서나 정보를 확인하고 Select Box에서 해당 지원자의 상태를 변경할 수 있도록 구현해주었습니다.
- 최종합격이나 불합격을 하는 경우 메일로 결과를 알려줄 수 있도록 <button>을 구현하였고, 클릭 시 confirm 후 원하는 메일을 지원자에게 전송할 수 있도록 하였습니다.

### 📝실시간 채팅

- 인턴십 참여자들끼리 소통할 수 있는 공간을 마련하고자 Websocket 기반의 실시간 단체 채팅을 구현하였습니다.
- servlet-context에서 /chatting 패턴으로 요청이 오는 경우  internshipChatHandler에서 요청을 처리할 수 있도록 <websocket:handlers>을 등록해주었습니다.
- internshipChatHandler에서는 TextWebSocketHandler을 상속 해주어 각각 연결, 종료, 메시지 전송을 위한 함수들을 오버라이드 해주었습니다.
- new SockJS로 소켓을 생성해주고, onMessage/onClose/onOpen 함수를 만들어 각 오버라이드 해준 메서드에 연결해주었습니다.
- 메시지 전송을 할 때 전송 당시 세션에 담겨있는 회원의 아이디와 메시지를 같이 보내주는 데, 받은 아이디와 현재 로그인 한 회원의 아이디가 일치하는 경우 오른쪽에, 그렇지 않은 경우 왼쪽에 <div>영역을 append 하여 채팅방 UI를 구현하였습니다.

### 📝챗봇

- 인턴십에 관하여 궁금한 사항이 있는 경우 챗봇을 통해 질문할 수 있도록 Websocket기반의 실시간 챗봇을 구현하였습니다.
- secretKey와 apiUrl를 입력하고 HttpURLConnection을 통해 api 서버와 POST방식으로 통신하여 받아온 데이터 값을 설정해주었습니다.
- 메시지를 보내는 경우 getReqMessage 메서드에서 네이버 챗봇에서 요구하는 포맷으로 변경해주도록 JSONObject 객체를 선언하여 데이터를 put 해주었습니다.
- 메시지를 보낼 때 encodeBase64String 함수를 통해 보낼 메세지를 네이버에서 제공해준 암호화로 변경해주었습니다

### 📝커뮤니티

**1) 커뮤니티 메인 화면**

- 등록해놓은 게시글들이 **JSTL**의 <c: forEach>을 통해 <div>로 나열되어 있고, 안에 <input type=“hidden”> 태그를 넣은 다음 value 속성값으로 ModelAttribute로 미리 초기화할 때 조회한 게시판 번호(boardNo) 데이터를 가져와 해당 게시판의 게시물만 조회하도록 구현하였다.
- 작성자의 이름, 직업, 연차, 작성일을 각 테이블 Left outer 조인을 통해 데이터를 가져와 <span>태그를 사용해 한 <div>영역 안에 상단에 구현하였다.

**2) 게시 글 상세보기**

- 해당 게시글 번호를 기준으로 이전글과 다음글이 존재한다면 해당 정보도 가져올 수 있도록 쿼리문을 작성하여 상세페이지 내에서 이전글과 다음글의 제목도 확인하고 해당 페이지로 이동할 수 있도록 구현하였다.
- 클릭 이벤트를 통해 상세보기 페이지로 넘어간다. 글 내용과 함께 댓글이 존재하는 경우 댓글의 내용, 댓글이 존재하지 않는 경우 ‘첫 댓글을 입력해보세요!’ 라는 문구가 생성된다.
- 현재 게시글 이전 게시글과 다음 게시글의 제목을 확인하고 해당 글 상세보기로 이동할 수 있다.
- 게시글의 작성자가 본인일 경우 수정, 삭제할 수 있는 버튼이 나올 수 있도록 구현하였다.
- 댓글의 내용을 입력하지 않고 등록하려고 하는 경우 ‘내용을 입력해주세요.’라는 경고 멘트를 보여줄 수 있도록 구현하였다.
- 댓글의 작성자가 본인일 경우 수정, 삭제할 수 있는 버튼이 나올 수 있도록 구현하였다.

**3) 게시글 등록**

- 게시글의 제목을 입력하지 않고 등록하려고 하는 경우 ‘게시글 제목을 입력해주세요.’라는 경고 멘트를 보여줄 수 있도록 구현하였다.
- 게시글의 내용을 입력하지 않고 등록하려고 하는 경우 ‘게시글 내용을 입력해주세요.’라는 경고 멘트를 보여줄 수 있도록 구현하였다.
- 게시글의 textarea는 **ckEditor**를 통해 게시글에서 사진을 업로드가 가능하도록 구현하였으며, 기본키인 poNo는 시퀀스로 만들어줘서 <selectKey>를 활용하였다.
- 파일을 첨부하고 업로드 및 다운로드가 가능하게 구현하였다.

**4) 게시글 수정**

- 게시글 기본키인 boardNo를 키 값으로 하여 게시글의 정보를 미리 조회해온 뒤, model에 addAttribute하여 페이지 내 value 값으로 기존의 제목, 내용 등을 불러와 수정할 수 있도록 구현하였다.
- 첨부파일이 등록된 게시글의 경우 ModelAttribute로 미리 초기화할 때 조회한 첨부파일목록(boardAttVOList) 데이터를 가져와 해당 게시글 수정페이지로 이동시 첨부파일 이름들을 조회하도록 구현하였다.
- 첨부파일을 삭제하고자 하는 경우에는 <a> 태그로 넣어둔 삭제 버튼을 클릭하면 삭제할 수 있도록 구현하였다.

**5) 게시글 삭제**

- 게시글 기본키인 boardNo를 키 값으로 하여 게시글의 정보를 미리 조회해온 뒤, model에 addAttribute하여 게시글의 작성자와 현재 로그인한 회원의 ID가 같으면 게시글을 삭제 할 수 있도록 구현하였다.
- 해당 게시글이 삭제되면 해당 게시글 번호를 부모로 하여 데이터를 구성하던 자식 데이터들도 ON DELETE CASCADE를 통해 삭제될 수 있도록 구현하였다.

### 📝인턴십 커뮤니티

- 모든 조회 및 검색기능을 **ajax**를 통한 **비동기**로 구현하였다.
- tr 클릭을 통해 상세보기 페이지로 넘어간다.
- 또한, 게시글의 작성자가 본인일 경우 수정, 삭제할 수 있는 버튼이 나온다.
- 글을 등록, 수정, 삭제할 수 있는 컨트롤러는 @ResponseBody와 @Controller의 기능을 합친 **@RestController**를 사용하였다.
- 게시글을 수정하는 경우 기본키인 boardNo를 키 값으로 하여 게시글의 정보를 미리 조회해온 뒤, model에 addAttribute하여 페이지 내 value 값으로 기존의 제목, 내용 등을 불러와 수정할 수 있도록 구현하였다.
- 게시글을 삭제하는 경우 기본키인 boardNo를 키 값으로 하여 게시글의 정보를 미리 조회해온 뒤, model에 addAttribute하여 게시글의 작성자와 현재 로그인한 회원의 ID가 같으면 게시글을 삭제 할 수 있도록 구현하였다.

### 📝파일 업로드 및 다운로드

**1) 파일 업로드**

- 파일 업로드는 일반회원의 프로필사진, 기업회원의 회사 대표 및 로고사진, 커뮤니티 이미지 및 파일 등록, 프리미엄 강의이미지 등 사이트 전반적인 기능들에서 사용하기 때문에 모듈화하여 모든 팀원이 간편하게 사용할 수 있도록 구현하였습니다.
- attachInsert(MultipartFile[] uploadFile, T tvo) 형태로 파일과 해당 기능을 사용하는 곳의 VO를 함께 파라미터로 받아 해당 VO의 instanceof를 판별하여 기본키값을 가져와 etpId에 set 할 수 있도록 구현하였습니다.
- 파일 이름이 중복되는 경우를 피하기 위하여 randomUUID().toString()를 통해 기존 파일 이름 앞에 랜덤 문자열을 붙여주었고, SimpleDateFormat으로 현재 날짜에 해당하는 폴더를 만들어 해당 폴더에 업로드 할 수 있도록 구현하였습니다.

**2) 파일 다운로드**

- 파일 이름을 파라미터 값으로 받아, 정해진 경로에 존재하는 파일을 찾아 Resource객체 생성 후, HttpHeaders에 해당 정보를 담아 ResponseEntity 객체를 생성해 사용자의 요청에 파일 정보를 전달할 수 있도록 구현하였습니다.
