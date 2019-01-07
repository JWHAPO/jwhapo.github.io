---
layout: post
title: Spring boot Test MockMvc
---

### MockMvc 란?  
*MVC의 Controller 부분을 테스트할 수 있는 라이브러리.*  
*웹 애플리케이션을 서버에 배포하지 않고 요청,응답등의 스프링 MVC의 동작을 테스트할 수 있다.*  

### 의존성 추가  
보통 spring boot로 프로젝트를 생성하면 spring-boot-starter-test가 기본적으로 추가되어있을 것이다.  
없다면 추가!.  
gradle입니다.  

*testImplementation('org.springframework.boot:spring-boot-starter-test')*   

### 테스트 코드 #1  

```java  
@RunWith(SpringRunner.class)
@WebMvcTest(CarController.class)
public class CarControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean
    CarService carService;

    @Test
    public void findAllTest() throws Exception{

        Car car = new Car(1L,1L,"newCar1", 2210L,"kg","KIA","1"); // 테스트할 Car 객체 생성

        List<Car> allCars = Collections.singletonList(car);
        given(carService.findAll()).willReturn(allCars);

        mockMvc.perform(get("/cars").contentType(MediaType.APPLICATION_JSON))
                .andExpect(status().isOk())  //응답 상태코드가 200 (HttpStatus.OK)이 아니면 에러!
                .andExpect(jsonPath("$", hasSize(1))) //json 결과 사이즈가 1개가 아니면 에러!!( 위에 Car 객체에 1개만 넣었음..)
                .andExpect(jsonPath("$[0].no",is(car.getNo().intValue())));
    }
}
~~~   

### 테스트 코드 #2

~~~   
@Test
    public void findByEmailAndPasswordTest() throws Exception{
        User user = new User(1L,"kjw@test.com","123","Mr.KKK","Seoul","2");
        given(userService.findByEmailAndPassword("kjw@naver.com","123")).willReturn(user);

        mockMvc.perform(get("/users/kjw@test.com/123").contentType(MediaType.APPLICATION_JSON))
                .andExpect(status().isOk())
                .andExpect(jsonPath("name",is(user.getName())));

    }

~~~  
