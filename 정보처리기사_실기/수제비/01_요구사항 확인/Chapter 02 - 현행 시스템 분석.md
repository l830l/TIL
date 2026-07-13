# 현행 시스템 파악
## 개념
- 현행 시스템이 어떤 하위 시스템으로 구성되어 있고, 제공 기능 및 연계 정보는 무엇이며 어떤 기술 요소를 사용하는지를 파악하는 활동
- 사용하고 있는 소프트웨어 및 하드웨어는 무엇인지, 네트워크는 어떻게 되어있는지 파악하는 활동

## 절차
### 1단계 : 구성/기능/인터페이스 파악
- 시스템 구성 현황 파악
- 시스템 기능 파악
- 시스템 인터페이스 현황 파악

### 2단계 : 아키텍처 및 소프트웨어 구성 파악
- 아키텍처 파악
- 소프트웨어 구성 파악

### 3단계 : 하드웨어 및 네트워크 구성 파악
- 시스템 하드웨어 현황 파악
- 네트워크 구성 파악

## 소프트웨어 아키텍처 (Software Architecture)
### 개념
- 여러가지 소프트웨어 구성요소와 그 구성요소가 가진 특성 중에서 외부에 드러나는 특성, 그리고 구성요소 간의 관계를 표현하는 시스템의 구조나 구조체이다.

### 소프트웨어 아키텍처 프레임워크 개념
- 소프트웨어 집약적인 시스템에서 아키텍처가 표현해야 하는 내용 및 이들 간의 관계를 제공하는 아키텍처 기술 표준

### 소프트웨어 아키텍처 4+1 뷰
#### 개념
- 고객의 요구사항을 정리해 놓은 시나리오를 4개의 관점에서 바라보는 소프트웨어적인 접근 방법
- 4개의 분리된 구조로 구성되는 아키텍처 개념을 제시하고, 이들 4개의 뷰가 서로 충돌되지 않는지, 시스템 요구사항을 충족시키는지를 증명하기 위해 체크 방법으로 유스케이스를 사용한다

#### 구성요소
![[Frame 13.png|447]]
##### 유스케이스 뷰(Usecase View)
- 유스케이스 또는 아키텍처를 도출하고 설계하여 다른 뷰를 검증하는 데 사용되는 뷰
- 외부 행위자에 의해 인식되는 시스템의 기능 요구사항을 보여주는 데 초점
- 사용자, 설계자, 개발자, 테스트 관점

##### 논리 뷰(Logical View)
- 시스템의 기능적인 요구사항이 어떻게 제공되는지 설명해주는 뷰
- 설계자, 개발자 관점

##### 프로세스 뷰(Process View)
- 시스템의 비기능적인 속성으로서 자원의 효율적인 사용, 병행 실행, 비동기, 이벤트 처리 등을 표현한 뷰
- 개발자, 시스템 통합자 관점

##### 구현 뷰(Implementation View)
- 개발 환경 안에서 정적인 소프트웨어 모듈의 구성을 보여주는 뷰
	- 정적이다는 뜻은 실행 중에 움직이는 흐름이 아니라 개발자가 만들어놓은 소프트웨어 조각들의 배치를 뜻한다.
- 컴포넌트 구조와 의존성을 보여주고 컴포넌트에 관한 부가적인 정보 정의
	- 컴포넌트 구조가 더 큰 개념이고 하위 요소가 보통 모듈이다.

##### 배포 뷰(Deployment View)
- 컴포넌트가 물리적인 아키텍처에 어떻게 배치되는가를 매핑해서 보여주는 뷰
- 물리적 시스템을 구성하고 있는 각 부분들의 분 산 형태와 설치에 초점

### 소프트웨어 아키텍처 패턴
#### 개념
- 소프트웨어를 설계할 떄 참조할 수 있는 전형적인 해결 방식
- 소프트웨어 아키텍처에서 일반적으로 발생하는 문제점에 대한 일반화된 해결 방식이자 재사용이 가능한 솔루션

#### 유형
##### 계층화 패턴(Layered Pattern)
![[Frame 14.png|201]]
- 시스템을 계층(Layer)으로 구분하여 구성하는 패턴
- 각 하위 모듈들은 특정한 수준의 추상화를 제공하고, 각 계층은 다음 상위 계층에 서비스를 제공
- 서로 마주 보는 두 개의 계층 사이에서만 상호 작용이 이루어짐

##### 클라이언트-서버 패턴(Client-Server Pattern)
![[Frame 15.png|621]]
- 하나의 서버와 다수의 클라이언트로 구성된 패턴
- 사용자가 클라이언트를 통해서 서버에 서비스를 요청하면 서버는 클라이언트에게 서비스 제공
- 서버는 계속 클라이언트로부터 요청을 대기

##### 파이프-필터 패턴(Pipe-Filter Pattern)
- 데이터 스트림을 생성하고 처리하는 시스템에서 사용 가능한 단방향 채턴
- 서브 시스템이 입력 데이터를 받아 처리하고, 결과를 다음 서브 시스템으로 넘겨주는 과정을 반복
- 필터 컴포넌트는 재사용성이 좋고, 추가가 쉽기 때문에 확장이 용이하나, 필터 간 데이터 이동에서 데이터 변환 오버헤드가 발생    
![[Frame 16.png|221]]

##### 브로커 패턴(Broker Pattern)
![[Frame 17.png|558]]
- 분리된 컴포넌트들로 이루어진 분산 시스템에서 사용되고, 이 컴포넌트들은 원격 서비스 실행을 통해 상호 작용이 가능한 패턴
- 컴포넌트 간의 통신을 조정하는 역할 수행
- 서버는 자신의 기능들을 브로커에 넘겨주며, 클라이언트가 브로커에 서비스를 요청하면 브로커는 클라이언트를 자신의 레지스트리에 있는 적합한 서비스로 리다이렉션 함
	- 리다이렉션 : 사용자가 요청한 서비스를 다른 서비스로 자동적으로 이동시켜 주는 동작
	- 레지스트리 : 브로커가 가지고 있는 서비스 목록표 또는 주소록으로 어떤 서비스가 어디에 있는지 기록해둔 목록

##### 모델-뷰-컨트롤러 패턴(MVC: Model View Controller Pattern)
![[Frame 18.png|452]]
- 대화형 애플리케이션을 모델, 뷰 컨트롤러 3개의 서브 시스템으로 구조화하는 패턴
	- 모델(Model) : 핵심 기능과 데이터 보관 
	- 뷰(View) : 사용자에게 정보 표시(하나 이상의 뷰가 정의될 수 있음)
	- 컨트롤러(Controller) : 사용자로부터 요청을 입력받아 처리. 모델과 뷰 사이에서 전달자 역할을 수행

##### 마스터-슬레이브 패턴(Master-Slave Pattern)
![[Frame 19.png|581]]
- 연산, 통신, 조정을 책임지는 마스터와 제어되고 동기화 대상인 슬레이브로 구성되는 패턴
- 일반적으로 실시간 시스템에서 사용

### 소프트웨어 아키텍처 비용 평가모델
#### 개념
- 아키텍처 접근법이 품질 속성에 미치는 영향을 판단하고 아키텍처의 적합성을 평가하는 모델

#### 종류
![[Frame 20.png|709]]
##### SAAM(Software Architecture Analysis Method)
- 변경 용이성과 기능성에 집중
- 평가가 용이하여 경험이 없는 조직에서도 활용 가능한 비용 평가모델

##### ATAM(Architexture Trade-off Analysis Method)
- 아키텍처 품질 속성을 만족시키는지 판단 및 품질 속성들의 이해 상충관계까지 평가하는 모델
	- 아키텍처 품질 속성 : 특정 품질에 대한 요구 사항을 명세한 내역, 최적의 하키텍처를 선택하기 위한 핵심요소이다.

##### CBAM(Cost Benefit Analysis Method)
- ATAM 바탕의 시스템 아키텍처 분석 중심으로 경제적 의사결정에 대한 요구를 충족하는 비용 평가모델

##### ADR(Active Design Review)
- 소프트웨어 아키텍처 구성요소 간 응집도를 평가하는 모델

##### ARID(Active Reviews for Intermediate Design)
- 전체 아키텍처가 아닌 특정 부분에 대한  품질 요소에 집중하는 비용 평가 모델

## 디자인 패턴
### 개념
- 소프트웨어 공학의 소프트웨어 설계에서 공통으로 발생하는 문제에 대해 자주 쓰이는 설계 방법을 정리한 패턴
- 디자인 패턴을 참고하여 개발할 경우 개발의 효율성과 유지보수성, 운용성이 높아지며, 프로그램의 최적화에 도움이 된다

### 구성요소
#### 패턴의 이름
- 디자인 패턴을 부를 때 사용하는 이름과 디자인 패턴의 유형
#### 문제 및 배경
- 디자인 패턴이 사용되는 분야 또는 배경, 해결하는 문제
#### 솔루션
- 디자인 패턴을 이루는 요소들, 관계, 협동 과정
#### 사례
- 디자인 패턴의 간단한 적용 사례
#### 결과
- 디자인 패턴을 사용하면 얻게되는 이점이나 영향
#### 샘플 코드
- 디자인 패턴이 적용된 원시 코드
	- 원시 코드 : 프로그래머가 프로그래밍 언어를 사용해 컴퓨터 소프트웨어나 프로그램을 사람이 읽을 수 있는 텍스트 형태로 작성한 설계도

### 유형
#### 생성 패턴
- 객체 인스턴스 생성에 관여, 클래스 정의와 객체 생성 방식을 구조화, 캡슐화를 수행하는 패턴
#### 구조 패턴
- 더 큰 구조 형성 목적으로 클래스나 객체의 조합을 다루는 패턴
#### 행위 패턴
- 클래스나 객체들이 상호 작용하는 방법과 역할 분담을 다루는 패턴

### 종류
#### 생성 패턴
##### Builder
- 복잡한 인스턴스를 조립하여 만드는 구조로, 복합 객체를 생성할 때 객체를 생성하는 방법(과정)과 객체를 구현(표현)하는 방법을 분리함으로써 동일한 생성 절차에서 서로 다른 표현 결과를 만들 수 있는 디자인 패턴
	- 복합 객체 : 여러 값이나 다른 객체들이 조립되어 하나의 객체가되는 것
