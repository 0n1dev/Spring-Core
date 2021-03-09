# 스프링 핵심 원리
---

> [김영한님 인프런](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8)

# 스프링이란?
---

- **스프링 프레임워크**
    - 핵심 기술 : 스프링 DI 컨테이너, AOP 등
    - 웹 기술 : 스프링 MVC, 스프링 WebFlux
    - 데이터 접근 기술 : 트랜잭션, JDBC, ORM 지원, XML 지원
    - 기술 통합
    - 테스트
    - 언어
- **스프링 부트**
    - 스프링을 편리하게 사용할 수 있도록 지원, 최근에는 기본으로 사용
    - 단독으로 실행 가능한 스프링 애플리케이션을 쉽게 생성
    - 웹 서버를 내장해서 별도의 웹 서버 설치가 필요 없음
    - 손쉬운 빌드 구성을 위한 stater 종속성 제공
    - 3rd parth 라이브러리 자동 구성
    - 메트릭, 상태 확인, 외부 구성 같은 프로덕션 준비 기능 제공
    - 관례에 의한 간결한 설정
- 스프링 데이터
- 스프링 세션
- 스프링 시큐리티
- 스프링 Rest Docs
- 스프링 배치
- 스프링 클라우드

##  스프링의 핵심
---

- 객체 지향 언어가 가진 강력한 특징을 살려내는 프레임워크
- 좋은 객체 지향 애플리케이션을 개발할 수 있게 도와주는 프레임워크

# 좋은 객체 지향 프로그래밍이란?
---

- 추상화
- 캡슐화
- 상속
- 다형성

-> 객체 지향 프로그래밍은 프로그램을 유연하고 변경이 용이하게 만들기 때문에 대규모 소프트웨어 개발에 많이 사용

## 유연하고, 변경이 용이?
---

- 레고 블럭 조립하듯
- 컴포넌트를 쉽고 유연하게 변경하면서 개발할 수 있는 방법

-> 다형성

### 다형성(Polymorphism)
---

> 역할과 구현으로 구분하면 세상이 단순해지고, 유연해지며 변경도 편리해진다.

**장점**

- 클라이언트는 대상의 역할(인터페이스)만 알면 된다.
- 클라이언트는 구현 대상의 내부 구조를 몰라도 된다.
- 클라이언트는 구현 대상의 내부 구조가 변경 되어도 영향을 받지 않는다.
- 클라이언트는 구현 대상 자체를 변경해도 영향을 받지 않는다.

### 자바에서 다형성
---

- 역할 -> 인터페이스
- 구현 -> 인터페이스를 구현한 클래스, 구현 객체

> 다형성으로 인터페이스를 구현한 객체를 실행 시점에 유연하게 변경할 수 있다.

### 스프링과 객체 지향
---

- 다형성이 중요
- 스프링은 다형성을 극대화해서 이용할 수 있게 도와줌
- 제어의 역전(IoC), 의존관계 주입(DI)은 다형성을 활용해서 역할과 구현을 편리하게 다룰 수 있도록 지원

# 좋은 객체 지향 설계의 5가지 원칙 (SOLID)
---

- SRP : 단일 책임 원칙 (Single Responsiblility Principle)
    - 한 클래스는 하나의 책임만 가져야 한다.
    - **중요한 기준은 변경**
        - 변경이 있을 때 파급 효과가 적으면 단일 책임 원칙을 잘 따른 것
- OCP : 개방-폐쇄 원칙 (Open/Closed Principle)
    - 소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.
    - 다형성
    - 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능을 구현
    - 역할과 구현의 분리
- LSP : 리스코프 치환 원칙 (Liskov Substitution Principle)
    - 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.
    - 다형성에서 하위 클래스는 인터페이스 규약을 다 지켜야 한다는 것
    - ex) 냉장고라는 인터페이스의 기능을 온도 뜨겁게로 구현하면 LSP 위반
- ISP : 인터페이스 분리 원칙 (Interface Segregation Principle)
    - 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.
    - ex) 자동차 인터페이스 분리
        - 운전 인터페이스
        - 정비 인터페이스 분리
    - 인터페이스가 병확해지고, 대체 가능성이 높아진다.
- DIP : 의존관계 역전 원칙 (Dependency Inversion Principle)
    - 프로그래머는 "추상화에 의존해야지, 구체화에 의존하면 안된다."
    - 구현 클래스에 의존하지 말고, 인터페이스에 의존하라는 뜻
    - 역할(Role)에 의존하게 해야 한다는 것과 같다.

> 다형성만으로는 OCP, DIP 원칙을 지킬수 없음

# 객체 지향 설계와 스프링
---

- 스프링은 다음 기술로 다형성 + OCP, DIP를 가능하게 지원
    - DI(Dependency Injection) : 의존관계, 의존성 주입
    - DI 컨테이너 제공
