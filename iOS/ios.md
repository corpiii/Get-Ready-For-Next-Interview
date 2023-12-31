# iOS 질문과 답

## iOS
### Bounds 와 Frame 의 차이점을 설명하시오.
- Frame은 부모뷰의 좌측 상단을 기준으로 뷰의 크기, 위치를 표현하는 사각형
- Bounds는 뷰 자신의 좌측 상단을 기준으로 크기,위치를 표현하는 사각형

Frame은 부모뷰 내에서 뷰의 위치와 크기를 설정하는데 사용하고
Bounds는 내부 내용을 회전하거나 크기를 조절할 때 사용합니다.

---
### 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.

1. GPS, 카메라, 가속계, 자이로센서 등을 사용하기 어렵습니다.
2. 네트워크가 느리거나 끊김, 불안정한 경우를 테스트하기 어렵습니다.
3. 실제 사용자의 경험을 테스트하지 못합니다.

---
### 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체를 무엇이라고 하는가?

데이터베이스입니다.
iOS에서는 CoreData 프레임워크를 사용해서 쉽게 사용할 수 있습니다.
또한 iOS17 이후부터는 SwiftData 프레임워크 또한 사용할 수 있습니다.

---
### 앱 화면의 콘텐츠를 표시하는 로직과 관리를 담당하는 객체를 무엇이라고 하는가?

ViewController

---
### App thinning에 대해서 설명하시오.

사용자가 다운로드 하는 앱의 용량을 최적화하는 기술입니다.
크게 App slicing, Bitcode, On-Demand-Resource(ODR) 3가지로 나뉘며 

Appslicing은 다양한 디바이스를 지원하기 위해 여러 버전의 데이터를 올려두고 성능, 해상도에 맞게 데이터를 다운받을 수 있도록 하는 기술입니다.

Bitcode는 Appstore에 제출할 때 바이너리 코드보다 좀 더 추상화 된 단계의 코드를 제출해서 디바이스의 특성, 호환에 맞게 애플에서 알아서 코드를 바꿔주는 역할을 합니다. 프로젝트 파일의 build setting에서 설정해주면 자동으로 사용할 수 있습니다

ODR은 사용자가 데이터를 필요로 할 때 다운로드 해서 사용할 수 있는 기술 입니다. 프로젝트 파일에서 세팅해주고 Asset의 resource tag를 지정해 준 후 NSBundleResourceRequest 클래스를 사용해서 애플의 서버로 부터 다운로드 해서 사용합니다.


---

### 앱이 시작할 때 main.c 에 있는 UIApplicationMain 함수에 의해서 생성되는 객체는 무엇인가?

UIApplication와 Appdelegate가 생성됩니다.

---

### @Main에 대해서 설명하시오.

앱의 진입점을 설정합니다.

---
### 앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?



---
### 상태 변화에 따라 다른 동작을 처리하기 위한 앱델리게이트 메서드들을 설명하시오.

iOS 13이후부터 SceneDelegate로 변경되었으며

- sceneDidDisconnect
    - scene이 화면에서 제거되었을 때
- sceneDidBecomeActive
    - 화면이 active되었을 때 호출
- sceneWillResignActive
    - 화면이 inActive되기 직전 호출
- sceneWillEnterForeground
    - 화면이 foreground로 전환되기 직전에 호출
- sceneDidEnterBackground
    - 화면이 background로 전환되기 직전에 호출

---
### 앱이 In-Active 상태가 되는 시나리오를 설명하시오.

전화, 알림 같은 인터럽트가 발생하거나 되면 inActive 상태가 됩니다.
앱을 처음 시작하면 inactive 상태를 거쳐 active 상태가 됩니다.

---

### scene delegate에 대해 설명하시오.

iOS 13버전 이후 부터 사용가능한 객체이며
AppDelegate에서 각 Scene에 대한 라이프사이클 이벤트를 관리하는 객체입니다.

또한 여러개의 Scene을 가질 수 있기 때문에 각 Scene간의 데이터를 공유하고 관리할 수 있습니다.

---
### UIApplication 객체의 컨트롤러 역할은 어디에 구현해야 하는가?

?

---
### App의 Not running, Inactive, Active, Background, Suspended에 대해 설명하시오.

- Not running: 앱이 실행되기 전의 상태
- Inactive: 앱의 화면이 보이나 아직 활성화 되지 않은 상태
- Active: 앱의 화면이 보이고 정상적으로 실행중인 상태
- Background: 앱을 dismiss하여 화면에서 벗어났지만 백그라운드에서 실행중인 상태
- Suspended: Background에서도 작업을 실행하지 않고 메모리에 관련 데이터만 저장되어있는 상태


---
### NSOperationQueue 와 GCD Queue 의 차이점을 설명하시오.



---
### GCD API 동작 방식과 필요성에 대해 설명하시오.
### Global DispatchQueue 의 Qos 에는 어떤 종류가 있는지, 각각 어떤 의미인지 설명하시오.
### iOS 앱을 만들고, User Interface를 구성하는 데 필수적인 프레임워크 이름은 무엇인가?