- 생성과 표기를 분리해서 복잡한 객체를 생성
``` java
Burger burger = builder
        .addBread()
        .addPatty()
        .addVegetable()
        .addSauce()
        .build();
```
- 여기서 생성과 표기를 분리해서 복잡한 객체를 생성한다는 뜻은 조립 과정은 비슷하지만, 최종 결과물의 표현은 새우버거, 치즈버거 등 달라질 수 있다는 뜻이다.
##### Prototype
- 처음부터 일반적인 원형을 만들어 놓고, 그것을 복사한 후 필요한 부분만 수정하여 사용하는 패턴
	- 여기서 말하는 일반적인 원형이란 기본 샘플 객체로 이미 만들어져있는 인스턴스를 뜻한다. 즉, 기본값이 들어있는 원본 객체를 복사한 뒤, 복사본의 일부 값만 수정하는 방식이다.
``` java
// 원형
User prototype = new User(  
	"기본 이름",  
	"default@email.com",  
	"1234",  
	new Address("서울", "강남구"),  
	List.of("USER"),  
	new ProfileImage("default.png")  
);

// prototype
User user1 = prototype.copy();
```
- 생성할 객체의 원형을 제공하는 인스턴스에서 생성할 객체들의 타입이 결정되도록 설정하며 객체를 생성할 때 갖추어야 할 기본 형태가 있을 때 사용되는 디자인 패턴
	- 객체를 생성할 때 갖추어야할 기본 형태란 객체가 만들어질 때 기본적으로 가지고 있어야 하는 상태를 뜻한다.
	- 생성할 객체의 원형을 제공하는 인스턴스란 새 객체를 만들 때 클래스가 아니라 이미 존재하는 객체가 복사 기준을 제공한다는 뜻이다.
	- 인스턴스에서 타입이 결정된다는 뜻은 prototype  인스턴스의 실제 타입에 따라 새 객체 타입이 결정된다는 뜻이다.
``` java
Monster prototype1 = new Slime();
Monster prototype2 = new Orc();

Monster monster1 = prototype1.copy(); // Slime 생성
Monster monster2 = prototype2.copy(); // Orc 생성
```
- 기존 객체를 복제함으로써 객체를 생성

##### Factory Method
- 상위 클래스에서 객체를 생성하는 인터페이스를 정의하고 하위 클래스에서 인스턴스를 생성하도록 하는 패턴
	- 여기서 부모가 java 의 interface 를 구현한다는 뜻이 아니라 객체 생성용 메서드의 틀을 정한다는 뜻으로 이해하면 된다.
	- 자식 클래스는 인터페이스 타입을 구현한 실제 객체를 생성한다.
	- 부모 클래스가 객체를 만들 메서드 이름과 반환 타입만 정하고, 자식 클래스가 실제로 어떤 객체를 new 할지 결정하는 패턴
- 상위 클래스에서는 인스턴스를 만드는 방법만 결정하고, 하위 클래스에서 그 데이터의 생성을 책임지고 조작하는 함수들을 오버라이딩하여 인터페이스와 실제 객체를 생성하는 클래스를 분리할 수 있는 특성을 갖는 디자인 패턴 
- 생성할 객체의 클래스를 국한하지 않고 객체를 생성
	- 즉, 생성할 객체를 부모 코드에 박아두지 않고 하위 클래스가 결정하게 한다는 뜻이다.

##### Abstract Factory
- 구체적인 클래스에 의존하지 않고 서로 연관되거나 의존적인 객체들의 조합을 만드는 인터페이스를 제공하는 패턴
- 이 패턴을 통해 생성된 클래스에서는 사용자에게 인터페이스를 제공 하고 구체적인 구현은 Concrete Product 클래스에서 이루어지는 특징을 갖는 디자인 패턴
- 동일한 주제의 다른 팩토리를 묶음
``` java
interface UIFactory {
    Button createButton();
    Checkbox createCheckbox();
}
```

``` java
class MacFactory implements UIFactory {
    public Button createButton() {
        return new MacButton();
    }

    public Checkbox createCheckbox() {
        return new MacCheckbox();
    }
}
```

##### Singleton
- 전역 변수를 사용하지 않고 객체를 하나만 생성하도록 하며, 생성된 객체를 어디에서든지 참조할 수 있도록 하는 디자인 패턴
- 하나의 클래스에 하나의 인스턴스만 존재

#### 구조 패턴
##### Bridge
- 기능의 클래스 계층과 구현의 클래스 계층을 연결하고, 구현부에서 추상 계층을 분리하여 추상화된 부분과 실제 구현 부분을 독립적으로 확장할 수 있는 디자인 패턴
- 기능의 클래스 계층 -  무엇을 할 수 있는가
``` java
class RemoteControl {
    void turnOn() {}
    void turnOff() {}
}
```

``` java
class AdvancedRemoteControl extends RemoteControl {
    void mute() {}
}
```
- 구현의 클래스 계층 - 실제로 어떤 대상에게 동작을 수행할 것인가
``` java
interface Device {
    void powerOn();
    void powerOff();
    void setVolume(int volume);
}
```
- 둘을 연결한 다는 것은 상속으로 다 엮지 않고 기능 클래스가 구현 객체를 필드로 가진다.
``` java
class RemoteControl {
    protected Device device;

    public RemoteControl(Device device) {
        this.device = device;
    }

    public void turnOn() {
        device.powerOn();
    }

    public void turnOff() {
        device.powerOff();
    }
}
```
- 추상 계층은 `RemoteControl` 쪽이 추상화 된 부분이며, 사용자는 리모컨을 통해 조작하지, 내부에서는 어떻게 켜지는지 모른다. 반대로 구현쪽은 실제로 전원을 켜고, 끄고, 볼륨을 조절하는 쪽이다. Bridge는 이 둘을 상속으로 한 덩어리로 만들지 않고 따로 둔다. 
- 구현뿐만 아니라, 추상화된 부분까지 변경해야 하는 경우 활용

##### Decorator
- 기존에 구현되어 있는 클래스에 필요한 기능을 추가해 나가는 설계 패턴
- 기능 확장이 필요할 떄 객체 간의 결합을 통해 기능을 동적으로 유연하게 확장할 수 있게 해주어 상속의 대안으로 사용하는 디자인 패턴
- 객체의 결합을 통해 기능을 동적으로 유연하게 확장
	- 즉, `class ShotAmericano extends Americano`로 하지 않고, `new ShotDecorator(new Americano())` 로 한다는 뜻이다. 상속 대신 포함을 사용한다는 뜻으로 이해하면 된다.
- 기능을 추가할 때 보통 Decorator 클래스를 하나 만들고 기존 객체를 필드로 가진다. 단, 감싸는 객체와 감싸지는 객체가 같은 인터페이스 타입이어야 한다. 그래야 겉에서 보았을 때 원래 객체처럼 사용할 수 있다.
###### 예시
- 기본 커피가 아래와 같이 있다.
``` java
interface Coffee{
	int cost();
	String description();
}
```
- 기본 구현체는 아래와 같다
``` java
class Americano implements Coffee {
    @Override
    public int cost() {
        return 3000;
    }

    @Override
    public String description() {
        return "아메리카노";
    }
}
```
- 여기서 샷 추가, 우유 추가, 시럽 추가 기능이 필요하다고 할 때 상속으로 할 경우 클래스가 폭발적으로 증가하게 된다.
- 그래서 Decorator 는 아래와 같이 공통 Decorator 클래스를 만든다.
``` java
abstract class CoffeeDecorator implements Coffee {
    protected Coffee coffee;

    public CoffeeDecorator(Coffee coffee) {
        this.coffee = coffee;
    }
}
```
-  그 이후 샷 추가 Decorator 를 생성한다.
``` java
class ShotDecorator extends CoffeeDecorator {

    public ShotDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public int cost() {
        return coffee.cost() + 500;
    }

    @Override
    public String description() {
        return coffee.description() + " + 샷 추가";
    }
}
```
- 우유 추가 Decorator 를 생성한다.
``` java
class MilkDecorator extends CoffeeDecorator {

    public MilkDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public int cost() {
        return coffee.cost() + 700;
    }

    @Override
    public String description() {
        return coffee.description() + " + 우유 추가";
    }
}
```
- 사용은 아래와 같이 하면 된다.
``` java
public class Main {
    public static void main(String[] args) {
        Coffee coffee = new Americano();

        coffee = new ShotDecorator(coffee); // 샷 추가
        coffee = new MilkDecorator(coffee); // 우유 추가
        coffee = new SyrupDecorator(coffee); // 시럽 추가

        System.out.println(coffee.description());
        System.out.println(coffee.cost());
    }
}
```

##### Facade
- 복잡한 시스템에 대하여 단순한 인터페이스를 제공함으로써 사용자와 시스템 간 또는 여타 시스템과의 결합도를 낮추어 시스템 구조에 대한 파악을 쉽게 하는 패턴
	- Facade 가 없으면 Controller 가 많은 객체를 의존해야 하지만 Facade 를 사용함으로써 Facade 하나만 의존하면 된다.
- 오류에 대해서 단위별로 확인할 수 있게 하며 사용자의 측면에서 단순한 인터페이스 제공을 통해 접근성을 높일 수 있는 디자인 패턴
- 통합된 인터페이스 제공
	- 여러 기능을 하나의 입구로 묶는다. 즉, `facade.signup()` 이런 식으로 복잡한 내부 로직 대신 의미 있는 큰 기능 단위만 호출하면 되게 된다.
###### 예시
- 예를 들어 회원가입 기능을 할 때, 아래와 같은 실제 여러 일이 일어난다.
	1. 이메일 중복 확인
	2. 비밀번호 암호화
	3. 사용자 저장
	4. 환영 이메일 발송
	5. 로그에 기록
- 이걸 사용하는 쪽에서 전부 직접 호출하면 코드가 복잡해진다.
``` java
emailService.checkDuplicate(email);
String encodedPassword = passwordEncoder.encode(password);
userRepository.save(user);
mailService.sendWelcomeMail(email);
logService.write("회원가입 완료");
```
- Facade 패턴은 이것을 하나로 감싼다.
``` java
userSignupFacade.signup("지혜", "jihye@email.com", "1234");
```

##### Flyweight
- 다수의 객체로 생성될 경우 모두가 갖는 본질적인 요소를 클래스화 하여 공유함으로써 메모리를 절약하고, '클래스의 경량화'를 목적으로 하는 디자인 패턴 
	- 여기서 말하는 본질적인 요소란 보통 객체들이 공통으로 가지고 있는 변하지 않는 정보를 뜻한다. Flyweight 에서는 이것을 내부 상태 또는 공유 상태라고 본다.
