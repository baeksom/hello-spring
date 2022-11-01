# hello-spring
--------------------------------------------------------------------------------------------------
섹션 2 \
정적 컨텐츠
서버에서 하는 것 없이 파일을 그대로 웹 브라우저에 내려줌
프로그램x 정적파일이 그대로 받아드림

내장 톰캣 서버가 요청을 받음 - 스프링에게 요청 넘김 - 스프링 컨테이너의 컨트롤러에서 찾음(컨트롤러에게 우선순위) -
내부에서 찾음

mvc(model, view, controller) & 템플릿 엔진
템플릿 엔진 : 서버에서 프로그래밍 변환해서 동적으로 바꿔 내리는 것
view - 화면에 관련된 일
controller - 비즈니스 로직, 서버 관련

템플릿 엔진을 controller로 쪼개서 view를 템플릿 엔진으로 html을 쪼개서 프로그래밍 한 것을 랜더링하여 
랜더링이 된 html을 고객에게 전달
서버에서 변형을 해서 내려주는 방식

API
서버끼리 통신할때 객체를 반환
HttpMessageConver를 이용해 Json스타일로 바꿔서 view없이 반환

@responsebody
http에서 응답 바디부에 데이터를 직접 넣어줌
HttpMessageConverter 동작
- StringConverter : String 일 때 동작
- JsonConverter : 객체일 때 동작
--------------------------------------------------------------------------------------------------
섹션 3 \
비즈니스 요구사항 정리

웹 애플리케이션 계층 구조
컨트롤러 : 웹 MVC 컨트롤러 역할
서비스 : 핵심 비즈니스 로직 구현
리포지토리 : DB 접근, 도메인 객체를 DB에 저장하고 관리
도메인 : 비즈니스 도메인 객체 예> 회원, 주문, 쿠폰 등 DB에 저장되고 관리됨

MemberService - 회원 비즈니스 로직 
MemberRepository - 회원 저장 (인터페이스로 설계)

domain 패키지 - member 클래스에 id와 식별자 - getter & setter 
시스템이 저장하는 아이디

회원 respository 인터페이스
 - 회원 객체 저장소 

테스트 주도 개발 (tdd)
: 테스트 틀을 먼저 만들고 그에 맞춰 구현 클래스를 개발함 

--------------------------------------------------------------------------------------------------
섹션 4 \
스프링 빈을 등록하는 2가지 방법
- 컴포넌트 스캔과 자동 의존관계 설정
- 자바 코드로 직접 스프링 빈 등록하기


-컴포넌트 스캔과 자동 의존관계 설정
@Controller 이노테이션
자동으로 생성을 해서 관리함
외부 요청 받음
@Autowired
스프링 컨테이너에서 멤버 서비스를 가져옴
멤버 컨트롤러가 생성될 때 스프링빈에 등록되어있는 멤버서비스 객체를 가져다 넣어줌
의존관계를 주입해줌, 연결을 해줌
@Service
스프링 컨테이너에 MemberService를 등록해줌
비즈니스 로직 만듦
@Repository
데이터 저장

-자바 코드로 직접 스프링 빈 등록하기
여기서는 향후 메모리 리포지토리를 다른 리포지토리로 변경할 예정이므로, 컴포넌트 스캔 방식 대신에 자바 코드로 스프링 빈을 설정하였다

--------------------------------------------------------------------------------------------------
섹션 5 \
요청이 오면 스프링 컨테이너 안의 관련 컨트롤러가 있는지 찾고 없으면 static파일을 찾음

요청이 오면 controller에서 찾음
매핑된게 있어서 controller 호출

회원 가입
members/new로 들어감
get방식으로 들어가서 createForm() 매핑
members/createMemberForm 이동 -> 화면에 뿌려짐
값을 받아 mbers/new에 post방식으로 넘어감 PostMapping("/members/new") create()
setName을 호출해 member의 name에 값이 들어감

회원 조회
타임리프
$ 모델 안에 컨트롤러에서 꺼냄
getter을 통해 값을 꺼내줌
