# 닷넷이란 무엇인가?

## 기본 개념

### 용어

* 공통 중간 언어 (Common Intermediate Language)
  - 자바와 마찬가지로 C# 소스 코드를 컴파일하면 기계어로 바로 번역되는 것이 아니라 중간 언어(Intermediate Language)로 먼저 번역되고, 닷넷 런타임이 IL을 기계어로 번역해 준다. (자바의 바이트코드 같은 개념)
  - IL은 구조상 어셈블리어와 비슷하게 생겼으며, 정식 명칭은 CIL(Common Intermediate Language)라고 함
  - ILASM.EXE 컴파일러를 이용해 IL 코드를 컴파일하면 동일한 결과물을 얻을 수 있다.
  - C#, VB.NET, C++/CLI, ASP.NET, F# 외에도 COBOL, Lisp, Python, PHP, Ruby 등의 언어도 IL 언어로 번역할 수 있으므로 닷넷 런타임은 언어에 독립적이다.
  - 하지만 C#은 닷넷에 의한, 닷넷을 위한, 닷넷의 언어이므로 닷넷 기능을 최대한 활용할 수 있다.
 
* 공용 타입 시스템 (Common Type System)
  - 닷넷 호환 언어가 지켜야 할 타입의 표준 규격
  - CTS 규약의 범위를 벗어난 언어는 IL을 생성할 수 없다. (가령, 다중 상속)
  - 그러나 CTS 규약을 100% 구현할 필요는 없다.
 
* 공용 언어 사양 (Common Language Specification)
  - 닷넷 호환 언어가 지켜야 할 최소한의 언어 사양
  - 예를 들어 C#, VB.NET 등 닷넷 호환 언어로 작성된 프로그램이 다른 언어로 작성된 프로그램과 객체를 공유할 수 있는 이유는 CLS를 준수하기 때문이다.
 
* 메타데이터
  - C# 언어로 컴파일된 실행 파일에는 메타데이터가 있어서, 소스가 없어도 Reflection 기술을 이용해 어떤 클래스, 메서드가 제공되는지 확인 가능하다.
 
* 어셈블리, 모듈, 매니페스트
  - 어셈블리: 닷넷에서 생성한 결과물(EXE, DLL)을 의미함 (그 어셈블리가 아니다!)
  - 어셈블리 안에는 1개 이상의 모듈이 있을 수 있다.
  - 모듈 목록을 관리하는 매니페스트라는 것이 있다.
  - 즉, 하나의 어셈블리 안에는 매니페스트를 포함하는 모듈이 무조건 있으며, 그 외의 모듈들이 있을 수 있다. (각 모듈은 메타데이터를 갖고 있음)
 
* 공용 언어 기반구조 (Common Language Infrastructure)
  - 마이크로소프트에서 ECMA 표준으로 제출한 공개 규약: CTS 명세, IL에 대한 코드 정의, 메타데이터와 이진 파일의 구조 등
  - 마치 여러 회사에서 만든 JVM이 있듯이, 공개된 CLI를 이용해 닷넷 런타임을 만들 수 있다.
 
* 공용 언어 런타임 (Common Language Runtime)
  - CLR의 역할: (1) IL을 JIT 컴파일러를 이용해 기계어로 번역하고, (2) GC를 제공해 동적 메모리 할당 및 회수를 지원함
  - CLR 자체를 관리 환경(Managed Environment)라고 함
  - 과거 닷넷 프레임워크가 구현한 CLR은 CLI 사양을 따르는 대표적인 VM이었다.
  - 이후 닷넷 코어가 나오면서 다중 플랫폼에 맞게 재구현한 CoreCLR이 나왔다.
 
* 닷넷
  - 닷넷 = CoreCLR + 부가 구성 요소
  - 부가 구성요소로는 BCL(Base Class Library)와 기타 파일들이 있다.
  - 히스토리: "닷넷 프레임워크"가 처음에 등장, 다중 플랫폼 지원을 위해 "닷넷 코어"가 등장했다가 "닷넷"으로 통합됨
  - 닷넷 프레임워크는 4.8까지 나왔고, 닷넷 코어는 3.1까지 나왔으며, 닷넷은 5, 8, 7, 8 순서로 나왔다. (2024년 상반기)
  - 리눅스, Mac OS X, Android, iOS 등을 지원하며 모바일(Xamarin / .NET MAUI 프레임워크, Unity 게임 엔진)도 지원한다.

## C# 기초

### 자료형

* 기본 자료형
  - 정수형: sbyte, byte (8비트), short, ushort (16비트), int, uint (32비트), long, ulong (64비트)
    * 이것들은 닷넷 기본 타입의 별칭이다. (System.Sbyte, System.Byte, System.Int16, System.UInt16, System.Int32, System.UInt32, System.Int64, System.UInt64)
  - 실수형: float (4바이트, System.Single), double (8바이트, System.Double), decimal (16바이트, System.Decimal)
  - 문자형: char (유니코드 16비트, System.Char), string (유니코드 문자열, System.String)
  - 불리언: bool (System.Boolean)

### 기타 문법

* 형 변환 (암시적, 명시적), 예약어 및 키워드, 식별자, 리터럴, 변수 (스택, 힙), 상수, 연산자, 배열 (다차원, 가변 배열도 있음), 제어문 (조건문, 반복문), 구조체 (struct), 열거형 (enum)

### 객체 지향

* 클래스 (멤버, 메서드, 생성자, 종료자), 네임스페이스 (using, namespace), 캡슐화 (private, protected, public, internal, internal protected), 프로퍼티 (get, set), 읽기 전용 (readonly)

* 상속, 형 변환 (as, is), 부모 클래스 (base), 다형성 (오버라이드, 오버로드)

* 클래스 확장: 중첩 클래스, 추상 클래스, 델리게이트 (delegate), 이벤트, 인터페이스 (interface), 인덱서

* 깊은 복사와 얕은 복사 (ref [in, out 개념], out): 포인터 대용으로 생각하면 된다.

## C# 1.0

## BCL (Base Class Library)

## C# 2.0

## C# 3.0

## C# 4.0

## C# 5.0

## C# 6.0

## C# 7.0

## C# 7.1

## C# 7.2

## C# 7.3

## C# 8.0

## C# 9.0

## C# 10

## C# 11

## C# 12