- 여러 개의 가상 인스턴스를 제공하여 메모리를 절감
	- 실제로는 공유 객체 하나를 쓰지만, 겉은로 보기에는 여러 객체가 각각 존재하는 것처럼 동작하게 한다는 뜻이다. 
- 똑같이 반복되는 객체 데이터를 매번 새로 만들지 말고, 공통 부분은 하나만 만들어서 공유하는 패턴
###### 예시
- 게임에서 나무를 10만개 만든다고 가정했을 때, 나무마다 아래와 같은 정보가 있다.
``` java
나무 종류: 소나무
색상: 초록색
이미지: pine.png
크기: 보통
x좌표: 10
y좌표: 20
```
- 그런데 나무 10만개가 모두 종류, 색상, 이미지 정보를 각각 들고 있으면 메모리가 낭비된다.
``` java
나무1: 소나무, 초록색, pine.png, x=10, y=20
나무2: 소나무, 초록색, pine.png, x=30, y=50
나무3: 소나무, 초록색, pine.png, x=70, y=90
```
- 여기서 반복되는 `소나무, 초록색, pine.png` 는 모든 소나무가 공유할 수 있다. 나무마다 달라지는 것은 `x, y`좌표이다. Flyweight 는 이 둘을 나눈다.
- 아래와 같이 공통 정보를 담는 클래스를 만든다.
``` java
class TreeType {
    private final String name;
    private final String color;
    private final String image;

    public TreeType(String name, String color, String image) {
        this.name = name;
        this.color = color;
        this.image = image;
    }

    public void draw(int x, int y) {
        System.out.println(
                name + " 그리기, 색상: " + color +
                ", 이미지: " + image +
                ", 위치: (" + x + ", " + y + ")"
        );
    }
}
```
- 여기서 말하는 TreeType 이 Flyweight 객체이다. 이 값들은 여러 나무가 공유할 수 있다. 이 객체를 매번 새로 만드는 것이 아니라 재사용하는 Factory를 만든다.

##### Proxy
- 실제 객체에 대한 대리 객체
- 실체 객체에 대한 접근 이전에 필요한 행동을 취할 수 있게 만들며 이 점을 이용해서 미리 할당하지 않아도 상관없는 것들을 실제 이용할 때 할당하게 하여 메모리 용량을 아낄 수 있으며, 실체 객체를 드러나지 않게 하여 정보 은닉의 역할도 수행하는 디자인 패턴
	- 진짜 필요할 때까지 실제 객체 생성을 미루는 것으로 지연 로딩이라고도 한다.
- 특정 객체로의 접근을 제어하기 위한 용도로 사용
- 진짜 객체 앞에 대리 객체를 세워서 진짜 객체에 접근하기 전에 검사나 추가 작업을 하게 만드는 패턴
- Decorator 와 비슷해보일 수 있으나 둘은 목적이 다르다. 즉, Proxy는 실제 객체에 대한 접근을 제어하여 권한 검사, 지연 로딩, 캐싱, 대리 호출을 한다. 반면 Decorator 는 기존 객체에 기능을 덧붙이는 것이 목적이다.

###### 예시
- 이미지를 불러오는 객체가 아래와 같이 있다.
``` java
interface Image {
    void display();
}
```

``` java
class RealImage implements Image {
    private String fileName;

    public RealImage(String fileName) {
        this.fileName = fileName;
        loadFromDisk();
    }

    private void loadFromDisk() {
        System.out.println(fileName + " 파일을 디스크에서 로딩");
    }

    @Override
    public void display() {
        System.out.println(fileName + " 이미지 출력");
    }
}
```
- 진짜 이미지 객체는 파일을 로딩해야해서 무거운데, 이 객체는 생성될 때 파일을 바로 로딩한다. 그런데 이미지가 실제로 화면에 보이지 않을 수도 있으므로 미리 로딩하는 것은 메모리 낭비가 된다. 즉, 상품 이미지가 100개 있으면 사용자가 처음 화면을 열었을 때 실제로 보이는 것은 위쪽 10개 뿐인 것이다. 그런데 프로그램이 처음부터 100개 이미지를 모두 올리면 메모리 낭비가 되는 것이다. 
``` java 
class ProxyImage implements Image {
    private String fileName;
    private RealImage realImage;

    public ProxyImage(String fileName) {
        this.fileName = fileName;
    }

    @Override
    public void display() {
        if (realImage == null) {
            realImage = new RealImage(fileName);
        }

        realImage.display();
    }
}
```

``` java
public class Main {
    public static void main(String[] args) {
        Image image = new ProxyImage("cat.png");

        System.out.println("이미지 객체 생성 완료");

        image.display();
        image.display();
    }
}
```

- 위에처럼 display 가 될 때만 실제 이미지를 메모리에 올리는 것이다.

##### Composite
- 객체들의 관계를 트리 구조로 구성하여 부분-전체 계층을 표현하는 패턴
	- 부분-전체 계층이란 큰 객체 안에 작은 객체들이 포함되는 구조를 뜻한다.
- 사용자가 단일 객체와 복합 객체 모두 동일하게 다루도록 하는 패턴
	- 단일 객체 `File` 와 복합 객체 `Folder`를 같은 인터페이스로 묶는다. 즉, `File`, `Folder`를 같은 인터페이스를 구현한다. 그러면, 사용하는 쪽에서 파일인지 폴더인지 크게 신경쓰지 않고 호출이 가능하다. 이것이 동일하게 취급한다는 뜻이다. 
- 복합 객체와 단일 객체를 동일하게 취급. 즉, 하나짜리 객체와 여러 개를 담을 객체를 똑같은 방식으로 다루게 만드는 패턴이다.

###### 예시
- 컴퓨터 파일 시스템에서 폴더와 파일은 트리 구조를 이룬다. 여기서 파일을 단일 객체라고 보고 폴더를 복합 객체라고 본다. 사용자가 둘 다 비슷하게 다루고 싶어 할 때 아래와 같이 사용한다.
``` java
file.show();
foleder.show();
```
- 파일이면 자기 이름만 보여주고, 폴더면 안에 있는 파일과 폴더들을 전부 보여주면 된다. 이것이 Composite 패턴이다.

##### Adapter
- 기존에 생성된 클래스를 재사용할 수 있도록 중간에서 맞춰주는 역할을 하는 인터페이스를 만드는 패턴
	- `KakaoPay` 클래스는 라이브러리 클래스로 이미 만들어져있지만, 내 코드의 인터페이스와 맞지 않는 것이다. 그러나 해당 클래스를 직접 수정하면 안된다.(외부 라이브러리 또는 기존 코드의 버그 생성 등). 그래서 기존 클래스는 그대로 두고 중간ㄷ에 Adapter 를 두는 것이다.
- 상속을 이용하는 클래스 패턴과 위임을 이용하는 인스턴스 패턴의 두 가지 형태로 사용하는 디자인 패턴
- 인터페이스가 호환되지 않는 클래스들을 함께 이용할 수 있도록 타클래스와 인터페이스를 기존 인터페이스에 덧씌운다.
	- 기존 클래스 위에 내가 원하는 인터페이스 모양을 하나 씌운다는 뜻이다. 즉, 사용하는 쪽에서는 `KakaoPay`의 원래 이름을 몰라도 사용할 수 있다. `paymentProcessor.pay(10000)`으로 통일해서 사용할 수 있기 때문이다.
- 원래 서로 맞지 않는 인터페이스를 중간에서 변환해서 같이 쓸 수 있게 만드는 패턴이다.

###### 필요성
- 내가 만든 서비스는 아래와 같은 인터페이스를 기대한다고 가정한다.
``` java
interface PaymentProcessor{
	void pay(int amount);
}
```
- 이 때 내 코드는 결제를 할 때 무조건 `paymentProcessor.pay(10000)`라고 쓰고 싶어한다.
- 그런데 외부 결제 라이브러리는 이미 아래와 같이 만들어져있다.
``` java
class KakaoPay{
	public void requestPayment(int price){
		System.out.println("카카오페이 결제: "+price+ "원");
	}
}
```
- 메서드 이름이 다르므로 인터페이스가 호환되지 않는다. 이 때 Adapter가 필요하여 만드는 것이다. 

###### 사용법
- 아래와 같이 Adapter 를 만든다. 
``` java
class KakaoPayAdapter implements PaymentProcessor{
	private final KakaoPay kakaoPay;
	
	public KakaoPayAdapter(KakaoPay kakaoPay){
		this.kakaoPay = kakaoPay;
	}
	
	// 핵심
	@Override
	public void pay(int amount){
		kakaoPay.requestPayment(amount);
	}
}
```
- 서비스가 원하는 `pay()` 메소드를 호출하면 Adapter 가 내부에서 카카오페이의 `requestPayment()` 로 바꿔서 호출해주는 것이다.

###### 상속을 이용하는 클래스 패턴
- 아래와 같이 Adapter 가 `KakaoPay`를 상속받는다.
``` java
class KakaoPayClassAdapter extends KakaoPay implements PaymentProcessor{
	@Override
	public void pay(int amount){
		requestPayment(amount);
	}
}
```
- 그리고 동시에 내가 원하는 인터페이스를 구현한다. 이 방식은 기존 클래스를 상속해서 메서드를 직접 호출할 수 있다. 하지만, Java 는 다중 상속이 불가능하기 때문에 유연성이 떨어질 수 있다.

###### 위임을 이용하는 인스턴스 패턴
- 아까의 예시로 든 사용 방식으로 이 방식이 더 자주 사용된다.
``` java
class KakaoPayAdapter implements PaymentProcessor{
	private final KakaoPay kakaoPay;
	
	public KakaoPayAdapter(KakaoPay kakaoPay){
		this.kakaoPay = kakaoPay;
	}
	
	@Override
	public void pay(int amount){
		kakaoPay.requestPayment(amount);
	}
}
```
- 여기서는 Adapter 가 `KakaoPay`를 상속하지 않고 필드로 가지고 있는다. 그리고 실제 일은 `KakaoPay`에게 맡기는 것이다. 이것을 위임이라고 한다. 실무에서는 보통 이 인스턴스 패턴을 더 많이 쓴다고 생각하면 된다.

