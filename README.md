# hello-spring

섹션 4
스프링 빈을 등록하는 2가지 방법
-컴포넌트 스캔과 자동 의존관계 설정
-자바 코드로 직접 스프링 빈 등록하기


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

섹션 5
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
