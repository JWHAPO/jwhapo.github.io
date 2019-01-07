---
layout: post
title: Spring boot Test MockMvc 
---

### MockMvc 란?  
*MVC의 Controller 부분을 테스트할 수 있는 라이브러리.*  
*웹 애플리케이션을 서버에 빼포하지 않고 스프링 MVC의 동작을 테스트할 수 있다.*  

### 의존성 추가  
보통 spring boot로 프로젝트를 생성하면 spring-boot-starter-test가 기본적으로 추가되어있을 것이다.  
없다면 추가!.  
*testImplementation('org.springframework.boot:spring-boot-starter-test')*  

### 테스트 코드

------------
@RunWith(SpringRunner.class)
@WebMvcTest(CarController.class)
@AutoConfigureRestDocs(outputDir = "target/snippets")
public class CarControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean
    CarService carService;


    @Test
    public void findAllTest() throws Exception{

        Car car = new Car(1L,1L,"newCar1", 2210L,"kg","KIA","1");

        List<Car> allCars = Collections.singletonList(car);
        given(carService.findAll()).willReturn(allCars);

        mockMvc.perform(get("/cars").contentType(MediaType.APPLICATION_JSON)).andExpect(status().isOk())
                .andExpect(jsonPath("$", hasSize(1)))
                .andExpect(jsonPath("$[0].no",is(car.getNo().intValue())))
                .andDo(document("cars/findAll"));
    }
}
------------------