#### 행위 패턴
##### Mediator
- 객체 지향 설계에서 객체의 수가 너무 많아지면 서로 간 통신을 위해 복잡해져서 객체 지향에서 가장 중요한 느슨한 결합의 특성을 해칠 수 있으므로 이를 해결하는 방법으로 중간에 이를 통제하고 지시할 수 있는 역할을 하는 중재자를 두고, 중재자에게 모든 것을 요구하여 통신의 빈도수를 줄려 객체 지향의 목표를 달성하게 해주는 디자인 패턴
- 상호 작용의 유연한 변경을 지원

###### 필요성
- 채팅방에 사용자가 `지혜, 철수, 영희, 민수` 이렇게 4명이 있다고 생각하자. 만약 각 사용자가 서로를 직접 알아야 한다면 관계가 아래와 같이 복잡해진다.
``` java
지혜 → 철수
지혜 → 영희
지혜 → 민수

철수 → 지혜
철수 → 영희
철수 → 민수

영희 → 지혜
영희 → 철수
영희 → 민수

민수 → 지혜
민수 → 철수
민수 → 영희
```
- 사용자가 많아질수록 연결선이 거미줄처럼 늘어난다. 이러면 한 객체가 너무 많은 객체를 알게되어 결합도가 높아진다. Mediator 패턴은 이것을 아래와 같이 바꾼다.
```
지혜 ┐
철수 ┤
영희 ┤ → ChatRoomMediator (채팅방 중재자)
민수 ┘
```
- 중재자가 있다는 것은 사용자가 메세지를 보낼 때
``` java
// (X)
chulsoo.receive("안녕");
younghee.receive("안녕");
minsoo.receive("안녕");

// O
chatRoom.sendMessage(this, "안녕");
```
- 이렇게 보내면 `ChatRoom` 이 알아서 다른 사용자들에게 전달한다는 뜻이다. 즉, 객체가 다른 객체들을 직접 조작하지 않고, 중간 객체에게 처리해달라고 요청하는 것이다.

###### 예시
- 중재자 인터페이스를 만든다.
``` java
interface ChatMediator {
    void sendMessage(User sender, String message);
    void addUser(User user);
}
```
- 그 이후 사용자 클래스를 만든다
``` java
class User{
	private String name;
	private ChatMediator mediator;
	
	public User(String name) { 
		this.name = name; 
	} 
	
	public void setMediator(ChatMediator mediator) { 
		this.mediator = mediator; 
	}
	
	public void send(String message){
		System.out.println(name + "전송 : " + message);
		mediator.sendMessage(this, message);
	}
	
	public void receive(String message){
		System.out.println(name + "수신 : " + message);
	}
}
```
- 여기서의 핵심은 사용자가 다른 사용자를 모른다는 것이다. 즉, 사용자는 철수, 영희, 민수를 필드로 가지지 않는다. 오직 mediator 만 안다.
- 중재자 구현 클래스는 아래와 같다.
``` java
import java.util.ArrayList;
import java.util.List;

class ChatRoom implements ChatMediator {
    private List<User> users = new ArrayList<>();

    @Override
    public void addUser(User user) {
        users.add(user);
        user.setMediator(this);
    }

    @Override
    public void sendMessage(User sender, String message) {
        for (User user : users) {
            if (user != sender) {
                user.receive(message);
            }
        }
    }
}
```
- 사용은 아래와 같다
``` java
ChatMediator chatRoom = new ChatRoom();

User jihye = new User("지혜");
User chulsoo = new User("철수");

chatRoom.addUser(jihye);
chatRoom.addUser(chulsoo);

jihye.send("안녕!");
```
- User 가 ChatMediator 인터페이스에 의존한다.

##### Interpreter
- 언어의 다양한 해석, 구체적으로 구문을 나누고 그 분리된 구문의 해석을 맡는 클래스를 각각 작성하여 여러 형태의 언어 구문을 해석할 수 있게 만드는 디자인 패턴
	- 꼭 한국어, 영어 같은 자연어가 아니라 규칙이 있는 표현식을 뜻한다. 예를 들어, `1 + 2`, `A AND B`, `age > 20`, `user.role == ADMIN` 이런 것들도 넓게 보면 언어라고 할 수 있다. 즉, 정해진 문법을 가진 문자열이나 표현식이라고 보면 된다.
	- 구문을 나눈다는 뜻은 `지혜 AND 개발자` 이것을 하나의 문자열로만 보면 그냥 글자 덩어리이다. Interpreter 는 이것을  `지혜`, `AND`, `개발자` 처럼 쪼갠다. 그리고 각각을  `WordExpression("지혜")`, `AndExpression(...)`, `WordExpression("개발자")`와 같이 객체로 표현한다. 즉, 문자열을 문법 단위로 쪼개서 각각 해석 가능한 객체로 만드는 것이다. 
	- 분리된 구문의 해석을 맡는 클래스를 각각 작성한다는 것은 단어 해석은 `WordExpression`, AND 해석은 `AndExpression`, OR 해석은 `OrExpression` 이런식으로 만든다는 뜻이다. 각 클래스는 자기 역할만 해석한다. 즉, `WordExpression` 은 특정 단어가 포함되어 있는지만 확인하고, `AndExpression`은 양쪽 조건이 모두 참인지 확인하고, `OrExpression`은 둘 중 하나라도 참인지 확인한다.
- 문법 자체를 캡슐화하여 사용
	- 문법 규칙을 if 문으로 흩뿌리지 않고, 각각의 클래스로 감싼다는 뜻이다.
- 문장을 작은 문법 단위로 쪼개고, 각 문법단위를 객체로 만들어서 해석하게 하는 패턴으로 문자열을 보고 의미를 해석하는 규칙을 클래스로 만든다고 보면 된다.
- 특정 문법 규칙을 가진 간단한 언어를 해석하는 패턴이 Interpreter 이다.

###### 예시
- 공통 인터페이스를 만든다.
``` java
interface Expression{
	boolean interpret(String context);
}
```
- 여기서 단어 하나를 해석하는 클래스를 만든다.
``` java
@AllArgsConstructor
class WordExpression implement Expression{
	private String word;
	
	@Override
	public boolean interpret(String context){
		return context.contains(word);
	}
}
```
- 이렇게 만들면 `new WordExcpression("지혜")`는 문장 안에 "지혜" 가 있는지 검사할 수 있다.
- AND 조건을 해석하는 클래스를 만든다. 
``` java
@AllArgsConstructor
class AndExpression implements Expression {
    private Expression left;
    private Expression right;

    @Override
    public boolean interpret(String context) {
        return left.interpret(context) && right.interpret(context);
    }
}
```
- OR 조건을 해석하는 클래스를 만든다.
``` java
@AllArgsConstructor
class OrExpression implements Expression {
    private Expression left;
    private Expression right;

    @Override
    public boolean interpret(String context) {
        return left.interpret(context) || right.interpret(context);
    }
}
```
- 아래와 같이 사용하면 된다.
``` java
public class Main {
    public static void main(String[] args) {
        Expression jihye = new WordExpression("지혜");
        Expression developer = new WordExpression("개발자");

        Expression condition = new AndExpression(jihye, developer);

        System.out.println(condition.interpret("지혜는 개발자입니다.")); // true
        System.out.println(condition.interpret("지혜는 학생입니다.")); // false
    }
}
```

###### 사용처
- 간단한 수식 계산기, 검색 조건 해석, 필터 조건 해석, 규칙 엔진, SQL 비슷한 간단한 DSL 등에서 사용할 수 있다.
- 단, Interpreter 문법이 단순할 때는 괜찮지만 문법이 복잡해지면 클래스가 엄청 많아질 수 있다. 그래서 복잡한 언어를 만들 때는 보통 파서 라이브러리나 컴파일러 구조를 따로 사용한다. Interpreter 패턴은 작고 단순한 규칙 언어에 적합하다.

##### Iterator
- 컬렉션 구현 방법을 노출시키지 않으면서도 그 집합체 안에 들어있는 모든 항목에 반복자(Iterator)를 사용하여 접근할 수 있는 디자인 패턴
- 내부구조를 노출하지 않고, 복잡 객체의 원소를 순차적으로 접근 가능하게 해주는 행위 패턴
- 자료구조 안이 어떻게 생겼는지는 숨기고 바깥에서는 하나씩 꺼내 볼 수 있게 해주는 패턴

###### 필요성
- 보통 순회할 때는 아래와 같이 한다
``` java
List<String> students = List.of("지혜", "정훈", "영희");

for(String student: students){
	System.out.println(student);
}
```
- 겉으로는 간단하지만, 내부적으로는 Iterator 개념이 들어가 있다. 즉, 사용자는 `ArrayList`가 내부에 배열을 쓰는지, `LinkedList`가 노드를 쓰는지 몰라도 된다. 
- Iterator 를 안쓰면 내부 구조에 따라 순회 코드가 달라질 수 있다. 예를 들어 List 이다가 Set 으로 바꾸면 인덱스 접근이 되지 않을 수 있다. 그런데 Iterator 를 쓰면 통일 시킬 수 있다. 

##### Template Method
- 어떤 작업을 처리하는 일부분을 서브 클래스로 캡슐화해 전체 일을 수행하는 구조는 바꾸지 않으면서 특정 단계에서 수행하는 내역을 바꾸는 패턴
- 일반적으로 상위 클래스(추상 클래스)에는 추상 메서드를 통해 기능의 골격을 제공하고, 하위 클래스(구체 클래스)의 메서드에는 세부 처리를 구체화하는 방식으로 사용하며 코드 양을 줄이고 유지보수를 용이하게 만드는 특징을 갖는 디자인 패턴
- 상위 작업의 구조를 바꾸지 않으면서 서브 클래스로 작업 일부분을 수행
- 전체 작업 순서는 부모 클래스가 정해두고, 중간중간 달라지는 세부 단계만 자식 클래스가 구현하게 하는 패턴으로 부모가 큰 흐름을 잡고, 자식이 세부 내용을 채우는 구조이다.

###### 예시 - 음료 만들기
- 커피와 차를 만드는 과정은 아래와 같이 비슷하다.
	1. 물을 끓인다
	2. 재료를 넣는다
	3. 컵에 따른다.
	4. 추가 재료를 넣는다.
- 그런데 둘은 재료와 추가 재료가 다르다. 여기서 전체 순서만 고정이 된다. 이럴 때 Template Method 패턴을 사용한다.