- 클라이언트 코드의 변경 없이 기능 확장

# 스프링 핵심 원리 이해1 - 예제 만들기
---

## 비즈니스 요구사항과 설계
---

- 회원
    - 회원을 가입하고, 조회할 수 있다.
    - 회원은 일반과 VIP 두 가지 등급이 있다.
    - 회원 데이터는 자체 DB를 구축할 수 있고, 외부 시스템과 연동할 수 있다. (인터페이스 필요 할듯?)
- 주문과 할인 정책
    - 회원은 상품을 주문할 수 있다.
    - 회원 등급에 따라 할인 정책을 적용할 수 있다.
    - 할인 정책은 변경 가능성이 높다. 회사의 기본 할인 정책을 아직 정하지 못했고, 오픈 직전까지 고민을 미루고 싶다. 최악의 경우 할인을 적용하지 않을 수 도 있다.

-> 지금은 스프링 없이 순수한 자바로만 개발을 목표로 잡는다.

![현재 프로젝트 모습](./img/purejava.png)

# 스프링 핵심 원리 이해2 - 객체 지향 원리 적용
---

## 새로운 할인 정책 개발
---

### 기존 코드의 문제점
---

> 할인 정책을 변경하려면 클라이언트인 `OrderServiceImpl`의 코드를 수정해야 한다. (개방-폐쇄 원칙 벗어남)

```java
public class OrderServiceImpl implements OrderService {

    private final MemberRepository memberRepository = new MemoryMemberRepository();
//    private final DiscountPolicy discountPolicy = new FixDiscountPolicy();
    private final DiscountPolicy discountPolicy = new RateDiscountPolicy();

}
```

- 우리는 역할과 구현을 충실하게 분리했다. -> O
- 다형성도 활용하고, 인터페이스와 구현 객체를 분리했다. -> O
- OCP, DIP 같은 객체지향 설계 원칙을 충실히 준수했다.
    - 그렇게 보이지만 아니다.
    - DIP : 추상 인터페이스와 구현 클래스 모두 의존하고 있다. -> 위반하고 있다.
    - OCP : DIP를 위반하기 때문에 FixDiscountPolicy에서 RateDiscountPolicy로 바뀌는 순간 OrderServiceImpl의 코드도 변경해야된다. -> 위반하고 있다.

### 문제점 해결 방법 - 1
---

```java
public class OrderServiceImpl implements OrderService {

    private final MemberRepository memberRepository = new MemoryMemberRepository();
//    private final DiscountPolicy discountPolicy = new FixDiscountPolicy();
//    private final DiscountPolicy discountPolicy = new RateDiscountPolicy();

    private DiscountPolicy discountPolicy;

}
```

> DIP는 지켰지만 구현 클래스가 없어서 동작하지 않음.

누군가 클라이언트인 `OrderServiceImpl`에 DiscountPolicy의 구현 객체를 대신 생성하고 주입해야 된다.

### 문제점 해결방법 - 2 (관심사의 분리)
---

AppConfig 클래스를 만들어 생성자를 통해 주입.

```java
package hello.core;

import hello.core.discount.FixDiscountPolicy;
import hello.core.member.MemberService;
import hello.core.member.MemberServiceImpl;
import hello.core.member.MemoryMemberRepository;
import hello.core.order.OrderService;
import hello.core.order.OrderServiceImpl;

public class AppConfig {

    public MemberService memberService() {
        return new MemberServiceImpl(new MemoryMemberRepository());
    }

    public OrderService orderService() {
        return new OrderServiceImpl(new MemoryMemberRepository(), new FixDiscountPolicy());
    }
}
```

- AppConfig는 애플리케이션의 실제 동작에 필요한 **구현 객체를 생성** 해준다.
- AppConfig는 생성한 객체 인스턴스의 참조(레퍼런스)를 **생성자를 통해서 주입** 해준다.

#### 리팩터링
---

```java
package hello.core;

import hello.core.discount.DiscountPolicy;
import hello.core.discount.FixDiscountPolicy;
import hello.core.member.MemberService;
import hello.core.member.MemberServiceImpl;
import hello.core.member.MemoryMemberRepository;
import hello.core.order.OrderService;
import hello.core.order.OrderServiceImpl;

public class AppConfig {

    public MemberService memberService() {
        return new MemberServiceImpl(memberRepository());
    }

    private MemoryMemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }

    public OrderService orderService() {
        return new OrderServiceImpl(memberRepository(), discountPolicy());
    }
    
    public DiscountPolicy discountPolicy() {
        return new FixDiscountPolicy();
    }
}
```

- 중복으로 사용하는 부분을 변경
- 역할에 따른 구현이 잘보임