UIKit, SwiftUI

---
### Foundation Kit은 무엇이고 포함되어 있는 클래스들은 어떤 것이 있는지 설명하시오.

데이터 관리에 필요한 클래스들을 제공하는 프레임워크입니다.

- Array, Dictionary, Set 등의 컬렉션 데이터 클래스
- NSDate, Calendar 등의 날짜 데이터 처리 클래스
- URL, URLSession 등의 네트워크 데이터 처리 클래스
- UserDefaults 같은 사용자 데이터 클래스
- Error 에러 관련 정보 처리 클래스

등이 있습니다.


---
### Delegate란 무엇인지 설명하고, retain 되는지 안되는지 그 이유를 함께 설명하시오.


### NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.
### UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?
### App Bundle의 구조와 역할에 대해 설명하시오.
### 모든 View Controller 객체의 상위 클래스는 무엇이고 그 역할은 무엇인가?
### 자신만의 Custom View를 만들려면 어떻게 해야하는지 설명하시오.
### View 객체에 대해 설명하시오.
### UIView 에서 Layer 객체는 무엇이고 어떤 역할을 담당하는지 설명하시오.
### UIWindow 객체의 역할은 무엇인가?
### UINavigationController 의 역할이 무엇인지 설명하시오.
### TableView를 동작 방식과 화면에 Cell을 출력하기 위해 최소한 구현해야 하는 DataSource 메서드를 설명하시오.

cellForRowAt, numberOfRowsInSection

- cellForRowAt: 각 Index에 해당하는 cell에 어떤 cell을 넣을 것인지.
- numberOfRowsInSection: 테이블 뷰의 한 섹션당 몇개의 Row를 가질 것인지.

---
### 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.
### setNeedsLayout와 setNeedsDisplay의 차이에 대해 설명하시오.

### NSCache와 딕셔너리로 캐시를 구성했을때의 차이를 설명하시오.
### URLSession에 대해서 설명하시오.
### prepareForReuse에 대해서 설명하시오.
### 다크모드를 지원하는 방법에 대해 설명하시오.
### ViewController의 생명주기를 설명하시오.
### TableView와 CollectionView의 차이점을 설명하시오.

## Autolayout
### 오토레이아웃을 코드로 작성하는 방법은 무엇인가? (3가지)
### hugging, resistance에 대해서 설명하시오.
### Intrinsic Size에 대해서 설명하시오.
### 스토리보드를 이용했을때의 장단점을 설명하시오.
### Safearea에 대해서 설명하시오.
### Left Constraint 와 Leading Constraint 의 차이점을 설명하시오.

## Swift
### struct와 class와 enum의 차이를 설명하시오.
### class의 성능을 향상 시킬수 있는 방법들을 나열해보시오.
### Copy On Write는 어떤 방식으로 동작하는지 설명하시오.
### Convenience init에 대해 설명하시오.
### AnyObject에 대해 설명하시오.
### Optional 이란 무엇인지 설명하시오.
### Struct 가 무엇이고 어떻게 사용하는지 설명하시오.
### Subscripts에 대해 설명하시오.
### String은 왜 subscript로 접근이 안되는지 설명하시오.
### instance 메서드와 class 메서드의 차이점을 설명하시오.
### class 메서드와 static 메서드의 차이점을 설명하시오.
### Delegate 패턴을 활용하는 경우를 예를 들어 설명하시오.
### Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오.
### KVO 동작 방식에 대해 설명하시오.
### Delegates와 Notification 방식의 차이점에 대해 설명하시오.
### 멀티 쓰레드로 동작하는 앱을 작성하고 싶을 때 고려할 수 있는 방식들을 설명하시오.
### MVC 구조에 대해 블록 그림을 그리고, 각 역할과 흐름을 설명하시오.
### 프로토콜이란 무엇인지 설명하시오.
### Protocol Oriented Programming과 Object Oriented Programming의 차이점을 설명하시오.
### Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.
### mutating 키워드에 대해 설명하시오.
### 탈출 클로저에 대하여 설명하시오.
### Extension에 대해 설명하시오.
### Extension 내부에서 함수를 override할 수 있는지 설명하시오.
### 접근 제어자의 종류엔 어떤게 있는지 설명하시오.
### defer란 무엇인지 설명하시오.
### defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.
### property wrapper에 대해서 설명하시오.
### Generic에 대해 설명하시오.
### some 키워드에 대해 설명하시오.
### Result타입에 대해 설명하시오.
### Codable에 대하여 설명하시오.
### Closure에 대하여 설명하시오.
### Closure와 함수와의 관계에 대해 설명하시오.

## ARC
### ARC란 무엇인지 설명하시오.
### Retain Count 방식에 대해 설명하시오.
### Strong 과 Weak 참조 방식에 대해 설명하시오.
### 순환 참조에 대하여 설명하시오.
### 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.