###### 코드
1. 부모 클래스가 전체 흐름을 정한다.
``` java
abstract class Beverage{
	// Template Method
	// 전체 작업 순서를 정의한다.
	// final 을 붙여 자식이 마음대로 흐름을 바꿀 수 없도록 한다.
	public final void prepare(){
		boilWater();
		brew();
		pourInCup();
		addCondiments();
	}
	
	private void boilWater(){
		System.out.println("물을 끓인다");
	}
	
	protected abstract void brew(); // 재료
	
	private void pourInCup(){
		System.out.println("컵에 따른다.");
	}
	
	protected abstract void addCondiments(); // 추가 재료
}
```
2. 자식 클래스는 일부 단계만 구현한다. 
``` java
// 커피
class Coffee extends Beverage{
	@Override
	protected void brew(){
		System.out.println("커피를 내린다.");
	}
	
	@Override
	protected void addCodiments(){
		System.out.println("설탕과 우유를 넣는다.");
	}
}
```

``` java
// 차
class Tea extends Beverage {

    @Override
    protected void brew() {
        System.out.println("찻잎을 우린다.");
    }

    @Override
    protected void addCondiments() {
        System.out.println("레몬을 넣는다.");
    }
}
```
3. 사용은 다음과 같이 한다. 
``` java
public class Main {
    public static void main(String[] args) {
        Beverage coffee = new Coffee();
        coffee.prepare();

        System.out.println();

        Beverage tea = new Tea();
        tea.prepare();
    }
}
```

###### Hook 메서드
- Template Method 에는 Hook 메서드라는 것도 자주 나온다. Hook 은 쉽게 말하면 자식 클래스가 필요하면 끼어들 수 있는 선택 단계를 뜻한다. 즉, 어떤 사람은 커피에 설탕과 우유를 넣고, 어떤 사람은 넣지 않을 수 있다. 

``` java
abstract class Beverage {

    public final void prepare() {
        boilWater();
        brew();
        pourInCup();

        if (wantsCondiments()) {
            addCondiments();
        }
    }

    private void boilWater() {
        System.out.println("물을 끓인다.");
    }

    protected abstract void brew();

    private void pourInCup() {
        System.out.println("컵에 따른다.");
    }

    protected abstract void addCondiments();

    // Hook Method
    protected boolean wantsCondiments() {
        return true;
    }
}
```
- 자식이 원하지 않으면 아래와 같이 바꿀 수 있다. 
``` java
class BlackCoffee extends Beverage {

    @Override
    protected void brew() {
        System.out.println("블랙커피를 내린다.");
    }

    @Override
    protected void addCondiments() {
        System.out.println("아무것도 넣지 않는다.");
    }

    @Override
    protected boolean wantsCondiments() {
        return false;
    }
}
```

##### Observer
- 한 객체의 상태가 바뀌면 그 객체에 의존하는 다른 객체들에 연락이 가고 자동으로 내용이 갱신되는 방법으로 일대 다의 의존성을 가지며 상호 작용하는 객체 사이에서는 가능하면 느슨하게 결합하는 디자인 패턴
	- 일대다 의존성이란 하나의 객체를 여러 객체가 지켜보는 구조를 뜻한다. 
	- 한 객체의 상태가 바뀌면 다른 객체들에게 연락이 간다는 것은 해당 객체를 구독하고 있던 객체들에게 자동으로 알려준다는 뜻이다. 중요한 것은 사용하는 쪽에서 일일이 이렇게 호출하지 않아도 된다는 뜻이다.
	- 여기서 느슨하게 결합한다는 뜻은 `WeatherData` 는 구체 클래스를 직접 몰라도 된다. 즉, 구체 타입을 직접 의존하지 않고, 그냥 `Observer` 인터페이스만 안다. 그래서 새로운 `Observer`를 추가해도 `Weather` 코드를 크게 바꿀 필요가 없다. 그래서 느슨한 결합이라고 볼 수 있다.
- 객체의 상태 변화에 따라 다른 객체의 상태도 연동, 일대다 의존
- 어떤 객체의 상태가 바뀌었을 때 그 객체를 지켜보고 있던 다른 객체들에게 자동으로 알려주는 패턴

###### 예시 - 유튜브 구독
- 유튜브 채널 `개발 채널` 이 있고, 구독자 `지혜, 철수, 영희`가 있다. 개발 채널에 새 영상이 올라오면 구독자들에게 알림이 간다. 이것이 `Observer` 패턴이다. 
- 즉, Subject 는 유튜브 채널, Observer 는 구독자들이라고 보면 된다. 

###### 코드 예시
- Observer 인터페이스는 다음과 같다. 이 인터페이스를 구현한 객체들은 알림을 받을 수 있는 객체이다.
``` java 
interface Observer{
	void update(int temperature);
}
```
- Subject 인터페이스는 다음과 같다. 
``` java
interface Subject{
	void registerObserver(Observer observer);
	void removeObserver(Observer observer);
	void notifyObservers();
}
```
- 날씨 데이터 클래스 
``` java
import java.util.ArrayList;
import java.util.List;

class WeatherData implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private int temperature;

    @Override
    public void registerObserver(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(temperature);
        }
    }
    
		// 온도가 바뀌면 바로 Observer 들에게 알림을 보낸다. 
    public void setTemperature(int temperature) {
        this.temperature = temperature;
        notifyObservers();
    }
}
```

- Observer 구현체 1
``` java
class CurrentTemperatureDisplay implements Observer {
    @Override
    public void update(int temperature) {
        System.out.println("현재 온도 표시: " + temperature + "도");
    }
}
```
- Observer 구현체 2
``` java
class HeatWarningDisplay implements Observer {
    @Override
    public void update(int temperature) {
        if (temperature >= 30) {
            System.out.println("폭염 주의 알림");
        }
    }
}
```
- 사용하는 코드는 다음과 같다.
``` java
public class Main {
    public static void main(String[] args) {
        WeatherData weatherData = new WeatherData();

        Observer currentDisplay = new CurrentTemperatureDisplay();
        Observer warningDisplay = new HeatWarningDisplay();

        weatherData.registerObserver(currentDisplay);
        weatherData.registerObserver(warningDisplay);

        weatherData.setTemperature(28);
        weatherData.setTemperature(31);
    }
}
```

###### 사용처
- 어떤 객체의 상태 변화를 여러 객체가 알아야 할 때
- 알림, 이벤트, 구독 구조가 필요할 때
- 상태 변경에 따라 화면이나 데이터가 자동 갱신되어야 할 때

###### Mediator 랑의 차이
- Mediator
	- 여러 객체 사이의 복잡한 상호작용을 중재자가 조정한다.
	- 채팅방, 관제탑 느낌
- Observer
	- 한 객체의 상태 변화가 여러 객체에게 자동 전달된다
	- 구독, 알림 느낌

##### State
- 객체 상태를 캡슐화하여 클래스화함으로써 그것을 참조하게 하는 방식으로 상태에 따라 다르게 처리할 수 있도록 행위 내용을 변경하여, 변경 시 원시 코드의 수정을 최소화할 수 있고, 유지보수의 편의성도 같는 디자인 패턴
	- 객체 상태를 캡슐화하여 클래스화 한다는 뜻은 상태별 행동을 각각의 클래스로 감싼다는 뜻이다. 예를 들어 주문 상태가 있다고 해보자 `결제 완료 상태, 배송중 상태, 배송 완료 상태` . 이 때, 각 상태마다 행동이 달라진다. `결제 완료 상태에서 취소 -> 가능`, `배송 중 상태에서 취소 -> 불가능`, `배송 완료 상태에서 반품 -> 가능`. 이것을 상태 클래스 안에 넣는 것이다. 
	- 새로운 상태가 추가되어도 if 문 방식은 기존 Order 클래스 안의 여러 메서드를 수정해야 하는 반면, State 패턴이면 새 상태 클래스만 추가하면 된다.
- 객체의 상태에 따라 행위 내용을 변경
	- 같은 메서드를 호출해도 상태에 따라 결과가 달라진다는 뜻이다. 
- 객체의 상태마다 행동이 달라질 때 상태를 if 문으로 처리하지 않고 상태 클래스로 분리하는 패턴

###### 필요성
- 객체 안에 아래와 같은 코드가 많아졌을 때 쓰는 패턴이다.
``` java
if (state.equals("주문완료")) {
    // 결제 가능
} else if (state.equals("배송중")) {
    // 결제 불가, 취소 제한
} else if (state.equals("배송완료")) {
    // 반품 가능
}
```
- 상태가 늘어나면 코드가 점점 진흑탕이 된다. 이것을 전부 if, switch 문으로 처리하면 유지 보수가 힘들어진다. State 패턴은 이 상태들을 각각의 클래스로 만든다.
``` java
OrderState
 ├─ PaidState
 ├─ ShippingState
 ├─ DeliveredState
 └─ CanceledState
```
- 그리고 `Order` 객체는 현재 상태 객체를 필드로 가진다. `privatge OrderState state`.

###### 코드
- 상태 인터페이스를 만든다.
``` java
interface OrderState {
    void cancel(Order order);
    void refund(Order order);
}
```
- 각 상태는 cancel(), refund() 를 자기 방식대로 처리할 것이다.
- 결제 완료 상태를 클래스로 만든다.
``` java
class PaidState implements OrderState {

    @Override
    public void cancel(Order order) {
        System.out.println("주문을 취소합니다.");
        order.setState(new CanceledState());
    }

    @Override
    public void refund(Order order) {
        System.out.println("아직 배송 전입니다. 취소를 이용하세요.");
    }
}
```
- 배송 중 상태.
``` java
class ShippingState implements OrderState {

    @Override
    public void cancel(Order order) {
        System.out.println("배송 중이라 취소할 수 없습니다.");
    }

    @Override
    public void refund(Order order) {
        System.out.println("배송 중에는 환불할 수 없습니다.");
    }
}
```
- 배송 완료 상태
``` java
class DeliveredState implements OrderState {

    @Override
    public void cancel(Order order) {
        System.out.println("이미 배송 완료되어 취소할 수 없습니다.");
    }

    @Override
    public void refund(Order order) {
        System.out.println("반품 요청을 진행합니다.");
    }
}
```
- 취소 상태
``` java
class CanceledState implements OrderState {

    @Override
    public void cancel(Order order) {
        System.out.println("이미 취소된 주문입니다.");
    }

    @Override
    public void refund(Order order) {
        System.out.println("취소된 주문은 환불 처리 대상이 아닙니다.");
    }
}
```
- 상태를 가지는 Order 객체
``` java
class Order {
    private OrderState state;

    public Order(OrderState state) {
        this.state = state;
    }

    public void setState(OrderState state) {
        this.state = state;
    }

    public void cancel() {
        state.cancel(this);
    }

    public void refund() {
        state.refund(this);
    }
}
```
- Order 는 현재 상태가 뭔지 직접 if 로 판단하지 않고 상태 개게에게 그냥 물어본다. 그러면 PaidState, ShippingState, DeliveredState 가 각자 알아서 처리한다.
- 사용은 아래와 같이 한다. 
``` java
public class Main {
    public static void main(String[] args) {
        Order order = new Order(new PaidState());

        order.cancel();
        order.cancel();

        System.out.println();

        Order shippingOrder = new Order(new ShippingState());
        shippingOrder.cancel();
        shippingOrder.refund();

        System.out.println();

        Order deliveredOrder = new Order(new DeliveredState());
        deliveredOrder.cancel();
        deliveredOrder.refund();
    }
}
```

