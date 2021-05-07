### 서블릿 컨테이너: 서블릿의 생성주기에 대한 모든 권한을 개발자가 아니라 컨테이너가 가짐.(IoC)   
### 스프링 IoC 컨테이너: Object의 모든 작업 담당 . Object에 대한 제어권 가짐 .Application Context 인터페이스를 구현한 클래스의 오브젝트
```AbstractApplicationContext context=new GenericXmlApplicationContext("classpath:com/anno/user8/applicationContext.xml");```
#### 프로퍼티 파일 내용 읽어오기: 
프로퍼티:   
join.name=\uC774\uD604\uC9C0   
join.tel=010-1111-1111   
join.age=24   

프로퍼티 파일 읽어오기 :   	
<context:property-placeholder location="classpath:com/prop/user.properties"/>   
프로퍼티파일의 값으로 설정 :
```
<bean id="userService" class="com.prop.UserServiceImpl">   
<property name="name" value="${join.name}"/>   
<property name="tel" value="${join.tel}"/>   
<property name="age" value="${join.age}"/>   
</bean>	   
```

+ 객체 의존성 : new CLASS() 하면 CLASS 객체에 의존성을 가짐 -> **tight coupling**
+ 문제점:    
  + 하나의 모듈이 바뀌면 의존한 다른 모듈까지 변경.    
  + Unit Test 작성이 어려워짐  
  + 해결법-> DI : 객체 자체가 아니라 FrameWork에 의해 객체의 의존성이 주입되게    
+ DI(의존성 주입):  **스프링 프레임워크에서 지원하는 IoC의 형태**
  + 각 클래스간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결   
  + Framework에 의해 동적으로 주입돼서 모듈간 결합도 낮아지고 유연성 높아지고 객체간 의존성 줄임
  + 코드 재사용성 높이고 가독성 높아짐 .  
  + Constructor Injection   
  + Setter Injection   
  + Field Injection
+ Spring Bean: 스프링 빈 컨테이너에 존재하는 객체. 빈 컨테이너가 의존성 주입으로 빈 객체 사용하게 해줌 .
  + XML기반
    + Constructor Injection   
      + 기본 생성자를 이용한 빈 정의    
	     ```<bean id="userService" class="com.user1.UserServiceImpl"/>```   
      + 인자 있는 생성자 이용 빈 정의      
       ```
          <bean id="userService2" class="com.user1.UserServiceImpl2">
		      <constructor-arg index="0" value="스프링"/>	
		      <constructor-arg index="2" value="17"/>	
		      <constructor-arg index="1" value="010-1111-2222"/>	
	        </bean>
        ```
      + value가 객체라면 ref사용
        ``` 
          <bean id="user" class="com.user1.User">
		      <constructor-arg ref="userService2"/>
	        </bean>
        ```
      + c 네임 스페이스
        ``` 
          <bean id="userService" class="com.user2.UserServiceImpl2" c:name="가나다"
		      c:tel="010-2222-3333" c:age="20" />
         <bean id="user" class="com.user2.User"
		      c:userService-ref="userService" init-method="init"
		      destroy-method="destroy" />
        ```  
    + Setter Injection 
      + 문자열 또는 기본 자료형일때   
      ```
        <bean id="userService" class="com.user3.UserServiceImpl">
	      <property name="name" value="너자바"/>
	      <property name="tel" value="010-7777-8888"/>
	      <property name="age" value="21"/>
        </bean>
      ```   
      + 객체일때   
      ```
       <bean id="user" class="com.user3.User">
 	      <property name="userService" ref="userService" />
       </bean>
      ```
      + p 네임스페이스   
      ```
      <bean id="userService" class="com.user4.UserServiceImpl" p:name="가나다"
		  p:tel="010-2222-3333" p:age="20" />
      <bean id="user" class="com.user4.User"
		  p:userService-ref="userService"/>
      ```
      + 컬렉션 타입   
        + 맵
        ```
        <property name="address"><!-- map에 의존성주입 -->
			  <map>
				<entry key="서블릿" value="서울"/><!-- <entry key="아름" value-ref="객체2"/> -->
				<entry>
					<key><value>스프링</value></key>
					<value>경기</value><!-- <ref bean="객체"/> -->
				</entry>
			  </map>
		    </property>
        ```
        + 리스트   
        ```
        <property name="hobby">
			  <list>
				<value>게임</value><!-- <ref bean="객체"/> 즉 value가 객체인 경우는 ref-->
				<value>영화</value>
				<value>음악</value>
				<value>운동</value>
			  </list>
		    </property>
        ```
        + 프로퍼티   
        ```
        <property name="tels">
			  <props><!-- 프로퍼티는 키와 값이 모두 String만 가능 -->
				<prop key="하하하">010-1111-1111</prop>
				<prop key="머머머">010-2222-2222</prop>
				<prop key="고고고">010-3333-3333</prop>
			  </props>
		    </property>
        ```
        
          
    
    + 자동  주입   
    	``` <bean id="user" class="com.user6.User" autowire="byType"/> ```
    	+ 의존 관계 자동설정 (이 방법은 스프링 5.1부터 deprecated 됨)  
		byName: 프로퍼티와 동일한 이름을 갖는 빈을 주입(setter injection)   
		byType: 프로퍼티와 동일한 타입을 갖는 빈을 주입(setter injection). 동일한 타입이 하나인 경우만 가능   
		constructor:생성자를 이용하여 타입이 일치한 빈을 찾아 주입       
	     
	 
    + Lookup Method Injection(컨네이너가 관리하는 빈의 메소드를 재정의하여 컨테이너안의 다른 빈을 검색하는 기능 )    
    ```
    <bean id="pizzaShop" class="com.look.PizzaShop">
		<lookup-method name="makePizza" bean="pizza"/><!-- pizza객체를 리턴 -->
		<lookup-method name="makeVeggiePizza" bean="veggiePizza"/><!-- veggiePizza객체를 리턴 -->
    </bean>
     ```
    
  + Annotation기반
 	+ @Autowired, @Resource 등 애노테이션 활성화 -> 	<context:annotation-config/>
 	+ 모든 어노테이션 활성화 -> <context:component-scan base-package="com.anno.user6"/>
 	+ service만 스캔->    
 	```
		<context:component-scan base-package="com.anno.user7" use-default-filters="false">
	 	<context:include-filter type="annotation" expression="org.springframework.stereotype.Service"/>
	 	</context:component-scan>
	```	
  	+ @Autowired 를 붙이기(필드, setter, 생성자) : 타입을 이용
  	+ 동일 타입이 둘 이상이면 동일 이름 빈을 주입 . 동일 이름이 없으면 예외  
  	+ @Qualifier("이름") @Autowired+@Qualifier=>타입+이름
  	***
  	+ @Resource(name="name 속성 안써도되고 써도되고") : 자바제공 어노테이션
  	+ JDK 9이상부터 @Resource, @PostConstruct, @PreDestroy는 deprecated 됨->해결방법: javax.annotation을 의존성 주입(메이븐)
  	``` 
		<dependency> 
	 		<groupId>javax.annotation</groupId>
	 		<artifactId>javax.annotation-api</artifactId> 
	 		<version>1.3.2</version>
	  	</dependency>
	```
	***
	+ @Inject 자바 제공. 타입으로 의존성 주입. 동일한 타입이 둘 이상이면 동일한 이름으로 의존성 주입
	+ @Inject와 @Named("userService2")로 같이 씀 
	***
	+ @Value("자바"): 파라미터에 값 설정
  		 
  + 자바 기반   
