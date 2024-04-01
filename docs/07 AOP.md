## AOP가 필요한 상황

- 모든 메서드의 호출 시간을 측정하고 싶다면?
    - 이제 상사가 와서 모든 메서드의 호출시간을 알고 싶어함. 나는 큰일났다. AOP를 모르는 나는 다 바꿔야되는 상황 발생
- 공통 관심 사항(cross-cutting concern) vs 핵심 관심 사항(core concern)
- 회원 가입 시간, 회원 조회 시간을 측정하고 싶다면?

#### 문제

- 회원 가입, 회원 조회에 시간을 측정하는 기능은 핵심 관심 사항이 아니다.
- 시간을 측정하는 로직은 공통 관심 사항이다.
- 시간을 측정하는 로직과 핵심 비즈니스 로직이 섞여서 유지보수가 어렵다.
- 시간을 측정하는 로직을 별도의 공통 로직으로 만들기 매우 어렵다.
- 시간을 측정하는 로직을 변경할 때 모든 로직을 찾아가면서 변경해야 한다.

## AOP 적용

- AOP: Aspect Oriented Programming
- 공통 관심 사항(cross-cutting concern) vs 핵심 관심 사항(core concern) **분리**

![image](https://github.com/muyaaho/spring-start/assets/76798969/b7e845f6-ddfa-442c-8a39-45fbac1fd7b7)

#### 시간 측정 AOP 등록

```java
@Aspect
@Component
public class TimeTraceAop {

    @Around("execution(* hello.hellospring..*(..))")
    public Object execute(ProceedingJoinPoint joinPoint) throws Throwable {
        long start = System.currentTimeMillis();
        System.out.println("START: " + joinPoint.toString());
        try {
            return joinPoint.proceed();
        } finally {
            long finish = System.currentTimeMillis();
            long timeMs = finish - start;
            System.out.println("END: " + joinPoint.toString() + " " + timeMs + "ms");
        }
    }
}
```

- `@Component`: 컴포넌트 스캔, Spring bean에 등록한다.
- `hello.hellospring..*(..))`: hello.hellospring 하위에 다 적용하겠다.

#### 해결

- 회원 가입, 회원 조회 등 핵심 관심사항과 시간을 측정하는 공통 관심사항을 분리한다.
- 시간을 측정하는 로직을 별도의 공동 로직으로 만들었다.
- 핵심 관심 사항을 깔끔하게 유지할 수 있다.
- 변경이 필요하면 이 로직만 변경하면 된다.
- 원하는 적용 대상을 선택할 수 있다.

### 스프링의 AOP 동작 방식 설명

![image](https://github.com/muyaaho/spring-start/assets/76798969/cf90494c-4e26-4210-8222-c4dd776af156)

- Controller에서 프록시로 실행된다. 프록시는 가짜 memberService다.
- 그 다음 `joinPoint.proceed()`가 실행 되고 실제 memberService가 실행된다.
- Controller에서 생성자를 print 해보면 `~~ memberService$$EnhancerBySpringCGLIB~` 가 실행된다.
    - CGLIB: CG라이브러리, 현재 memberService 가지고 코드를 복제해서 조작하는 기술이다.
- DI를 알아서 해주므로 만들어진 만들어진 프록시가 주입될 수 있다.
- 이와 같은 방식은 프록시 방식 AOP라고 한다.