##### Visitor
- 각 클래스 데이터 구조로부터 처리 기능을 분리하여 별도의 크래스를 만들어 놓고, 해당 클래스의 메서드가 각 클래스를 돌아다니며 특정 작업을 수행하도록 만드는 패턴
- 객체의 구조는 변경하지 않으면서 기능만 따로 추가하거나 확장할 때 사용하는 디자인 패턴
- 특정 구조를 이루는 복합 객체의 원소 특성에 따라 동작을 수행할 수 있도록 지원하는 행위
- 객체 구조는 그대로 두고 그 객체들에 대해 수행할 기능만 밖으로 빼는 패턴
	- 만약 출력 기능을 추가하고 싶으면 Book, Food, Electronics 클래스마다 print() 메서드를 추가해야 할 수 있다. 그런데 Visitor 를 쓰면 새 Visitor 만 만들면 된다. 

###### 예시 
- Book, Movie, Food 같은 클래스들이 이미 있는데 여기에 새로운 기능을 계속 추가해야 한다고 해보자. 예를 들어 가격계산, 할인 계산, 배송비 계산, 출력 형식 만들기, 검증하기. 이 기능들을 각 클래스 안에 계속 넣으면 클래스가 점점 뚱뚱해진다. Visitor 패턴은 이런 기능들을 객체 안에 넣지 않고 방문자 클래스로 따로 빼는 방식이다.
- 쇼핑몰 상품마다 가격 계산 방식이 다음과 같이 다르다고 보자.
```
Book: 기본 가격 그대로
Food: 신선식품 추가 포장비 있음
Electronics: 보증 비용 있음
```
- 이 계산 로직을 상품 클래스 안에 다 넣지 않고 밖으로 뺀다. 즉, `PriceVisitor`가 상품들을 돌아다니면서 계산하게 한다.
```
PriceVisitor → Book 방문
PriceVisitor → Food 방문
PriceVisitor → Electronics 방문
```
- 그래서 객체 순회 여행자처럼 Visitor 라는 이름이 붙은 것이다. 

###### 코드
- 방문 가능한 객체들의 공통 인터페이스를 만든다.
``` java
interface Product {
    void accept(ProductVisitor visitor); // 방문자를 받아들이는 메소드
}
```
- Visitor 인터페이스
	- 여기서 중요한 것은 상품 종류마다 `visit()` 메서드가 따로 있다는 것이다. 그래서 객체 종류에 따라 다른 처리를 할 수 있다. 
``` java
interface ProductVisitor {
    void visit(Book book);
    void visit(Food food);
    void visit(Electronics electronics);
}
```
- 상품 클래스들
	- `accept` 메소드로 인하여 `this`가 `Book`이면 `visit(Book book)` 이 호출되고, `this`가 `Food`면 `visit(Food food)`가 호출된다.
``` java
// 책
@AllArgsConstructor
@Getter
class Book implements Product {
    private String name;
    private int price;

    @Override
    public void accept(ProductVisitor visitor) {
        visitor.visit(this);
    }
}
```

``` java
// 음식
@AllArgsConstructor
@Getter
class Food implements Product {
    private String name;
    private int price;

    @Override
    public void accept(ProductVisitor visitor) {
        visitor.visit(this);
    }
}
```

``` java
// 전자제품
@AllArgsConstructor
@Getter
class Electronics implements Product {
    private String name;
    private int price;

    @Override
    public void accept(ProductVisitor visitor) {
        visitor.visit(this);
    }
}
```
- 가격 계산 Visitor 를 만든다.
	- 여기서 가격 계산 기능이 `Book`, `Food`, `Electronics` 안에 있지 않고, `PriceVisirot` 안에 모여 있다. 이것이 처리 기능을 분리한다는 뜻이다.
``` java
class PriceVisitor implements ProductVisitor {
    private int totalPrice = 0;

    @Override
    public void visit(Book book) {
        totalPrice += book.getPrice();
        System.out.println("책 가격 계산: " + book.getName());
    }

    @Override
    public void visit(Food food) {
        totalPrice += food.getPrice() + 1000; // 포장비
        System.out.println("음식 가격 계산: " + food.getName() + " + 포장비");
    }

    @Override
    public void visit(Electronics electronics) {
        totalPrice += electronics.getPrice() + 5000; // 보증비
        System.out.println("전자제품 가격 계산: " + electronics.getName() + " + 보증비");
    }

    public int getTotalPrice() {
        return totalPrice;
    }
}
```
- 사용 코드는 다음과 같다.
``` java
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Product> products = List.of(
                new Book("자바 책", 30000),
                new Food("샌드위치", 6000),
                new Electronics("키보드", 50000)
        );

        PriceVisitor priceVisitor = new PriceVisitor();

        for (Product product : products) {
            product.accept(priceVisitor);
        }

        System.out.println("총 가격: " + priceVisitor.getTotalPrice());
    }
}
```

###### 장점
- 새로운 기능을 추가할 때 기존 객체 클래스를 덜 건드린다.
- 기능별로 따로 관리할 수 있다.

###### 단점
- 방문 대상 클래스가 새로 추가되면 Visitor 들을 다 고쳐야 한다. 

###### 사용처
- 방문대상 클래스 종류는 자주 바뀌지 않는 대신 기능은 자주 추가될 때

##### Command
- 실행될 기능을 캡슐화함으로써 주어진 여러 기능을 실행할 수 있는 재사용성이 높은 클래스를 설계하는 패턴
	- 캡슐화 한다는 것은 어떤 행동을 클래스 안에 넣는다는 뜻이다.
- 하나의 추상 클래스에 메서드를 만들어 각 명령이 들어오면 그에 맞는 서브 클래스가 선택되어 실행되는 특징을 갖는 디자인 패턴
	- 모든 명령이 공통으로 따라야 하는 `execute()`메서드를 만들고 실제 명령 클래스들이 그 메서드를 각각 다르게 구현한다.
- 요구사항을 객체로 캡슐화
- 실행할 행동을 메서드 호출로 바로 실행하지 않고 하나의 객체로 포장해서 다루는 패턴.
- 기존에는 `light.turnOn()` 이런식으로 바로 호출했다면 Command 패턴은 이 행동을 객체로 만들어서 `Command command = new LightrOnCommand(light); command.execute()` 라고 한다. 여기서 `LightOnCommand`가 불 켜기 명령 객체이다

###### 기본 구조
- 먼저 모든 명령이 공통으로 가져야 할 인터페이스를 만든다
``` java
interface Command{
	void execute();
}
```
- 모든 명령은 `execute()`로 실행된다.
``` 
전등 켜기 명령
전등 끄기 명령
에어컨 켜기 명령
음악 재생 명령
```
- 사용하는 쪽은 구체 명령이 뭔지 몰라도 된다. 그냥 `command.execute()` 만 호출하면 된다.

###### 코드 예시
- 전등 클래스
	- 이 클래스는 실제 기능을 수행하는 객체이다. Command 패턴에서는 이것을 Receiver 라고 부른다(실제일을 하는 객체 Light)
``` java
class Light{
  public void turnOn() {
			System.out.println("전등 켜기");
	}

	public void turnOff() {
			System.out.println("전등 끄기");
	}
}
```
- 명령 객체를 만든다.
``` java
// 전등 켜기 명령
@AllArgsConstructor
class LightOnCommand implements Command {
    private Light light;

    @Override
    public void execute() {
        light.turnOn();
    }
}
```

``` java
// 전등 켜기 명령
@AllArgsConstructor
class LightOffCommand implements Command {
    private Light light;

    @Override
    public void execute() {
        light.turnOff();
    }
}
```
- 명령을 실행하는 객체
	- 리모컨은 전등을 직접적으로 모른다. 그래서 `private Light light` 이런 필드가 없다. 리모컨은 명령만 알고 있. 
``` java
@Setter
class RemoteControl {
    private Command command;

    public void pressButton() {
        command.execute();
    }
}
```
- 사용 코드
``` java
public class Main {
    public static void main(String[] args) {
        Light light = new Light();

        Command lightOnCommand = new LightOnCommand(light);
        Command lightOffCommand = new LightOffCommand(light);

        RemoteControl remoteControl = new RemoteControl();

        remoteControl.setCommand(lightOnCommand);
        remoteControl.pressButton();

        remoteControl.setCommand(lightOffCommand);
        remoteControl.pressButton();
    }
}
```

##### Strategy
- 알고리즘 군을 정의하고(추상 클래스) 같은 알고리즘을 각각 하나의 클래스로 캡슐화한 다음 필요할 때 서로 교환해 사용할 수 있도록 하는 패턴
	- 여기서의 알고리즘 군은 비슷한 목적을 가진 여러 방법 묶음을 뜻한다. 예를 들어 결제라면 결제 알고리즘 군은 가드 결제, 카카오페이 결제, 계좌이체 결제가 있다. 정렬이라면 정렬 알고리즘 군은 오름차순 정렬, 내림차순 정렬, 가격순 정렬이 있다. 할인이라면 정액 할인, 정률 할인, 회원 등급 할인이 있다. 이런 식으로 같은 목적을 가진 여러 방식을 알고리즘 군이라고 보면 된다.
- 행위를 클래스로 캡슐화해 동적으로 행위를 자유롭게 바꿀 수 있게 해주는 디자인 패턴
	- 행위를 클래스로 캡슐화한다는 뜻은 원래는 if 문으로 서비스 안에 코드가 들어가 있을 수 있지만 이런 것들을 밖으로 빼서 클래스로 만든다는 뜻이다.
- 행위 객체를 클래스로 캡슐화해 동적으로 행위를 자유롭게 변환
	- 실행 중에 전략 객체를 바꿀 수 있다. 즉, 내부 전략만 바꾸면 행동이 달라진다.