## Functional Programming
### 순수함수란 무엇인지 설명하시오.
### 함수형 프로그래밍이 무엇인지 설명하시오.
### 고차 함수가 무엇인지 설명하시오.
### Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.

## Architecture
### MVVM, MVI, Ribs, VIP 등 자신이 알고있는 아키텍쳐를 설명하시오.
### 의존성 주입에 대하여 설명하시오.

<!--
## SwiftUI
- @State에 대해서 설명하시오.

## Combine
- PassthroughSubject에 대해서 설명하시오
- @Published에 대해서 설명하시오
- AnyCancellable에 대해서 설명하시오
- sink에 대해서 설명하시오
- throttle과 debounce의 차이점을 설명하시오.

# Optional
아래부터는 추가로 공부를 하면 좋을 내용들입니다.

Objective-c나 rx는 회사, 팀마다 사용하는곳이 차이가있고 신입이나 주니어기준으로 필수라고 여겨지지않기에 옵셔널에 추가하였습니다.
-->
## Rx
### Reactive Programming이 무엇인지 설명하시오.
### RxSwift를 왜 사용하는지 설명하시오.
### RxSwift의 단점을 설명하시오.
### RxSwift에서 Hot Observable과 Cold Observable의 차이를 설명하시오.
### Subject의 종류와 차이점에 대해 설명하시오.
### Subject와 Driver의 차이를 설명하시오.
### Single, Completable, Maybe의 차이점에 대해 설명하고, 언제 적용하면 좋을지 설명하시오.

## MRC
### ARC 대신 Manual Reference Count 방식으로 구현할 때 꼭 사용해야 하는 메서드들을 쓰고 역할을 설명하시오.
### retain 과 assign 의 차이점을 설명하시오.
### 특정 객체를 autorelease 하기 위해 필요한 사항과 과정을 설명하시오.
### Autorelease Pool을 사용해야 하는 상황을 두 가지 이상 예로 들어 설명하시오. 
### 다음 코드를 실행하면 어떤 일이 발생할까 추측해서 설명하시오.
```swift
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
```

## Advanced
- method swizzling이 무엇이고, 어떨 때 사용하는지 설명하시오.
- NSCoder 클래스는 어떤 상황에서 어떻게 써야 하는지 설명하시오.
- Responder Chain 구조에 대해 설명하고, First Responder 역할에 대해 설명하시오.
- NSObject부터 UIButton 까지 상속 과정의 계층과 역할을 설명하시오.
- shallow copy와 deep copy의 차이점을 설명하시오.
- Push Notification 방식에 대해 설명하시오.
- Foundation 과 Core Foundation 프레임워크의 차이점을 설명하시오.
- NSURLConnection 에서 사용하는 Delegate 메서드들에 대해 설명하시오.
- Synchronous 방식과 Asynchronous 방식으로 URL Connection을 처리할 경우의 장단점을 비교하시오.
- Plist 파일 구조와 Plist 파일에 저장된 데이터를 다루기 적합한 클래스를 설명하시오.
- Core Data와 Sqlite 같은 데이터 베이스의 차이점을 설명하시오.
- JSON 데이터를 처리하는 방식과 파서, 객체 변환 방식에 대해 설명하시오.
- 웹 서버와 HTTP 연결을 사용해서 데이터를 주거나 받으려면 사용해야 하는 클래스와 동작을 설명하시오.
- Protocol에서는 왜 var만 되는지 설명하시요.
- DispatchQueue.main.sync를 사용하는 상황을 설명하시오.
- Run Loops에 대해 설명하시오.

## Objective-C
- Swift의 클로저와 Objective-C의 블록은 어떤 차이가 있는가?
- Mutable 객체과 Immutable 객체는 어떤것이 있는지 예를 들고, 차이점을 설명하시오.
- dynamic과 property 의미와 차이를 설명하시오.
- @property로 선언한 NSString* title 의 getter/setter 메서드를 구현해보시오.
- @property에서 atomic과 nonatomic 차이점을 설명하고, 어떤것이 안전한지, 어느것이 기본인지 설명하시오.
- @property로 선언한다는 것의 의미를 설명하고, .h에 넣을 경우와 .m에 넣을 경우 차이점을 설명하시오.
- -performSelector:withObject:afterDelay: 메시지를 보내면 인자값의 객체는 retain되는가? 그 이유를 함께 설명하시오.
- Objective-C 에서 캡슐화된 데이터를 접근하기 위한 방법들을 설명하시오.
- Fast Enumeration 이란 무엇인지 설명하시오. 
- unnamed category 방식에 대해 설명하시오.
- Category 확장과 Subclass 확장의 차이점을 설명하시오.
- Category 방식에 대해 설명하시오.
- Objective-C 에서 Protocol 이란 무엇인지 설명하시오.
- Objective-C++ 방식이 무엇인지 설명하고, 어떤 경우 사용해야 하는지 설명하시오.