- 상황에 따라 바뀔 수 있는 방법을 클래스로 따로 빼고, 필요할 때 갈아끼워 쓰는 패턴으로 어떤 행동을 if 문으로 고르지 않고 행동 자체를 객체로 만들어서 교체하는 방식이다.

###### 필요성
- 결제 방식은 카드결제, 카카오페이 결제, 계좌이체 결제 방식이 있다.
- if 문으로 하면 다음과 같다.
``` java
class PaymentService {
    public void pay(String type, int amount) {
        if (type.equals("CARD")) {
            System.out.println("카드 결제: " + amount);
        } else if (type.equals("KAKAO")) {
            System.out.println("카카오페이 결제: " + amount);
        } else if (type.equals("BANK")) {
            System.out.println("계좌이체 결제: " + amount);
        }
    }
}
```
- 처음에는 괜찮아보여도 결제 방식이 늘어나면 if 문이 늘어나 좋지 않은 방식이며, PaymentService 를 계속 수정해야하는 단점이 있다. Strategy 패턴은 결제 방식을 각각 클래스로 분리한다. 

###### 코드
- 결제 방식은 여러 개 일 수 있지만, `pay()`라는 방식으로 실행하자는 전략 인터페이스
``` java
interface PaymentStrategy{
	void pay(int amount)
}
```
- 각각의 알고리즘을 클래스로 캡슐화한다
	- 여기서 각각의 클래스가 하나의 전략이며, 결제 알고리즘들을 각각 클래스로 캡슐화한 것이다.
``` java
// 카드 결제 전략
class CardPaymentStrategy implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println("카드 결제: " + amount + "원");
    }
}
```

``` java
// 카카오페이 결제 전략
class KakaoPayStrategy implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println("카카오페이 결제: " + amount + "원");
    }
}
```

``` java
// 계좌이체 결제 전략
class BankTransferStrategy implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println("계좌이체 결제: " + amount + "원");
    }
}
```
- 전략을 사용하는 클래스
	- 이 때 `PaymentService`는 구체적으로 카드 결제인지 카카오페이인지 모른다. 그냥 `PaymentStrategy` 만 알고있다.
``` java
@AllArgsConstructor
class PaymentService {
    private PaymentStrategy paymentStrategy;

    public void changeStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void pay(int amount) {
        paymentStrategy.pay(amount);
    }
}
```
- 사용 코드
``` java
public class Main {
    public static void main(String[] args) {
        PaymentService paymentService = new PaymentService(new CardPaymentStrategy());

        paymentService.pay(10000);

        paymentService.changeStrategy(new KakaoPayStrategy());
        paymentService.pay(20000);

        paymentService.changeStrategy(new BankTransferStrategy());
        paymentService.pay(30000);
    }
}
```

###### State  패턴, Command 패턴과의 차이
- Strategy
	- 사용자가 선택한 전략에 따라 행동을 바꿈
	- 결제 방식, 정렬 방식, 할인 방식
- State
	- 객체의 현재 상태에 따라 행동이 바뀐다.
	- 주문완료, 배송중, 배송완료
- Command
	- 요청 자체를 객체로 만드는 것이다. 
	- Stragegy 는 어떤 방식으로 처리할지를 객체로 만드는것이므로 다르다.

##### Memento
- 클래스 설계 관점에서 객체의 정보를 저장할 필요가 있을 때 적용하는 디자인 패턴
- Undo 기능을 개발할 때 사용하는 디자인 패턴
- 객체를 이전 상태로 복구시켜야 하는 경우 '작업취소(Undo)' 요청 가능
- 객체의 현재 상태를 저장해 두었다가 나중에 그 상태로 되돌리는 패턴

###### 필요성
- 문서 편집기에서 사용자가 Undo 를 누르면 이전 상태로 돌아가야한다. 이 때 객체의 이전 상태들을 어딘가에 저장해 둬야 한다. 그런데 외부 객체가 문서 내부 필드를 직접 뜯어보며 저장하면 캡슐화가 깨진다. 그래서 Memento 패턴은 문서 객체가 자기 상태 저장본을 직접 만들어주고, 외부에서 그 저장본을 보관만 하게 한다.
- Memento 패턴에는 보통 3가지 역할이 있다.
	- Originator : 원래 상태를 가진 객체(ex. Document)
	- Memento: 저장된 상태 객체(ex. DocumentMemento)
	- Caretaker : 저장본들을 보관하는 객체(ex. History)

###### 코드
- 문서 상태 저장본을 만든다
	- 문서의 특정 시점 상태를 담고 있다.
``` java
@RequiredArgsConstructor
@Getter
class DocumentMemento {
	private final String content;
}
```
-  실제 문서 객체
``` java
@AllArgsConstructor
class Document {
    private String content;

    public void write(String content) {
        this.content = content;
    }

    public void show() {
        System.out.println("현재 문서 내용: " + content);
    }

    // 현재 상태 저장
    public DocumentMemento save() {
        return new DocumentMemento(content);
    }

    // 저장된 상태로 복구
    public void restore(DocumentMemento memento) {
        this.content = memento.getContent();
    }
}
```
- 저장본 보관함
	- 문서 내용이 뭔지 해석하거나 수정하지 않고 저장본을 보관만 한다.
``` java
import java.util.Stack;

class History {
    private Stack<DocumentMemento> history = new Stack<>();

    public void push(DocumentMemento memento) {
        history.push(memento);
    }

    public DocumentMemento pop() {
        return history.pop();
    }

    public boolean isEmpty() {
        return history.isEmpty();
    }
}
```
- 사용 코드는 다음과 같다.
``` java
public class Main {
    public static void main(String[] args) {
        Document document = new Document("안녕");
        History history = new History();

        document.show();

        history.push(document.save());
        document.write("안녕하세요");
        document.show();

        history.push(document.save());
        document.write("안녕하세요 지혜입니다");
        document.show();

        document.restore(history.pop());
        document.show();

        document.restore(history.pop());
        document.show();
    }
}
```

##### Chain of Responsibility
- 정적으로 어떤 기능에 대한 처리의 연결이 하드코딩 되어 있을 때 기능 처리의 연결 변경이 불가능한데 이를 동적으로 연결되어 있는 경우에 따라 다르게 처리될 수 있도록 연결한 디자인 패턴
	- 처리의 연결이 하드코딩 되어있다는 뜻은 if -else 문으로 처리되어있는 것을 뜻한다. 이것을 정적으로 하드코딩된 처리 연결이라고 한다.
	- 동적으로 연결되어 있는 경우에 따라 다르게 처리라는 뜻은 체인의 순서나 구성을 바꿀 수 있다는 뜻이다. 상황에 따라 `setNext`를 이용하여 상황에 따라 바꿀 수 있다. 또한 특정 Handler 를 빼거나 추가할 수 있다.
- 한 요청을 2개 이상의 객체에서 처리
- 직역하면 책임 연쇄 패턴이라고 한다. 
- 하나의 요청을 여러 처리 객체들이 차례대로 받아보고 자신이 처리할 수 있으면 처리하고 아니면 다음 객체에게 넘기는 패턴
```
요청 → Handler A → Handler B → Handler C → 처리 완료
```
- 각 처리자를 클래스로 분리하여 이들을 체인처럼 연결하여 요청이 들어왔을 때 처리할 수 있는지 먼저 확인하고 할 수 없으면 다음으로 넘기는 방식으로 한다. 

###### 코드 예시
- 요청 클래스
``` java
@AllArgsConstructor
@Getter
class Request{
	private String level;
}
```
- 공통 Handler 추상 클래스
	- 여기서 Handler 가 다음 Handler 를 알고 있으며 자신이 처리를 못하면 넘긴다.
``` java
@Setter
abstract class SupportHandler{
	protected SupportHandler next;
	
	public void handle(Request request){
		if(canHandle(request)){
			process(request);
			return;
		}
		
		if(next != null){
			next.handle(request)
		} else{
			System.out.println("처리할 수 있는 담당자가 없습니다.");
		}
	}
	
	protected abstract boolean canHandle(Request request);
	
	protected abstract void process(Request request);
}
```
- 구체 Handler 들
``` java
// 1차 상담원
class LevelOneSupport extends SupportHandler {
    @Override
    protected boolean canHandle(Request request) {
        return request.getLevel().equals("LOW");
    }

    @Override
    protected void process(Request request) {
        System.out.println("1차 상담원이 처리합니다.");
    }
}
```

``` java
// 2차 상담원
class LevelTwoSupport extends SupportHandler {
    @Override
    protected boolean canHandle(Request request) {
        return request.getLevel().equals("MEDIUM");
    }

    @Override
    protected void process(Request request) {
        System.out.println("2차 상담원이 처리합니다.");
    }
}
```

``` java
// 관리자
class LevelTwoSupport extends SupportHandler {
    @Override
    protected boolean canHandle(Request request) {
        return request.getLevel().equals("HIGH");
    }

    @Override
    protected void process(Request request) {
        System.out.println("관리자가 처리합니다");
    }
}
```
- 사용 코드
``` java
public class Main {
    public static void main(String[] args) {
        SupportHandler levelOne = new LevelOneSupport();
        SupportHandler levelTwo = new LevelTwoSupport();
        SupportHandler manager = new ManagerSupport();

        levelOne.setNext(levelTwo);
        levelTwo.setNext(manager);

        levelOne.handle(new Request("LOW"));
        levelOne.handle(new Request("MEDIUM"));
        levelOne.handle(new Request("HIGH"));
        levelOne.handle(new Request("UNKNOWN"));
    }
}
```

###### 사용처
- 로그인 요청 처리
``` 
요청 → 빈 값 검사 → 이메일 형식 검사 → 비밀번호 검사 → 로그인 처리
```
- Spring Security Filter Chain
```
요청 > JWT 인증 필터 > SecurityContext 설정 > 권한 검사 > Controller
```
- 예외처리 : 예외 
```
예외 → CustomExceptionHandler → ValidationExceptionHandler → DefaultExceptionHandler
```
- 고객센터 문의
```
문의 → 1차 상담원 → 전문 상담원 → 관리자
```

# 요구사항
## 개요
### 요구공학(Requirements Engineering)의 개요
- 사용자의 요구가 반영된 시스템을 개발하기 위하여 사용자 요구사항에 대한 도출, 분석, 명세, 확인, 및 검증하는 구조화된 활동
### 요구공학의 목적
- 이해관계자 사이에 효과적인 의사소통 수단을 제공하고 시스템 개발의 요구사항에 대한 공통된 이해를 설정한다.
- 요구사항 누락 방지 및 이해 오류로 인한 불필요한 비용을 절감하고 요구사항 변경 추적을 가능하게 한다.

### 요구사항의 분류
- 요구사항 파악의 기본은 시스템의 요구사항에 대한 파악이다.
- 요구사항은 기능적 요구사항과 비기능적 요구사항으로 분류된다.

#### 기능적 요구사항
##### 개념
- 시스템이 제공하는 기능, 서비스에 대한 요구사항
##### 도출 방법
- 특정 입력에 대해 시스템이 어떻게 반응해야 하는지에 대한 기술
- 특정 상황에 대해 시스템이 어떻게 동작해야 하는지에 대한 기술
##### 특성
###### 기능성
- 요구사항이 시스템이 제공해야 할 기능을 제대로 설명하고 있는지
- 시스템이 무엇을 해야 하는가가 분명히 드러나는 성질
- 시스템이 제공해야 할 기능이 요구사항에 명확히 들어 있는가

###### 완전성
- 필요한 기능이 빠짐없이 요구사항에 포함되어 있는지
- 해야 할 기능이 누락되지 않았는가를 보는 성질
- 필요한 기능이 빠짐없이 적혀있는가

###### 일관성
- 요구사항들끼리 서로 모순되지 않는지
- 요구사항끼리 충돌하지 않는가를 보는 성질
- 요구사항들이 서로 말이 맞는가

##### 사례
- 온라인 홈페이지에서는 쇼핑카트에 주문하고자 하는 품목을 저장할 수 있는 장바구니 기능을 제공해야 함
- 상품의 결제 수단은 신용카드, 무통장 입금, 포인트 결제가 가능해야 함

#### 비기능적 요구사항
##### 개념
- 시스템이 수행하는 기능 이외의 사항, 시스템 구축에 대한 제약사항에 관한 요구사항

##### 도출 방법
- 품질 속성과 관련하여 시스템이 갖춰야 할 사항에 관한 기술
- 시스템이 준수해야 할 제한 조건에 관한 기술

##### 특성
###### 신뢰성
- 시스템이 고장 없이 안정적으로 동작하는 정도
###### 사용성
- 사용자가 시스템을 얼마나 쉽고 편하게 사용할 수 있는지
###### 효율성
- 시스템이 자원과 시간을 얼마나 효율적으로 사용하는지
###### 유지보수성
- 시스템을 수정하거나 확장하기 쉬운 정도
###### 이식성
- 시스템을 다른 환경으로 옮겼을 때 얼마나 쉽게 동작할 수 있을지를 말한다
###### 보안성
- 시스템이 허가되지 않은 접근이나 공격으로부터 보호되는 정도
###### 품질 관련 요구사항
- 시스템의 전반적인 품질에 대한 요구사항으로 위에서 말한 특성드로 전부 품질 속성에 들어가나.
- 시스템이 얼마나 좋은 품질로 동작해야 하는지에 대한 요구
###### 제약사항
- 시스템을 개발하거나 운영할 때 반드시 지켜야 하는 제한 조건
- 개발 환경, 기술, 법률, 표준, 운영 조건에 대한 제한

##### 사례
- 특정 함수의 호출시간은 3초를 넘지 않아야 한다.
- 시스템은 하루 24시간 가동되어야 하며 가동률 99.5%를 만족해야 한다.
- 시스템은 운영되는 중에 패치 및 업그레이드를 할 수 있어야 한다.

## 프로세스
- 요구사항 프로세스는 요구사항 개발 단계와 요구사항 관리 단계로 구성된다.
![[Frame 21.png|642]]

### 요구사항 개발 단계 구성(CMM Level 3 프로세스 영역)
#### 요구사항 도출 단계(Elicitation)
##### 설명
- 요구사항 도출 단계는 소프트웨어가 해결해야 할 문제를 이해하고, 고객으로부터 제시되는 추상적 요구에 대해 관련 정보를 식별하고 수집 방법 결정, 수집된 요구사항을 구체적으로 표현하는 단계이다.
##### 주요 기법
###### 인터뷰(Interview)
- 이해관계자 직접 대화를 통해 정보를 구하는 공식적 · 비공식적 정보 수집 방법
###### 브레인스토밍(Brainstorming)
- 말을 꺼내기 쉬운 분위기로 만들어 회의 참석자들이 내놓은 아이디어들을 비판 없이 수용할 수 있도록 하는 회의
###### 델파이 기법(Delphi Method)
- 전문가의 경험적 지식을 통한 문제 해결 및 미래 예측을 위한 기법
###### 롤 플레잉(Role Playing)
- 현실에 일어나는 장면을 설정하고 여러 사람이 각자가 맡은 역을 연기하여 요구사항을 분석하여 수집하는 방법
###### 워크숍(Workshop)
- 단기간의 집중적인 노력을 통해 다양하고 전문적인 정보를 획득하고 공유하는 방법
- 프로젝트에 참여하는 모든 핵심 인물의 참여가 필요
- 참석자들은 해당 전문 영역별로 팀 협력이 필요하며 사전 준비가 요구
###### 설문조사(Survey)
- 설문지 또는 여론조사 등을 이용해 간접적으로 정보를 수집
- 개발될 시스템의 사용자가 다수일 때 의견 수렴에 용이
###### 프로토타입(prototype)
- 고객이 요구한 주요 기능을 시제품으로 구현
- 고객의 피드백을 통해 개선, 보완하여 완성 소프트웨어를 만들어 가는 모델

#### 요구사항 분석 단계(Analysis)
##### 설명
- 요구사항 분석 단계는 추출된 요구사항에 대해 충돌, 중복, 누락 등의 분석을 통해 완전성과 일관성을 확보하는 단계이다.
##### 분석 단계 기법
###### 데이터 흐름도(DFD; Data Flow Diagram)
- 데이터가 각 프로세스를 따라 흐르면서 변환되는 모습을 나타낸 그림
- 시스템 분석과 설계에서 매우 유용하게 사용되는 다이어그램
###### 자료사전(DD; Data Dictionary)
- 자료 요소, 자료 요소들의 집합, 자료의 흐름, 자료 저장소의 의미와 그들 간의 관계, 관계 값, 범위, 단위들을 구체적으로 명시하는 사전
###### UML(Unified Modeling Language)
- 객체 지향 소프트웨어 개발 과정에서 산출물을 명세화, 시각화, 문서화할 시 사용되는 모델링 기술과 방법론을 통합해 만든 표준화된 범용 모델링 언어

#### 요구사항 명세 단계(Specification)
##### 설명
- 요구사항 명세 단계는 체계적으로 검토, 평가, 승인될 수 있는 문서를 작성하는 단계이다.
- 산출물로 요구사항 명세서가 있다.
	- 요구사항 명세서 : 소프트웨어 개발 프로세스의 시작인 소프트웨어의 요구사항을 분석하고 정의하는 단계에서 작성되는 최종 산출물이다.

##### 주요 기법
###### 비정형 명세 기법
- 사용자의 요구를 표현할 때 자연어를 기반으로 서술하는 기법
- 사용자와 개발자의 이해가 용이
- 명확성 및 검증에 문제
###### 정형 명세 기법
- 사용자의 요구를 표현할 때 수학적인 원리와 표기법으로 서술하는 기법
- 정형 명세 언어인 Z-스키마, Petri Nets, 상태 차트 활용
	- Z-스키마 : 논리를 기반으로 한 수학적 표현을 사용하여 여러 특성을 함축적으로 표현하는 수리적 논리적 명세 언어이다.
- 표현이 간결, 명확성 및 검증이 용이
- 기법의 이해가 어려움

#### 요구사항 확인 및 검증 단계 
##### 설명
- 요구사항 확인 및 검증은 요구사항 명세서에 사용자의 요구가 올바르게 기술되었는지에 대한 검토, 베이스라인을 설정하는 활동이다.
- 프로젝트 참여자들이 요구사항을 이해했는지 확인하고 요구사항 문서가 프로젝트 표준에 적합한지, 일관성을 만족하는지, 완전한지를 검증해야 한다.

##### 주요 기법
###### 동료 검토(Peer Review)
- 2~3명이 진행하는 리뷰의 형태
- 요구사항 명세서 작성자가 요구사항 명세서를 설명하고 이해관계자들이 설명을 들으면서 결함을 발견하는 형태로 진행하는 검토 방법

###### 워크 스루(Walk Through)
- 오류를 조기에 검출하는 데 목적이 있는 검토 방법
- 검토 자료를 회의 전에 배포해서 사전 검토한 후 짧은 시간 동안 회의를 진행하는 형태로 리뷰를 통해 오류를 검출하고 문서화 하는 비공식적인 검토 방법

###### 인스펙션(Inspection)
- 소프트웨어 요구, 설계, 원시 코드 등의 저작자 외의 다른 전무가 또는 팀이 검사하여 오류를 찾아내는 공식적인 검토 방법
- 인스펙션 절차는 `계획 > 사전 교육 > 준비 > 인스펙션 회의 > 수정 > 후속 조치` 순서로 진행
### 요구사항 관리 단계(CMM Level 2 프로세스 영역)
#### 설명
- 프로젝트 진행 과정에서 발생하는 요구사항의 변경에 대해 일치성과 무결성을 제공하기 위해 변경 제어와 추적 등 일련의 관리를 수행하는 활동
- 주요 산출물로는 요구사항 변경요청서, 요구사항 변경승인서, 요구사항 추적표가 있다

#### 단계 절차
##### 요구사항 협상
- 가용한 자원과 수용 가능한 위험 수준에서 구현 가능한 기능을 협상하기 위한 기법
- 우선순위 설정, 시뮬레이션
##### 요구사항 기준선 설정
- 공식적으로 검토되고 합의된 요구사항 명세서를 통해 기준선을 설정하기 위한 방법
- 공식 회의, 형상관리
	- 형상관리 : 소프트웨어 생명주기 동안 발생하는 변경 사항을 체계적으로 관리하여 소프트웨어의 품질보증을 향상시키는 관리적 활동이다
##### 요구사항 변경 관리
- 요구사항 기준선을 기반으로 모든 변경을 공식적으로 통제하기 위한 기법
- 형상 통제 위원회, 영향도 분석
	- 형상 통제 위원회(CCB; Configuration Control Board) : 형상 관리에 대한 주요 방침을 정하고 산풀물을 검토하며, 단계별 의사결정을 수행하는 조직이다.