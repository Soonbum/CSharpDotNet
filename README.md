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
 
* 닷넷 프레임워크, 닷넷 코어, 그리고 닷넷
  - 닷넷 = CoreCLR + 부가 구성 요소
  - 부가 구성요소로는 BCL(Base Class Library)와 기타 파일들이 있다.
  - 히스토리: "닷넷 프레임워크"가 처음에 등장, 다중 플랫폼 지원을 위해 "닷넷 코어"가 등장했다가 "닷넷"으로 통합됨
  - 닷넷 프레임워크는 4.8까지 나왔고, 닷넷 코어는 3.1까지 나왔으며, 닷넷은 5, 8, 7, 8 순서로 나왔다. (2024년 상반기)
  - 리눅스, Mac OS X, Android, iOS 등을 지원하며 모바일(Xamarin / .NET MAUI 프레임워크, Unity 게임 엔진)도 지원한다.

| 설명 | .NET Framework | .NET Core |
| --- | --------------- | --------- |
| 플랫폼 | Windows | Linux, Mac OS X 등 |
| 앱 유형 | WPF, ASP.NET, Windows Forms | UWP, ASP.NET Core |
| 기반 라이브러리 | Base Class Library | Core Library |

* C# 언어는 닷넷의 버전 업그레이드와 함께 꾸준히 발전해 왔고 이를 간단히 정리하면 다음과 같다.
  - C# 언어의 향후 로드맵은 [여기](https://github.com/dotnet/roslyn/blob/main/docs/Language%20Feature%20Status.md)서 확인할 수 있다.

닷넷 런타임 | C# 언어 | 주요 기능
----------- | ------- | -------------
1.0, 1.1 | C# 1.0 | -
2.0, 3.0 | C# 2.0 - 기존 문법 보완 | 제네릭, 익명 함수, 널(Null) 타입
3.5 | C# 3.0 - 함수형 언어의 장점 흡수 | 람다 표현식, 확장 메서드, LINQ, 익명 타입
4.0 | C# 4.0 - 동적 언어의 장점 흡수 | 지연 바인딩, 선택적 파라미터, 명명된 인자, COM 지원 확장
4.5 | C# 5.0 - 비동기 호출 추가 | async/await 비동기 예약어
4.6 | C# 6.0 - 간편 표기 문법 보강 | 프레임워크와 컴파일러의 분리, 다수의 간편 표기 문법
4.7 ~ 4.7.2, 4.8 | C# 7.0 ~ 7.1 - 패턴 매칭, C# 7.2 - 구조체 성능 향상, C# 7.3 - 문법 보강 | 패턴 매칭, 튜플, `Span<T>`
.NET Core 3.0 | C# 8.0 - 문법 보강 | 비동기 스트림, 인덱스/범위 연산자, 기본 인터페이스 메서드, 다수의 간편 표기 문법
.NET 5 | C# 9.0 - 문법 보강 | 레코드, 함수 포인터, 모듈 이니셜라이저, 최상위 문
.NET 6 | C# 10 - 문법 보강 | record의 구조체 지원, 다수의 세부 문법 개선
.NET 7 | C# 11 - 문법 보강 | 패턴 매칭 추가, 원시 문자열 및 utf8 문자열 지원, 다수의 세부 문법 개선
.NET 8 | C# 12 - 문법 보강 | 기본 생성자, 기본 람다 파라미터, 인라인 배열, 컬렉션 식, 기타 문법 개선

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

### 문법 요소

* 전처리기 지시문: 특정 소스코드를 상황에 따라 컴파일 과정에서 추가/삭제할 때 사용한다.
  - #define, #undef: 소스코드 맨 위에 있어야 함
  - #if, #elif, #else, #endif: 적용되는 부분에 기록함
  - 그 외에도 #warning, #error, #line, #region, #endregion, #pragma 지시문이 있다.

* 지역 변수의 유효 범위: 지역 변수가 정의되면 변수를 포함하는 블록에서만 유효하다.

* 일반적인 애트리뷰트: 소스 외의 정보이며 메타데이터 정보에 포함됨, 프로그램에 영향을 끼치지 않으나 개발자가 정보를 남길 수 있음
  - System.Attribute로부터 상속 받은 클래스이다.
  - 애트리뷰트: 주석과 달리 컴파일러에게 코드에 대한 정보를 제공하기 위한 기능이다.
  - 형태는 다음과 같다: [AuthorAttribute], [Author], [Author()], [Author("Anders")], [Author("Anders", Version = 1)], ...
  - 생성자, 프로퍼티를 이용해 값을 지정할 수도 있다.
  - Reflection 기술과 함께 응용하여 사용될 수 있다.

* Flags 애트리뷰트
  - System.AttributeUsageAttribute는 다른 애트리뷰트와 달리 적용할 수 있는 대상이 한정되어 있다.
  - AttributeTargets 값의 종류의 각 타깃은 다음과 같다. (생략하면 다음 표에 따라 자동으로 선택됨)
  - 다만 타깃을 명시적으로 지정해야 하는 경우도 있다. (예를 들어, BCL의 MarshalAs 애트리뷰트는 타깃이 Field, Paramter, ReturnValue가 있으므로 직접 명시해야 함)

AttributeTargets 값 | [target: ...] | 설명
------------------- | ------------- | ---------
Assembly | assembly | 어셈블리
Module | module | 모듈
Class | type | class
Struct | type | struct
Enum | type | enum
Constructor | method | 타입의 생성자
Method | method | 타입의 메서드
Property | property | 타입의 프로퍼티
Field | field | 타입의 필드(멤버)
Event | event | 타입의 이벤트
Interface | type | interface
Parameter | param | 메서드의 파라미터
Delegate | type | delegate
ReturnValue | return | 메서드의 리턴값
GenericParameter | typevar | C# 2.0에 추가된 제네릭 파라미터에 지정됨
All | 기본값 | AttributeTargets에 정의된 모든 것

* 연산자
  - 시프트 연산자: 비트 단위로 데이터를 제어할 때 사용함 (<<, >>)
  - 비트 논리 연산자: 조건 논리 연산자(&&, ||, ^, !) 외에도 비트 논리 연산자(&, |, ^, ~)가 존재한다.
 
* 예약어
  - 연산 범위 확인: checked, unchecked (이 키워드 다음에 {}로 감싸면, 오버플로에 대한 예외를 발생 혹은 발생시키지 않음. 단, 언더플로는 체크 못함)
  - 가변 파라미터: params (함수 인자로 params 키워드 다음에 가변 배열 변수를 입력 받으면 임의의 개수를 인자로 받을 수 있다. C++의 va_list 개념)
  - Win32 API 호출: extern (C#에서 C/C++ 언어로 만들어진 비관리 코드의 기능을 사용할 때 platform invocation을 사용함)
    * 예를 들어, User32.dll 파일의 BOOL MessageBeep([in] UINT uTYPE) 함수를 호출한다고 해보자.
      ```cpp
      [DllImport("user32.dll")]
      static extern int MessageBeep(uint uType);
      ```
    * Win32 API에 대한 PInvoke 구문은 www.pinvoke.net 사이트에서 검색해 볼 수 있다.
  - 안전하지 않은 컨텍스트: unsafe (스택에 할당된 변수에 대해 C/C++ 언어의 포인터를 사용할 때 이 키워드를 맨앞에 붙임)
  - 참조 형식의 멤버에 대한 포인터: fixed (힙에 할당된 인스턴스에 대해 C/C++ 언어의 포인터를 사용할 때 이 키워드를 맨앞에 붙임)
  - 고정 크기 버퍼: fixed (위와 기능이 다름, extern으로 참조한 C++ DLL 함수에 인자를 넘길 때 메모리 배열 길이로 인한 오류를 막기 위해 unsafe 문맥에서 변수 앞에 사용함)
  - 스택을 이용한 값 형식 배열: stackalloc (값 형식의 배열을 힙이 아닌 스택에 강제로 할당하게 만듦, 스택은 용량이 적지만 빠름)
    ```cpp
    int* pArray = stackalloc int[1024];  // int 4byte * 1024 == 4KB 용량을 스택에 할당
    ```

### 프로젝트 구성

* 솔루션 (.sln)
  - 1개 이상의 프로젝트를 포함하고 있다.
  - 솔루션이 오피스 제품이라면, 프로젝트는 워드, 엑셀, 파워포인트, 아웃룩이라고 비유할 수 있다.

* 프로젝트 (.csproj)
  - 비주얼 스튜디오의 소스코드 관리를 위해 도입된 개념
  - 한 프로젝트 당 여러 개의 소스코드를 담을 수 있으며, 하나의 프로젝트는 하나의 EXE 또는 DLL 파일이 만들어진다. (내부적으로 XML 형식으로 기록되어 있음)

* 라이브러리 재참조
  - 본인이 만든 라이브러리, 닷넷이 제공하는 라이브러리, NuGet 패키지를 통해 받은 라이브러리를 활용할 수 있다.

* 디버그 빌드, 릴리스 빌드
  - 릴리스 빌드: 사용자에게 출시할 때에는 릴리스 빌드를 활용한다. (최적화 포함, 전처리 상수 TRACE 사용함)
  - 디버그 빌드: 개발 중에는 디버그 빌드를 활용한다. (최적화 없음, 전처리 상수 DEBUG/TRACE 사용함)
    * 전처리 상수 대신 [Conditional("DEBUG")] 애트리뷰트 등을 사용해도 됨
    * 그 외에도 System.Diagnostics 네임스페이스에서 Debug, Trace 타입의 WriteLine 함수를 이용해 Debug, Trace 메시지를 따로 출력할 수 있다. (DebugView 프로그램 활용 가능)

* 플랫폼 선택
  - 닷넷 런타임은 인텔/AMD CPU, ARM CPU를 지원하며, 그 외에도 모든 CPU를 지원한다. (x86/x64, ARM32/ARM64, AnyCPU)

### 예외

* 예외
  - 대표적인 예외로는 0으로 나누거나, 배열 범위를 벗어나거나, null을 참조하는 등이 있다.
  - System.Exception 타입이 제공하는 멤버는 다음과 같다.
    * Message (프로퍼티): 예외를 설명하는 메시지를 리턴한다.
    * Source (프로퍼티): 예외를 발생시킨 애플리케이션의 이름을 리턴한다.
    * StackTrace (프로퍼티): 예외가 발생한 메서드의 호출 스택을 리턴한다.
    * ToString (메서드): Message, StackTrace 내용을 포함하는 문자열을 리턴한다.
  - 개발자는 System.Exception에서 상속해서 예외를 직접 만들 수도 있다.

* 예외 처리 및 발생
  - try/catch/finally 구문을 이용해서 예외가 발생해도 프로그램이 중단되지 않도록 할 수 있다.
  - throw 구문을 이용해서 예외를 발생시킬 수도 있다.
  - 다만 예외 처리는 무겁기 때문에 가능하면 다른 방법을 사용해서 회피하는 것이 좋다.
  - 참고: using 키워드는 try/finally/Dispose에 대한 간편 표기법으로 사용된다. (네임스페이스를 선언하는 using과 다름)

### 가비지 수집기

* 가비지 수집기 (Garbage Collector)
  - 가비지 수집기 작동 원리
    * CLR에서 처음 할당되는 객체는 모두 0세대에 속한다.
    * 0세대 객체의 용량이 일정 크기를 넘어가면 GC는 가비지 수집을 한다. --> 사용되지 않는 0세대 객체는 없애고, 사용되는 객체는 1세대로 승격된다.
    * 1세대 객체의 총 용량이 일정 크기를 넘어가면 GC는 가비지 수집을 한다. --> 사용되지 않는 객체는 없애고, 1세대의 객체가 그 시점에도 사용되고 있으면 2세대로 승격된다. (2세대가 끝)
    * 2세대 객체의 총 용량이 일정 크기를 넘어가면 GC는 가비지 수집을 한다.
  - 가비지 수집을 하면 객체를 가리키는 주소값이 변경될 수 있다.
  - 단, 일정 크기의 객체는 가비지 수집마다 이동하면 성능이 크게 손실되므로 별도의 대용량 객체 힙(Oarge Object Heap)에 생성된다.
    * 주소는 바뀌지 않는 대신 메모리 파편화 현상이 발생한다.
    * 대용량 객체는 처음부터 2세대 객체로 분류한다.

## BCL (Base Class Library)

* __여기서 소개할 BCL 타입들은 일부에 불과하다. (자세한 것은 .NET API browser 참고할 것)__

### 시간

* System.DateTime
* System.TimeSpan
* System.Diagnostics.Stopwatch: 코드의 특정 구간에 대한 성능을 측정할 때 사용할 것

### 문자열 처리

* System.String
* System.Text.StringBuilder: 문자열을 연결하는 작업이 많을 때 사용할 것
* System.Text.Encoding: ASCII, Default, Unicode (UTF-16을 의미함), UTF32, UTF8 등이 있음
* System.Text.RegularExpressions.Regex

### 직렬화/역직렬화

* System.BitConverter
* System.IO.MemoryStream
* System.IO.StreamWriter / System.IO.StreamReader: 스트림에 문자열 데이터를 읽고 쓰는 데 유용함
* System.IO.BinaryWriter / System.IO.BinaryReader: 스트림에 이진 데이터를 읽고 쓰는 데 유용함
* System.Xml.Serialization.XmlSerializer
* System.Text.Json.JsonSerializer

### 컬렉션

* System.Collections.ArrayList
* System.Collections.Hashtable
* System.Collections.SortedList
* System.Collections.Stack
* System.Collections.Queue

### 파일

* System.IO.FileStream
* System.IO.File / System.IO.FileInfo
* System.IO.Directory / System.IO.DirectoryInfo
* System.IO.Path

### 스레딩

* System.Threading.Thread
* System.Threading.Monitor
* System.Threading.Interlocked
* System.Threading.ThreadPool
* System.Threading.EventWaitHandle
* 비동기 호출: I/O 연산이 끝날 때까지 차단되지 않으므로 non-blocking 호출이라고도 함
* System.Delegate의 비동기 호출: 일반 메서드에 대해서도 비동기 호출을 할 수 있는 수단 (C# 5.0의 async/await 구문이 제공되면서 거의 사용하지 않게 됨)

### 네트워크 통신

* System.Net.IPAddress
* 포트
* System.Net.IPEndPoint
* System.Net.Dns
* System.Net.Sockets.Socket
* System.Net.Http.HttpClient

### 데이터베이스

* 마이크로소프트 SQL 서버
* ADO.NET 데이터 제공자
* 데이터 컨테이너
* 데이터베이스 트랜잭션: using 키워드를 이용해 트랜잭션을 begin하고 마지막에 commit 해야 함

### 리플렉션

* AppDomain과 Assembly
* Type과 리플렉션
* 리플렉션을 이용한 확장 모듈 구현

### 기타

* 윈도우 레지스트리
* BigInteger
* IntPtr

## C# 2.0

### 제네릭

* 예를 들어, int와 같은 프리미티브 타입인 객체를 ArrayList와 같은 컬렉션 객체에 담을 경우 박싱/언박싱으로 인해 성능 저하가 발생한다.
  - 박싱/언박싱 문제: int 타입 <-> object 타입 식으로 잦은 형 변환이 발생하는 문제
  - 제네릭은 C++의 template과 유사한 개념이다.
  - `ArrayList`를 보완한 `List<T>` 타입이 도입됨: 여기서 T는 타입으로 대체할 수 있다.
  - 구체적인 프리미티브 타입을 지정함으로써 박싱/언박싱 문제가 해결된다.
  - 제네릭 클래스, 제네릭 메서드가 있다.

* 제네릭 메서드의 경우, 형식 파라미터에 제약 조건을 걸 수 있다.
  - ```
    public class MyClass<T> where T: ICollection
    public class MyType<T> where T: ICollection, IConvertible
    public class Dict<K, V> where K: ICollection
                            where V: IComparable
    ```
  - where 키워드를 사용해 형식 파라미터가 따라야 할 제약 조건을 지정할 수 있다.
  - 위의 경우 외에도 struct (값 형식), class (참조 형식), new() (기본 생성자 필수 포함), U (U 타입 인수) 키워드 등을 이용해 특별한 제약 조건을 걸 수 있음 (where T: [키워드])

* BCL에 적용된 제네릭은 다음과 같다. (가능하면 제네릭 버전 컬렉션을 대신 사용하는 것을 권장함)
  - `ArrayList --> List<T>`
  - `Hashtable --> Dictionary<TKey, TValue>`
  - `SortedList --> SortedDictionary<TKey, TValue>`
  - `Stack --> Stack<T>`
  - `Queue --> Queue<T>`

* 제네릭 버전 인터페이스는 다음과 같다. (가능하면 제네릭 버전 인터페이스를 대신 사용하는 것을 권장함)
  - `IComparable --> IComparable<T>`
  - `IComparer --> IComparer<T>`
  - `IEnumerable --> IEnumerable<T>`
  - `IEnumerator --> IEnumerator<T>`
  - `ICollection --> ICollection<T>`

### ?? 연산자 (null 병합 연산자)

* 피연산자1 ?? 피연산자2
  - 참조 형식의 피연산자1이 null이 아니라면 그 값을 그대로 반환하고, null이라면 피연산자2의 값을 반환한다.

### default 예약어

* 일반적인 변수의 경우, 값 형식은 0으로 참조 형식은 null로 초기화된다.

* 그러나 제네릭 형식의 파라밑로 전달된 경우에는 미리 타입을 알 수 없으므로 초기값을 결정할 수 없다.
  - default 예약어를 사용하면 컴파일러가 T 형식에 따라 자동으로 초기값을 결정할 수 있도록 해준다.
  - default 예약어는 타입을 인자로 받기 때문에 임의로 타입을 지정하는 방식으로도 사용할 수 있다.

### yield return/break

* yield 문법은 IEnumerable/IEnumerator로 구현한 코드에 대한 간편 표기법이라고 볼 수 있다.
  - yield return: 리턴할 때 위치를 기억해 뒀다가 다음에 호출될 때 마지막 yield return 문이 호출됐던 코드 다음 줄부터 실행이 재개된다.
  - yield break: 열거문이 제대로 작동하도록 루프 수행 후 열거를 중지하는 역할을 한다.
  - yield 문법이 적용된 코드는 그대로 실행되는 것이 아니라 C# 컴파일러가 내부적으로 yield 문이 사용된 메서드를 컴파일 시에 IEnumerable이 적용된 것과 같은 코드로 치환한다.
  - 이것은 필수 문법이 아니며, 알아두면 코드를 좀 더 간결하게 작성하는 데 도움이 된다.

### partial 클래스

* partial class 키워드를 사용하면 클래스 정의를 나누어서 할 수 있다.
  - 클래스 정의가 나뉜 코드는 한 파일에 있어도 되고 다른 파일로 나누는 것도 가능하지만 반드시 같은 프로젝트에서 컴파일해야 한다.
  - C# 컴파일러가 빌드 시에 같은 프로젝트에 있는 partial 클래스를 하나로 모아 단일 클래스로 빌드한다.
  - 이 기법은 윈도우 응용 프로그램, 웹 응용 프로그램 개발 시에 주로 사용한다고 한다.

### nullable 형식

* nullable 타입: `System.Nullable<T>` 구조체
  - 일반적인 값 형식에 대해 null 표현이 가능하게 하는 역할을 한다.
  - double? == Nullable<double>
  - hasValue 속성: 값이 할당되어 있으면 True, 할당되어 있지 않으면 False
  - Value: hasValue가 true일 경우 유효한 값이 들어 있다.

### 익명 메서드

* 이름이 없는 메서드로서 델리게이트에 전달되는 메서드가 1회용일 때 유용하게 사용된다.
  - 함수 이름 대신 delegate 키워드를 사용하여 함수 정의를 넣어서 인자로 넘겨준다.
  - 이 문법은 간편 표기법으로 C# 컴파일러가 내부적으로 빌드 시점에 중복되지 않을 특별한 문자열을 하나 생성해 메서드의 이름으로 사용하고 delegate 키워드 다음의 코드를 분리해 해당 메서드의 본체로 넣는다.

### 정적 클래스

* 클래스의 정의에 static 키워드를 사용하여 정의된 정적 클래스는 오직 정적 멤버만을 내부에 포함할 수 있다.
  - BCL 라이브러리에 포함된 System.Math 타입이 대표적이다.
  - Math 타입 클래스는 인스턴스를 여러 개 만들 필요가 없기 때문이다.

## C# 3.0

### var 예약어

* C# 컴파일러에 타입 추론(type inference) 기능이 추가되면서 생긴 문법
  - 자바 스크립트의 동적 타입과 같은 기능
  - 코드가 간결해지는 장점이 있으나 엄격한 타입을 정하지 않을 경우 코드 가독성 저하, 디버깅의 어려움 등이 있을 수 있으므로 권장하지 않음

### 자동 구현 속성

* 자동으로 get, set 함수를 만들어 주는 기능
  - `public string Name { get; get; }`: 이렇게 하면 자동으로 get, set 함수를 만들어 준다.
  - `public string Name { get; protected set; }`: get, set에 서로 다른 접근 제한자를 지정할 수도 있다.

### 개체 초기화 (Object initializers)

* 내부 상태 변수의 개수가 많아질수록 생성자를 여러 개 만들어야 한다.
  - C# 3.0에서는 public 접근자가 명시된 멤버 변수에 한해 new 구문에서 이름과 값을 지정하여 초기화하는 기능을 제공한다.
  - ```
    class Person
    {
        string _name; int _age;

        public string Name { get { return _name; } set { _name = value; }
        public int Age { get { return _age; } set { _age = value; } }
    }

    class Program
    {
        static void Main(string[] args) {
            // 아래의 생성자들은 클래스 선언에 따로 정의되어 있지 않아도 작동한다.
            Person p1 = new Person();
            Person p2 = new Person { Name = "Anders" };
            Person p3 = new Person { Age = 10 };
            Person p4 = new Person { Name = "Anders", Age = 10 };

            // get, set 함수가 없으면 이렇게라도 할 수 있다.
            Person p5 = new Person { _name = "Anders", _age = 10 };
        }
    }
    ```

### 컬렉션 초기화

* 배열 변수처럼 컬렉션 객체를 초기화할 수 있는 문법이 추가되었다.
  - `List<int> numbers = new List List<int> { 0, 1, 2, 3, 4 };  // Add 메서드를 사용하지 않아도 됨`
  - 단, 해당 컬렉션 타입이 반드시 `ICollection<T>` 인터페이스를 구현해야 한다.

### 익명 타입

* C# 2.0에서 익명 메서드가 지원되고, C# 3.0에서는 익명 타입도 지원된다.
  - `var p = new { Count = 10, Title = "Anders" };`
  - 단, 객체의 타입명이 없기 때문에 지역 변수를 선언할 때 var 예약어를 사용해야 한다.

### 부분 메서드

* C# 2.0에서 부분 클래스가 지원되고, C# 3.0에서는 부분 메서드도 지원된다.
  - 단, 코드 분할을 하는 것이 아니라 메서드의 선언부/구현부를 분리할 수 있게만 허용한다.
  - 구현부가 정의되어 있지 않아도 컴파일은 정상적으로 된다.
  - 제약 사항: (1) 리턴 값을 가질 수 없다. (2) ref 파라미터는 사용할 수 있지만 out 파라미터는 사용할 수 없다. (3) private 접근자만 허용된다.
  - 제약 사항이 심하고 부분 클래스도 많이 사용하지 않기 때문에 별로 활용되지는 않는다.

### 확장 메서드 (Extension method)

* 일반적으로 상속을 통해 클래스를 확장하나 2가지 문제점이 있다.
  - sealed로 봉인된 클래스는 확장할 수 없다. (예: BCL의 System.String 타입)
  - 클래스를 상속 받아 확장하면 기존 소스코드를 새롭게 상속 받은 클래스 이름으로 바꿔야 한다.

* 확장 메서드 기능을 사용하면 클래스의 내부 구조를 전혀 바꾸지 않고 마치 새로운 인스턴스 메서드를 정의하는 것처럼 추가할 수 있다.
  - 확장 메서드는 static 클래스에 정의되어야 한다.
  - 확장 메서드는 반드시 static이어야 하고, 확장하려는 타입의 파라미터를 this 키워드와 함께 명시해야 한다.

* 그러나 클래스 상속과 달리 다음 한계점이 있다.
  - 부모 클래스의 protected 멤버 호출이 불가능하다.
  - 부모 클래스의 메서드 재정의(오버라이드)가 불가능하다.

### 람다 식

* C#의 경우 람다 식은 다음과 같이 구별되어 사용된다.
  - 코드로서의 람다 식: 익명 메서드의 간편 표기 용도로 사용됨
    * 자바 스크립트의 화살표 연산자(=>)의 문법과 같다.
    * 다만, 자바 스크립트와 달리 델리게이트로 정의해서 자주 사용하는 람다 식을 델리게이트로 정의해두고 쓸 수 있다. (Action, Func)
  - 데이터로서의 람다 식: 람다 식 자체가 데이터가 되어 구문 분석의 대상이 됨 (메서드로 실행될 수 있음)
    * 중괄호가 없는 람다 식의 경우, 그 자체로 "식을 표현한 데이터"로 사용할 수 있다.
    * 람다 식이 코드가 아니라 System.Linq.Expressions.Expression 타입의 인스턴스 데이터 역할을 하게 된다.
    * `Expression<Func<int, int, int>> exp = (a, b) => a + b;  // 이렇게 하면 람다 식으로 Expression 객체로 다룰 수 있음`
    * Expression 타입과 대응되는 팩터리 메서드를 이용하면, 일반적인 메서드 내부의 C# 코드를 Expression 조합만으로도 프로그램 실행 시점에 만들어 낼 수 있다.

### LINQ

* LINQ (Language Integrated Query)
  - C# 및 VB.NET 컴파일러에서 자주 사용되는 정보의 선택/열거 작업을 일관된 방법으로 다루기 위해 기존 문법을 확장시킨 것이다.
  - 쿼리 문법은 SQL 쿼리의 SELECT 구문과 유사하다.
  - 쿼리 문은 `IEnumerable<T>` 타입으로 저장된다.
  - 이것도 간편 표기법에 지나지 않으며, C# 컴파일러에 의해 빌드 시에 원래의 확장 메서드를 사용하는 코드로 변경되어 컴파일된다.

## C# 4.0

### 선택적 파라미터와 명명된 인수

* 선택적 파라미터: 인자를 전달하지 않아도 미리 지정된 기본값을 사용하는 것을 의미한다. (C++의 디폴트 파라미터 개념과 동일함)
  - ref, out 예약어와 함께 사용할 수 없다.
  - params 타입의 파라미터는 선택적 파라미터가 될 수 없다.
  - 선택적 파라미터의 기본값은 반드시 상수 표현식이어야 한다.

* 명명된 인수: 인자의 값을 받는 인자의 이름을 표기하는 것을 의미하며 코드의 가독성을 높인다. (파이썬의 함수에서 사용하는 기법)
  - `p.Output(age: 5, name: "Tom", address: "Tibet");`

### dynamic 예약어

* 마이크로소프트는 기존의 C#, VB.NET, C++/CLI와 같은 정적 언어 말고도 동적 언어까지도 닷넷과 호환되도록 CLR을 바탕으로 한 DLR(Dynamic Language Runtime) 라이브러리를 내놓았다.
  - 문제는 동적 언어로 만들어진 프로그램의 타입 시스템을 C#과 같은 정적 언어에서 연동하는 방법이 없다는 점이다.
  - 이런 문제를 해결하기 위해 C# 4.0에서 dynamic 예약어를 추가했다.
  - C# 3.0에서의 동적 타입인 var 예약어와 비슷해 보이나 차이가 있다.
  - var 예약어는 빌드 시점에 초기값과 대응되는 타입으로 치환되는 반명, dynamic 변수는 컴파일 시점에 타입을 결정하지 않고 해당 프로그램이 실행되는 시점에 타입을 결정한다.
  - dynamic 예약어는 내부적으로는 CallSite.Target 메서드를 사용하는 간편 표기법에 불과하다.

* dynamic 예약어가 도입됨에 따라 다음 장점을 갖추게 되었다.
  - 리플렉션 개선
  - 덕 타이핑: 동적 언어에서 제공하는 기능으로 서로 다른 타입의 동일한 프로퍼티/메서드를 호출할 수 있게 해준다.
  - 동적 언어와의 타입 연동

### 동시성 컬렉션

* 다중 스레드에서 컬렉션에 접근할 때 동기화를 적용하지 않으면 오류가 발생한다.
  - 일일이 동기화 코드를 추가하는 것은 매우 번거로운 일이다.
  - 그래서 BCL에서는 다중 스레드에서 쉽게 이용할 수 있는 전용 컬렉션을 System.Collections.Concurrent에서 제공하고 있다.
    * `BlockingCollection<T>`: Producer/Consumer 패턴에서 사용하기 좋은 컬렉션
    * `ConcurrentBag<T>`: `List<T>`의 순서가 지켜지지 않는 동시성 버전
    * `ConcurrentDictionary<TKey, TValue>`: `Dictionary<TKey, TValue>`의 동시성 버전
    * `ConcurrentQueue<T>`: `Queue<T>`의 동시성 버전
    * `ConcurrentStack<T>`: `Stack<T>`의 동시성 버전

## C# 5.0

### 호출자 정보

* C#은 C/C++과 달리 매크로 상수를 제공하지 않는다.
  - 매크로 상수에 대한 요구사항을 반영하여 호출자 정보로 구현되었다.
  - 매크로 상수와 같지는 않지만 C#의 특성을 살려 애트리뷰트, 선택적 파라미터의 조합으로 구현되었다.

* 호출자 정보: 호출하는 측의 정보를 메서드의 인자로 전달하는 것을 의미한다. 다음은 C# 5.0에서 제공하는 호출자 정보이다.
  - CallerMemberName: 호출자 정보가 명시된 메서드를 호출한 측의 메서드 이름
  - CallerFilePath: 호출자 정보가 명시된 메서드를 호출한 측의 소스코드 파일 경로
  - CallerLineNumber: 호출자 정보가 명시된 메서드를 호출한 측의 소스코드 라인 번호

### 비동기 호출

* async, await 예약어가 새롭게 추가되었다. (자바 스크립트에서도 지원하는 기능)
  - 이 예약어를 이용하면 비동기 호출을 마치 동기 방식처럼 호출하는 코드를 작성할 수 있다.
  - async를 메서드 앞에 붙여 주어야, 메서드 내부에서 await 키워드를 인지한다.
  - 비동기 호출은 파일 입출력, 네트워크 통신 등 CPU 연산에 비해 시간이 오래 걸리는 작업을 할 때 유용하며 동기 호출과 달리 대기 시간이 발생하지 않는다.

## C# 6.0

### 자동 구현 속성의 초기화 구문 추가

* C# 3.0의 "자동 구현 속성"을 사용한 경우, 초기값을 부여하려면 별도로 생성자 등의 메서드를 구현해야만 했다.
  - C# 6.0에서는 자동 구현 속성 초기화 구문을 제공하여 속성 정의 구문에서 직접 기본값을 지정할 수 있게 하였다.
  - ```
    class Person
    {
        public string Name { get; set; } = "Jane";    // set을 제거하면 읽기 전용 속성이 된다.
    }
    ```

### 표현식(람다식)을 이용한 메서드, 속성 및 인덱서 정의

* 메서드가 식(expression)으로 이루어진 경우 간략하게 표현식으로 구현할 수 있다.
  - `public Vector Move(double dx, double dy) => new Vector(x + dx, y + dy);`
  - `public void PrintIt() => Console.WriteLine(this);`
  - `public override string ToString() => string.Format("x = {0}, y = {1}", x, y);`

* 속성(프로퍼티) 정의에도 표현식을 적용할 수 있다.
  - `public double Angle => Math.Atan2(y, x);`
  - 단, 속성 정의에 대해 람다 식을 구현하면 읽기 전용 필드가 된다.

* 인덱서 구문에도 표현식을 적용할 수 있다.
  - `static double RadianToDegree(double angle) => angle * (180.0 / Math.PI);`
  - 속성(프로퍼티)과 마찬가지로 읽기 전용 인덱서로만 동작하게 된다.

* 생성자/종료자, 이벤트의 add/remove 접근자의 경우 메서드이기는 하지만 표현식을 이용한 구현은 불가능하다.

### using static 구문을 이용한 타입명 생략

* 기존에는 static 멤버를 사용할 때 반드시 타입명과 함께 써야 했다.
  - `Console.WriteLine("문자열 출력");`
 
* 그러나 C# 6.0부터는 자주 사용하는 타입의 전체 이름(FQDN)을 using static으로 선언해 두면, 타입명을 생략할 수 있게 되었다.
  - ```
    using static System.Console;
    ...
    WriteLine("문자열 출력");
    ```

* 단, C# 3.0에 도입된 "확장 메서드" 기능의 경우에도 static 키워드를 사용하기 때문에 문법적 모호성 문제로 using static 적용을 받지 않으므로 타입명을 생략하면 오류가 발생한다.

### null 조건 연산자

* null 조건 연산자: 참조 변수의 값이 null이라면 그대로 null을 리턴하고, null이 아니라면 지정된 멤버를 호출한다.
  - 이것을 잘 활용하면 null 값을 확인하는 if 문 사용을 대폭 줄일 수 있다.
  - `list?.Count`: list가 null이 아닐 경우 list.Count 멤버 변수의 값을 리턴하고, null이면 null을 리턴한다.

### 문자열 내에 식(expression) 포함

* 기존에는 문자열과 변수의 값을 조합해서 출력하려면 다음 방법을 사용해야 했다.
  - `return "이름: " + Name + ", 나이: " + Age;`
  - `return string.Format("이름: {0}, 나이: {1}", Name, Age);  // string.Format을 이용한 방법`

* C# 6.0에서는 string.Format을 사용하지 않고도 다음과 같이 표현할 수 있다.
  - `return $"이름: {Name}, 나이: {Age}";`
  - 만약 중괄호를 출력하고 싶으면 두 번 연이어 입력해야 한다. (`return $"{{이름: {Name}, 나이: {Age}}}";`)

### nameof 연산자

* C# 코드에 사용된 식별자를 이름 그대로 출력하고 싶을 때 다음과 같이 하면 된다.
  - `$"{nameof(name)} == {name}"`
  - 코드 내에서 식별자 이름을 하드코딩할 필요가 없게 되었다.
  - 리플렉션은 코드가 실행되어야 이름을 구할 수 있지만, nameof는 C# 6.0 컴파일러가 컴파일 시점에 문자열로 직접 치환해 주므로 실행 시점에 부하가 없다.

### Dictionary 타입의 인덱스 초기화

* 컬렉션 Dictionary 타입의 기존 초기화 문법은 다음과 같다.
  - ```
    var weekends = new Dictionary<int, string>
    {
        { 0, "Sunday" },
        { 6, "Saturday" },
    };
    ```

* C# 6.0의 컬렉션 Dictionary 타입의 초기화 문법은 키/값 개념에 맞게 직관적으로 바뀌었다.
  - ```
    var weekends = new Dictionary<int, string>
    {
        [0] = "Sunday",
        [6] = "Saturday",
    };
    ```
  - 참고로 키 값이 문자열이면 `["Key"] = ...` 식으로 입력하면 된다.

### 예외 필터

* 비주얼 베이직, F# 언어에서 지원하던 예외 필터를 사용할 수 있게 되었다.
  - ```
    try
    {
        // ...[코드]...
    } catch (예외_타입 e) when (조건식)
    {
        // ...[코드]...
    }
    ```
  - catch에 지정된 예외_타입에 속하는 예외가 try 블록 내에서 발생했을 때, 조건식이 true로 평가된 경우에만 해당 예외 처리기가 선택된다.
  - 조건식에는 메서드도 들어갈 수 있다.
  - 기존 예외 처리 구문의 경우, 동일한 예외 타입의 catch 구문을 여러 개 둘 수 없었지만, 예외 필터를 사용하면 이것이 허용된다.

### 컬렉션 초기화 구문에 확장 메서드로 정의한 Add 지원

* "컬렉션 초기화"에서 설명한 구문이 컴파일되려면 `ICollection<T>` 인터페이스를 구현해야 한다.
  - C# 6.0에서는 `ICollection<T>` 인터페이스가 없다면 Add 메서드가 확장 메서드로도 구현되어 있는지 다시 한 번 더 찾는 기능을 추가했다.

### 기타 개선 사항

* C# 5.0에서 C# 6.0으로 바뀌면서 개선된 기능은 다음과 같다.
  - catch/finally 블록 내에서 await 사용 가능
  - #pragma의 'CS' 접두사 지원
  - 재정의된 메서드의 선택 정확도를 향상

## C# 7.0

### 더욱 편리해진 out 파라미터 사용

* C# 7.0 이전에는 out 파라미터가 정의된 메서드를 사용하려면 반드시 인자로 전달될 인스턴스를 미리 선언해야 했다.
  - ```
    int result;
    int.TryParse("5", out result);
    ```

* C# 7.0부터는 변수 선언 없이 변수의 타입과 함께 out 키워드를 쓸 수 있다.
  - `int.TryParse("5", out int result);`
  - 타입 추론을 컴파일러에게 맡기는 var 키워드도 사용할 수 있다. (out var result)
  - 심지어 값을 무시하는 구문(discard)까지 추가되어 값이 필요하지 않은 상황에 대해서는 변수명까지 생략할 수 있게 되었다. (`int.TryParse("5", out _);`)

### 리턴값 및 로컬 변수에 ref 기능 추가

* C# 7.0 이전까지는 ref 키워드를 오직 메서드의 파라미터로만 사용할 수 있었다.

* C# 7.0부터는 로컬 변수, 리턴값에 대해서도 참조 관계를 맺을 수 있게 개선되었다.
  - 로컬 변수의 경우
    ```
    int a = 5;
    ref int b = ref a;  // 이렇게 하면 a와 b가 동일한 메모리를 공유하게 된다.
    ```
  - 리턴값의 경우 (총 네 곳에서 ref 키워드를 명시해야 함)
    ```
    ref int item = ref intList.GetFirstItem();
    ...
    public ref int GetFirstItem()
    {
        return ref list[0];
    }
    ```
  - 제약 사항은 다음과 같다.
    * 지역 변수를 return ref로 리턴해서는 안 된다.
    * ref 키워드를 지정한 지역 변수는 다시 다른 변수를 가리키도록 변경할 수 없다. (C# 7.3에서 이 제약 사항이 제거됨)

### 튜플

* 튜플: 유한 개의 원소로 이루어진 정렬된 리스트
  - 이것을 이용하면 메서드에서 인자를 받거나 값을 리턴할 때 여러 개의 값을 한 번에 전달할 수 있다. (리턴 값, 인자 모두 튜플 타입이 가능함)
  - 괄호를 이용해 다중 값을 처리할 수 있는 구문을 지원하게 되었다.
  - ```
    (bool, int) result = pg.ParseInteger("50");
    ...
    (bool, int) ParseInteger(string text)
    {
        ...
        return (result, number);
    }
    ```
  - 튜플을 리턴하는 메서드가 지정한 튜플의 이름들을 원하지 않거나 이름이 지정되지 않은 튜플인 경우 호츨하는 측에서 강제로 이름을 지정하는 것도 가능하다. (`(bool success, int n) result = pg.ParseInteger("50");`)
  - 심지어 튜플로 받지 않고 개별 필드를 분해해서 받는 구문도 지원한다. (`(var success, var number) = pg.ParseInteger("50");`)
  - 또한 out 파라미터 처리에서 지원했던 생략 기호도 튜플의 리턴값을 분해하는 구문에 사용할 수 있다. (`(var _, var n) = pg.ParseInteger("70");`)
  - 2개의 변수 값을 교환하는 Swap 함수 같은 기능도 튜플을 사용하면 간단하게 구현할 수 있다. (`(a, b) = (b, a);`)

* 메서드의 인자와 리턴에 사용한 모든 튜플 구문은 C# 7.0 컴파일러가 소스코드를 컴파일하는 시점에 System.ValueTuple 제네릭 타입으로 변경해서 처리한다.
  - 기존의 System.Tuple은 참조 형식이지만 System.ValueTuple은 값 형식이다.

### Deconstruct 메서드

* 커스텀 타입에 Deconstruct 메서드를 1개 이상 정의하여 튜플의 리턴 값을 분해하는 구문을 구현할 수 있다.
  - 분해가 되는 개별 값을 out 파라미터를 이용해 처리하면 된다.
  - 문법: 접근_제한자 void Deconstruct(out T1 x1, ..., out Tn xn) { ... }
  - out 파라미터이므로 반드시 값을 채워서 리턴해야 함
  - ```
    class Rectangle
    {
        ...
        public void Deconstruct(out int x, out int y, out int width, out int height) { ... }
    }
    ...
    (var _, var _, int width, int height) = rect;
    ```

### 람다 식을 이용한 메서드 정의 확대

* C# 6.0의 "표현식(람다식)을 이용한 메서드, 속성 및 인덱서 정의"에서 람다 식으로 메서드의 정의가 가능했던 유형은 다음과 같다.
  - 일반 메서드
  - 프로퍼티의 get 접근자 (읽기 전용)
  - 인덱서의 get 접근자 (읽기 전용)

* C# 7.0부터는 다음의 메서드 정의까지 람다 식으로 정의가 가능하다.
  - 생성자
  - 종료자
  - 이벤트의 add/remove
  - 프로퍼티의 set 접근자
  - 인덱서의 set 접근자

### 로컬 함수

* 로컬 함수 문법: 메서드 안에서만 호출 가능한 메서드를 1개 이상 정의할 수 있다.
  - 문법은 메서드 정의와 완전히 같고 단지 다른 메서드의 내부에서 정의한다는 차이점만 있다.

### 사용자 정의 Task 타입을 async 메서드의 리턴 타입으로 사용 가능

* 일반적으로 async 키워드가 붙은 메서드는 리턴 타입이 반드시 `void`, `Task`, `Task<T>` 중 하나로 알려져 있다.

* C# 7.0에서는 비동기 메서드에서 그 외의 타입도 리턴할 수 있게 되었다. (`ValueTask<T>` 타입)
  - 기존 `Task` 리턴 타입의 async 메서드는 모든 경우에 `Task` 객체를 생성해 리턴하였다.
  - `ValueTask`는 async 메서드 내에서 await를 호출하지 않은 경우라면 불필요한 `Task` 객체 생성을 하지 않음으로써 성능을 높인다.

### 자유로워진 throw 사용

* throw 구문은 제어문과 마찬가지로 식(expression)이 아닌 문(statement)에 해당한다.
  - 이전에는 표현식에서 throw를 사용하는 것에 제한이 있었다.
  - C# 7.0부터는 throw를 표현식에서도 사용할 수 있게 되었다.
  - 그러나 throw가 표현식으로 완전히 바뀐 것은 아니기 때문에 표현식이 허용되는 모든 곳에서 사용할 수는 없다.

### 리터럴에 대한 표현 방법 개선

* 숫자가 길어지면 가독성이 길어진다.
  - C# 7.0부터 숫자 내 임의의 위치에 밑줄을 추가할 수 있도록 허용하고 있다.
  - `int number = 10_000_000;  // 이것은 10진수, 16진수, 2진수에도 적용 가능함`
  - 값에는 영향을 미치지 않으며 순수하게 가독성을 높이기 위한 기능이다.

### 패턴 매칭

* C# 7.0부터 추가된 패턴 매칭 유형은 다음과 같다.
  - 상수 패턴
  - 타입 패턴
  - var 패턴

* is 연산자의 패턴 매칭
  - is 연산자는 기존 기능애서 패턴 매칭을 지원하기 위해 as 연산자 기능을 흡수했다.
  - 기존의 is 연산자는 변환 여부만 알 수 있었고 as 연산자는 변환 결과를 포함하고 있었는데, 이제는 is 연산자가 as 연산자와 동일한 역할을 수행할 수 있다.
  - 물론 기존의 is 연산자처럼 타입만 비교하는 것도 여전히 가능하다.

* switch/case 문의 패턴 매칭

## C# 7.1

### Main 메서드에 async 예약어 허용

* C# 7.1부터는 Main 메서드에도 async를 허용하였다.
  - 람다 식으로도 Main 메서드를 구현할 수 있다.

* 가능한 Main 메서드 정의는 다음과 같다.
  - `static async Task Main()`
  - `static async Task Main(string[])`
  - `static async Task<int> Main()`
  - `static async Task<int> Main(string[])`

### default 리터럴 추가

* C# 7.1부터는 default 예약어가 타입 추론이 가능해져서 리터럴 형식으로 쓸 수 있게 바뀐다.
  - C# 컴파일러 입장에서는 default 대상이 되는 타입을 추론할 수 있으므로 굳이 타입을 지정할 필요가 없다.
  - 제네릭 인자에도 default 리터럴을 쓸 수 있다.

### 타입 추론을 통한 튜플의 변수명 자동 지정

* C# 7.1부터는 튜플의 변수명에 대해서도 타입 추론을 활용해 사용의 편의성을 높였다.

### 기타 개선 사항

* C# 7.0에서 C# 7.1으로 바뀌면서 개선된 기능은 다음과 같다.
  - 패턴 매칭 - 제네릭 추가
  - 참조 전용 어셈블리 (Ref Assemblies)

## C# 7.2

### 메서드의 파라미터에 in 변경자 추가

* 메서드의 파라미터로 ref, out 키워드가 있었는데 C# 7.2부터는 in 키워드가 추가되었다.
  - ref 키워드를 사용하면 값 복사 부하는 없어지지만, 원본 값도 같이 변경되는 부작용이 있다.
  - 그래서 ref와 readonly 의미를 모두 갖는 in 키워드를 추가했다.

### 읽기 전용(readonly) 구조체

* 기존의 readonly 프로퍼티의 경우, 직접 변경하는 것은 불가하나 메서드 호출을 통해 간접적인 변경은 허용한다는 문제점이 있었다.
  - 그러나 메서드 호출을 통해 변경할 때 오류가 발생하지도 않고, 실제로 값은 변경되지 않는 현상이 발생한다.
  - C# 컴파일러의 방어 복사본(defensive copy) 처리 메커니즘은 개발자가 스스로 인지하기 어려워서 버그를 야기할 수 있다.
  - readonly struct는 구조체 자체를 읽기 전용으로 만들어 해결하였다.
  - 읽기 전용 구조체는 타입 내의 멤버 변수들을 모두 읽기 전용으로 강제한다. (모든 멤버는 readonly 키워드를 붙여야 함)
  - C# 컴파일러가 방어 복사본(defensive copy) 처리를 하지 않으므로 성능이 개선되었다.

### 메서드의 리턴 값 및 로컬 변수에 ref readonly 추가

* C# 7.2부터는 ref 키워드가 메서드 인자뿐만 아니라 리턴값, 로컬 변수에도 사용 가능하게 되었다.

### 스택에만 생성할 수 있는 값 타입 지원 - ref struct

* 값 형식의 struct는 스택을 사용하지만, 그 struct가 class 안에 정의되어 있는 경우 힙에 데이터가 위치하게 된다.

* ref struct는 값 형식을 오직 스택에만 생성할 수 있도록 강제하는 방법이다.
  - 스택에만 생성할 수 있으므로 로컬 변수, 메서드의 리턴 및 인자로 전달하는 것은 가능하다.
  - 다른 ref struct 타입의 필드로 정의할 수도 있다.
  - 그 외에 주요한 제약 사항으로 인터페이스를 구현할 수 없다.
  - 또 using 문의 대상으로 사용할 수 없다.

* 이러한 특수 타입이 나온 주된 이유는 C# 응용 프로그램의 성능을 최대한 높일 수 있도록 새롭게 도입한 `Span<T>`를 위해 꼭 필요했기 때문이다.
  - `Span<T>` 타입은 내부적으로 관리 포인터를 사용한다.
  - 관리 포인터는 절대 관리 힙에 놓일 수 없는 제약이 있기 때문에 `Span<T>` 타입을 구현하면서 관리 포인터를 담을 수 있는 특수 구조체로 ref struct가 도입되었다.
  - `Span<T>`와 더불어 가비지 컬렉터의 사용을 줄여 성능 향상을 가져온다.

### 신규 추가 타입: `Span<T>`

* `Span<T>`: 제네릭 관리 포인터를 가진 readonly ref struct
  - 배열에 대한 참조 뷰를 제공하는 타입이라고 볼 수 있다.
  - 기본적으로 C#에서 만드는 모든 배열을 `Span<T>` 타입으로 가리킬 수 있다.
  - 무분별한 힙의 사용을 최소화할 수 있고 이로 인해 가비지 컬렉터의 사용을 줄여 자연스럽게 성능 향상을 가져온다.
  - 예외 처리기에서도 힙의 경우 catch/finally 절이 실행되지 않지만, `Span<T>` 타입으로 감싼 경우 예외 처리가 가능하다는 장점이 있다.

### 3항 연산자에 ref 지원

* C# 7.2부터는 로컬 변수의 ref 키워드의 사용을 3항 연산자에도 적용할 수 있게 되었다.

### private protected 접근자 추가

* 접근 제한자가 5개(public, internal, protected, internal protected, private)였는데, C# 7.2부터 private protected가 추가되었다.
  - private protected는 private 접근자의 적용과는 아무런 상관이 없다.
  - 오히려 internal protected와 비슷하다.
    * internal protected: 동일 어셈블리 내에서 정의된 클래스이거나 다른 어셈블리라면 파생 클래스인 경우에 한해 접근을 허용한다. 즉 internal __또는__ protected 조건이다.
    * private protected: 동일 어셈블리 내에서 정의된 파생 클래스인 경우에 한해 접근을 허용한다. 즉 internal __그리고__ protected 조건이다.

### 숫자 리터럴의 선행 밑줄

* C# 7.0의 "리터럴에 대한 표현 방법 개선"에서 숫자형 리터럴에 밑줄을 쓰는 것이 가능했지만, 리터럴 접두사(0x, 0b)가 있는 경우 밑줄이 바로 나올 수 없다는 제약이 풀렸다.

### 뒤에 오지 않는 명명된 인수

* C# 4.0에 추가된 "명명된 인수"는 일단 파라미터의 이름을 명시하면 이후의 인자들은 모두 이름을 명시해야 하는 제약이 있다.
  - C# 7.2부터는 이렇게 뒤에 오지 않는 명명된 인수를 정상적으로 컴파일한다.
  - `p.Output(name: "Tom", 16, address: "Tibet");`

## C# 7.3

### 신규 제네릭 제약 조건 - Delegate, Enum, unmanaged

* 제네릭의 제약 조건으로 타입을 사용하려면 다음 조건을 만족해야 한다.
  - 클래스 타입이어야 한다.
  - sealed 타입이 아니어야 한다.
  - System.Array, System.Delegate, System.Enum은 허용하지 않는다.
  - System.ValueType은 허용하지 않지만 특별히 struct 제약을 대신 사용할 수 있다. 또한 System.Object도 허용하지 않지만 어차피 모든 타입의 기반이므로 제약 조건으로써의 의미가 없다.

* C# 7.3에서 System.Delegate, System.Enum은 제약 조건에서 풀리게 된다.

* 마지막 제약 조건으로 기존 strcut 제약의 좀 더 특수한 사례에 속한 unmanaged가 있다.
  - 이를 이용하면 struct 제약 중에서 대상 타입이 참조 형식을 필드로 갖지 않는다는 보장을 하나 더 해준다.
  - 따라서 기존에는 불가능했던 형식 파라미터에 대한 포인터 연산을 할 수 있다.

### 사용자 정의 타입에 fixed 적용 가능

* fixed 키워드를 그 대상이 기본형이거나 그것의 배열 또는 string으로 제한되었다.
  - 사용자가 만든 타입은 fixed의 대상이 될 수 없다.
  - C# 7.3부터 사용자 타입이 GetPinnableReference라는 이름으로 관리 포인터를 리턴하는 메서드를 포함하고 있는 경우라면 fixed 구문에 자연스럽게 사용할 수 있도록 통합되었다.
  - `Span<T>` 타입은 GetPinnableReference를 구현하고 있으므로 `Span<T>` 타입에 fixed 키워드를 사용할 수 있다.

### 힙에 할당된 고정 크기 배열의 인덱싱 개선

* C# 7.3부터는 힙에 할당된 경우일지라도 일관성 있게 fixed 없이 고정 크기 배열에 대한 인덱싱이 가능하다.

### 초기화 식에서 변수 사용 가능

* C# 7.2까지는 다음 4가지 유형에서 변수를 허용하지 않았다.
  - 필드 초기화 식
  - 프로퍼티 초기화 식
  - 생성자 초기화 식
  - LINQ 쿼리 식

* 원칙적으로 변수 선언은 문(statement)에 해당하기 때문에 식(expression)을 요구하는 코드에 사용할 수 없다.
  - 그러나 out 키워드를 갖는 메서드 호출이나 패턴 매칭에서의 변수명 선언이 발생하는 코드에서도 오류가 발생하므로 표현의 제약을 가져오는 문제로 부각되었다.
  - 그래서 위 4가지 유형에 대해 변수를 허용하게 되었다.

### 자동 구현 속성의 특성 지원

* 애트리뷰트는 "자동 구현 속성"에 대해 지정하는 것이 불가능했지만 C# 7.3부터는 가능해졌다.

### 튜플의 ==, != 연산자 지원

* 튜플 구문에 대해서도 ==, != 연산자가 지원된다.

### ref 지역 변수의 재할당 가능

* "리턴값 및 로컬 변수에 ref 기능 추가"에서 ref 로컬 변수인 경우 기존에는 다른 변수를 재할당하는 것이 불가능했으나 C# 7.3부터는 가능해졌다.

### stackalloc 배열의 초기화 구문 지원

* "스택을 이용한 값 형식 배열: stackalloc"에서 다룬 스택 배열에 대한 초기화 구문을 C# 7.3부터 지원한다.

## C# 8.0

### #nullable 지시자와 nullable 참조 형식

* 닷넷 프로그램을 개발하면 종종 접하게 되는 예외가 바로 System.NullReferenceException이다.
  - 이 신규 문법에서는 컴파일러 수준에서 null 참조 예외가 없도록 보장하는 것이 목표이다.

* 참조 타입의 사용 유형은 2가지가 있으며, C# 컴파일러는 이렇게 대응한다.
  - 해당 인스턴스가 null일 필요가 없는 참조 형식 (Non-nullable reference type) --> 참조 타입을 정의할 때 null 값을 담는 멤버가 없도록 보장함
  - 해당 인스턴스가 null일 수 있는 참조 형식 (Nullable reference type) --> 참조 타입의 인스턴스를 사용할 때 반드시 null 체크를 하도록 보장함

* C# 컴파일러에서 (런타임이 아닌) 컴파일 타임에 null 참조 예외를 어떻게 막을 수 있을까?
  - #nullable 지시자를 이용해 해당 소스코드 파일에 null 값일 수 있는 타입이 정의되지 않도록 보장한다.
    * #nullable [옵션]: enable이면 null 가능성이 있을 경우 경고를 발생시키고, disable이면 null 가능성 체크를 하지 않는다. (닷넷 7부터는 enable이 기본값임)
  - null일 수 있다면 해당 인스턴스를 null 가능한 타입이라고 명시한다.
    * `참조_타입?`: 참조_타입에 물음표를 붙여 인스턴스가 null일 수도 있음을 명시한다.
    * 이렇게 하면 컴파일러가 해당 멤버가 사용된 코드를 검사해 null 가능성이 있다고 경고를 발생시킨다.
  - 개발자가 명시적으로 null 체크를 위한 메서드를 만들었다면, C# 컴파일러에 의해 null 체크에 해당하는 코드라고 인식하도록 NotNullWhen 애트리뷰트를 적용할 수 있다.
    * `static bool IsNull([NotNullWhen(false)] string? value)`: 이 경우 IsNull 메서드가 false를 리턴하면 null이라고 C# 컴파일러가 인지함
    * NotNullWhen 애트리뷰트 외에도 null 처리 관련 힌트를 부여하는 애트리뷰트가 다수 존재한다: AllowNull, DisableNull, DoesNotReturn, DoesNotReturnIf, MaybeNull, MaybeNullWhen, NotNullIfNotNull

* null 체크 코드를 추가하지 않고 null 자체를 개발자가 감수하기로 했다면 null 포기 연산자를 사용하여 #nullable enable 경고를 무시할 수도 있다.
  - `return person.Name!.Length;  // 이 경우 person.Name의 값이 nullable이어도 경고하지 않음`

* nullable 문맥 제어
  - 주석 문맥 (annotation context)
    * enable
      - 모든 참조 타입은 null이 가능하지 않은 참조 타입으로 취급하고 따라서 null 예외 없이 안전하게 접근 가능
      - null 가능한 참조 타입(예: string?)을 사용할 수 있고, 해당 변수에 접근할 때 정적 분석기에 의해 null일 수 있다면 경고 발생
    * disable
      - null 가능한 참조 타입을 사용할 수 없음(참조 타입에 ?를 붙이면 경고 발생)
      - 모든 참조 변수는 null일 수 있음
      - 참조 변수를 접근해도 경고가 발생하지 않음
  - 경고 문맥 (warning context)
    * enable
      - null 접근으로 분석된 경우 경고를 발생시킨다. 주석 문맥의 활성화와 상관 없이 정적 분석기의 판정에 따른다.
    * disable
      - 경고를 발생시키지 않는다.

* 각각의 문맥 제어는 #nullable과 #pragma warning 지시자를 이용해 켜고 끌 수 있지만 매번 소스코드에 지정하는 것이 불편하므로 프로젝트 파일의 Nullable 노드를 통해 전역적으로 설정하는 것이 가능하다.
  - ```
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>net7.0</TargetFramework>
        <Nullable>enable</Nullable>
      </PropertyGroup>
    </Project>
    ```
  - 주석 | 경고 | 지시자 | 프로젝트 설정
    ---- | --- | ------ | ---------------
    enable | enable | #nullable enable | `<Nullable>enable</Nullable>`
    enable | disable | (불가능) | `<Nullable>annotations</Nullable>`
    dsiable | enable | (불가능) | `<Nullable>warnings</Nullable>`
    disable | disable | #nullable disable | `<Nullable>disable</Nullable>`

### 비동기 스트림

* 여기서 비동기 스트림은 IEnumerable/IEnumerator의 비동기 버전이다.
  - 메서드가 async를 지원하더라도 동기 버전 IEnumerable/IEnumerator를 사용하면 성능 저하가 발생한다.
  - 따라서 비동기 버전 IEnumerable/IEnumerator인 IAsyncEnumerable/IAsyncEnumerator가 추가되었다.

### 새로운 연산자 - 인덱스, 범위

* C# 8.0에 새로 추가된 2개의 연산자가 있다.
  - 연산자 | 문법 | 의미
    ------ | --- | -----
    ^ | ^n | 인덱스 연산자로서 뒤에서부터 n번째 위치를 의미함 (주의: 마지막 위치가 1에서 시작함)
    .. | n1..n2 | 범위 연산자로서 n1은 포함하고 n2는 포함하지 않는 범위를 지정한다. 수학적으로 표현하면 [n1, n2)와 같다. n1, n2은 생략 가능하다.

### 간결해진 using 선언

* IDisposable 인터페이스를 구현한 타입의 Dispose 메서드를 finally 구문에서 호출하도록 변경해 주는 using 문은 사용하기 편리하지만 블록이 추가되어 들여쓰기 구간이 발생한다.
  - C# 8.0에서는 들여쓰기를 생략할 수 있도록 개선된 문법을 제공한다.
  - 이 경우 using 블록은 using에 사용된 변수 선언을 기준으로 가장 가까운 바깥 블록까지 적용된다.

### Dispose 호출이 가능한 ref struct

* "스택에만 생성할 수 있는 값 타입 지원 - ref struct"에서 ref struct 특성으로 인해 인터페이스를 구현할 수 없고 이로 인해 using 문에 사용할 수 없었다. (C# 7.2)
  - 그래서 Dispose가 필요한 작업인데도 IDisposable을 구현할 수 없어 using 문에 사용하는 것이 불가능하다.
  - C# 8.0에서는 특별히 ref struct 타입에 한해서만 public void Dispose() 메서드를 포함한 경우 using 문에서 사용할 수 있도록 허용한다.

### 정적 로컬 함수

* "로컬 함수"는 static 함수를 구현할 수 없었지만 C# 8.0에서 제약이 풀렸다.

### 패턴 매칭 개선

* 패턴 매칭에 대한 지원이 추가되었다.
  - switch 식
  - 프로퍼티 패턴
  - 튜플 패턴
  - 위치 패턴
  - 재귀 패턴

### 기본 인터페이스 메서드

* C# 8.0에서는 인터페이스의 메서드에 구현 코드를 추가할 수 있게 되었다.
  - 유의할 점: 상속 받은 클래스에서 기본 인터페이스 메서드를 구현하지 않았다면, 그 메서드는 반드시 인터페이스로 형 변환해서 호출해야만 한다.
  - 다중 상속에서 발생하는 다이아몬드 문제에 대한 모호한 호출 문제를 해결할 수 있다.

### ??= (널 병합 할당 연산자)

* `변수 ??= 기본값`: 참조 객체인 변수의 값이 null이면 기본값을 변수에 대입한다.
  - 이것은 ??와 = 연산자의 복합 연산자에 불과하다. (`txt = txt ?? "test";` 이것은 `txt ??= "test";`와 같다)

### 문자열 @, $ 접두사 혼합 지원

* C# 6.0에 추가된 $ 접두사는 문자열 내에 식을 사용하도록 허용한다.
  - 여기서 @ 접두사와 혼용하는 경우 반드시 $@ 순서로 작성해야 한다.
  - C# 8.0부터는 제약이 풀려서 순서에 상관없이 정상적으로 컴파일된다.

### 기본 식으로 바뀐 stackalloc

* "스택을 이용한 값 형식 배열: stackalloc"에서 본 stackalloc 키워드는 지역 변수를 초기화하는 구문에만 한정되어 있었다.
  - C# 7.2의 `Span<T>` 타입이 나오면서 좀 더 자유롭게 사용할 수 있어야 한다는 요구사항이 반영되어 stackalloc은 식(expression)이 되었다.

### 제네릭 구조체의 unmanaged 지원

* 제네릭 구조체의 경우 내부 필드가 참조 객체를 포함하는지 여부와 상관없이 포인터 관련 연산을 지원하지 않았다.
  - C# 8.0부터는 제네릭 구조체에도 포인터 관련 연산이 가능해졌다.
  - 비관리 메모리로 할당 받은 경우 GC에 부하를 주지 않는다는 장점이 있다.

### 구조체의 읽기 전용 메서드

* "읽기 전용(readonly) 구조체"에서는 방어 복사본 문제로 인한 성능 손실을 없애기 위해 구조체 내의 모든 필드를 readonly로 바꾸도록 강제했다.
  - 그러나 원하는 메서드에 대해서만 상태 변경을 하지 않는다고 보장하면 구조체 자체의 정의를 readonly struct로 만들지 않아도 된다.
  - C# 8.0에서는 읽기 전용 메서드를 추가하여 구조체 전체를 읽기 전용으로 강제하지 않아도 되게끔 조건을 완화하였다.

## C# 9.0

### 레코드

* C# 9.0에서는 값을 담는 용도의 구조체에 대해 record 키워드를 넣으면 기본 메서드 구현을 모두 제공하는 클래스로 바꿔준다.
  - `public record Point` --> `public class Point`로 바꿔주며 Equals, GetHashCode, ==, != 등의 메서드가 자동으로 추가된다.

* 새로 추가된 문법 2가지가 있다. (개인적으로 캡슐화, 정보 은닉의 특성에 위배되는 것이 아닌가 싶다)
  - init 설정자 추가
    * readonly struct와 달리 클래스는 불변 타입을 개발자가 직접 구현해야 했다. (해당 필드를 외부에서 접근할 수 없으므로 생성자 구현이 필요함)
    * init 설정자를 사용하면 private 멤버라도 외부에서 초기화 구문으로 초기화를 할 수 있다.
    * 덕분에 개발자는 필드 초기화를 위한 생성자, 튜플과의 연동을 위한 Deconstruct 메서드도 만들 필요가 없다.
  - with 초기화 구문 추가
    * with 키워드를 이용하면 private 멤버의 값을 변경하는 별도의 메서드가 없어도 자유롭게 불변 개체의 값을 변경하는 인스턴스를 만들 수 있다.

### 대상에 따라 new 식 추론

* 변수의 타입에 따라 new 연산자의 대상 타입을 생략하도록 허용한다.
  - var 키워드처럼 new 키워드 다음에 타입을 지정하지 않아도 자동으로 타입을 결정한다.

### 달라진 조건식 평가

* 조건 연산자(?:)의 식 평가에도 타입 추론 기능이 관여되어 개선이 이루어졌다.
  - 형 변환 없이도 컴파일이 가능해졌다.

### 로컬 함수에 특성 지정 가능

* "로컬 함수"에도 애트리뷰트를 부여할 수 있게 되었다.

* 또한 로컬 함수로 extern 유형을 정의할 수 있게 되었다.

### 익명 함수 개선

* 정적 익명 함수
  - 익명 메서드 및 람다 메서드를 정적으로 정의하는 것이 가능해졌다.
 
* 익명 함수의 파라미터 무시
  - 원래 밑줄만으로 구성한 변수명이나 메서드 이름을 짓는 것이 가능하다.
  - 단, 메서드의 파라미터가 2개 이상 밑줄을 사용하면 중복 이름으로 평가되어 컴파일 오류가 발생했으나 C# 9.0부터는 밑줄을 식별자가 아닌 무시 구문으로 다루게 되어 정상적으로 컴파일이 된다.

* C# 9.0 이상에서 가능한 메서드별 구현 차이점
  메서드 종류 | 파라미터 무시 | static | 애트리뷰트
  ----------- | ----------- | ------ | ------------
  일반 메서드 | X | O | O
  익명 메서드(C# 2.0) | O (C# 9.0) | O (C# 9.0) | X
  람다 메서드(C# 3.0) | O (C# 9.0) | O (C# 9.0) | O (C# 10)
  로컬 함수(C# 7.0) | X | O (C# 8.0) | O (C# 9.0)

### 최상위 문

* C# 9.0부터 도입된 최상위 문의 기능으로 코드를 단 한 줄로 요약하는 것이 가능해졌다.
  - 예: `System.Console.WriteLine("Hello World!");`
  - 별도의 타입 및 메서드를 정의하지 않고도 컴파일이 된다. (C# 컴파일러가 자동으로 임시 타입과 Main 메서드를 생성함)

### 패턴 매칭 개선

* 패턴 일치 문법에 다음 3가지가 추가되었다.
  - 패턴에 타입명만 지정 가능
  - 프리미티브 타입에 한해 상수 값에 대한 `<`, `<=`, `>`, `>=` 관계 연산 가능
  - 논리 연산자(not, and, or)를 이용해 패턴 조합 가능

### 모듈 이니셜라이저

* C# 언어 수준에서 제공하지 않은 닷넷 런타임 기능으로 <Module>이라는 특별한 타입이 있다.
  - CLR이 닷넷 모듈을 로드한 후 거기에 정의된 정적 생성자를 호출하면, 사용자 코드에서 호출하지 않아도 자동으로 실행되는 코드를 정의할 수 있다.
  - C# 9.0부터는 ModuleInitializer라는 애트리뷰트를 정적 메서드에 부여하면 C# 컴파일러가 해당 메서드를 <Module> 타입의 정적 생성자에서 호출하는 코드를 넣어 컴파일한다.

* ModuleInitializer 애트리뷰트의 대상이 될 메서드에는 다음과 같은 제약 사항이 있다.
  - 반드시 static 메서드이어야 한다.
  - 리턴 타입은 void, 파라미터는 없어야 한다.
  - 제네릭 타입은 허용하지 않는다.
  - <Module> 타입에서 호출이 가능해야 하므로 internal 또는 public 접근 제한자만 허용한다.

* 유의사항: 어떤 순서로 호출될지 제어할 수 없으므로 실행 순서에 의존하는 코드를 작성해서는 안 된다.

### 공변 리턴 타입 (Covariant return type)

* C# 언어에서는 메서드를 이름, 파라미터 타입으로 구분하므로 리턴 타입이 달라도 중복 메서드로 인지하여 컴파일 오류가 발생한다.
  - 그러나 C# 9.0부터는 리턴 타입이 상속 관계의 하위 타입인 경우에 한해 사용할 수 있게 되었다.

### foreach 루프에 대한 GetEnumerator 확장 메서드 지원

* 외부 개발자가 해당 타입의 소스코드를 변경하지 않고 단지 GetEnumerator 확장 메서드를 제공하면 foreach에 사용할 수 있도록 만들 수 있다.

### 부분 메서드에 대한 새로운 기능

* C# 3.0의 부분 메서드는 다음 3가지 주요 제약을 가지고 있었는데 C# 9.0에서 모두 풀렸다.
  - 리턴 타입 허용
  - out 파라미터 허용
  - (암묵적으로 private이지만) 명시적으로 private을 포함한 접근 제한자 허용

* 대신 구현부를 더 이상 생략할 수 없는 조건이 추가되었다.

### localsinit 플래그 내보내기 무시

* C# 컴파일러는 기본적으로 모든 로컬 변수의 공간을 사용 여부에 상관없이 0 값으로 초기화하도록 내부 코드를 생성한다.
  - 하지만 0으로 초기화하는 것이 꼭 필요한 작업은 아니다.
  - C# 컴파일러는 개발자가 명시적으로 초기화하지 않은 변수를 사용할 때 컴파일 오류를 발생시킨다.
  - 어차피 개발자가 변수에 값을 할당해야 하기 때문에 변수를 초기화하는 작업을 2번 하지 않는 게 낫다.
  - 로컬 변수의 초기화를 생략하고 싶은 메서드에 SkipLocalsInitAttribute 애트리뷰트를 unsafe와 함께 적용하면 성능을 높일 수 있다.

### 원시 크기 정수

* 32비트 환경에서는 4바이트로, 64비트 환경에서는 8바이트로 동작하는 nint, nuint 정수 타입이 새로 추가되었다.

### 함수 포인터

* C# 8.0까지는 함수 포인터의 역할을 델리게이트가 담당했다.
  - 델리게이트를 경유하기 때문에 성능이 떨어진다.
  - C# 9.0부터 대상 메서드를 바로 호출해 성능을 높일 수 있는 새로운 함수 포인터 구문을 unsafe 문맥으로 제공한다.
  - 델리게이트를 함수 포인터로 바꾸면 성능은 개선되지만 안정성을 포기해야 한다.

* 함수 포인터는 비관리 모듈과의 연동에도 큰 변화를 가져온다.
  - 비관리 함수 포인터 지원
  - 비관리 함수를 통한 콜백 지원

### 제약 조건이 없는 형식 파라미터 주석 (Unconstrained type parameter annotations)

* 기본적으로 nullable 형식임을 의미하는 물음표 표시는 참조 형식이 아닌 값 형식에만 허용된다.
  - C# 8.0의 nullable 문맥은 참조 형식에 대해서도 ? 표시를 허용하게 만들었다.
  - 그러나 범용 형식 파라미터(T)에 ?를 사용하면 해당 타입이 값 형식일 수도, 참조 형식일 수도 있으므로 컴파일 오류가 발생했다.
  - 그래서 반드시 값 형식인지, 참조 형식인지 명시하는 제약이 필요하다.
  - C# 9.0부터는 제약을 지정하지 않으면 "where T class"를 생략한 것으로 간주하기로 했다.
  - 자세한 내용은 생략한다.

## C# 10

### 레코드 개선

* C# 10에서 record 문법이 2가지 개선되었다.
  - 레코드 구조체
    * 참조 형식(class) 유형으로만 record 타입을 정의할 수 있었으나 이제는 값 형식의 타입 생성을 지시하는 record struct가 추가되었다.
    * 따라서 기존의 참조 형식 record 정의를 구분하기 위해 record class 타입도 명시적으로 추가되었다.
  - class 타입의 record에 ToString 메서드의 sealed 지원
    * record를 정의하면 C# 컴파일러는 자동으로 System.Object 클래스의 멤버 중 Equals, GetHashCode, ToString 메서드에 대한 기본 코드를 제공하며, 원한다면 ToString과 GetHashCode 메서드에 한해 사용자 측에서 재정의할 수 있다.
    * C# 10부터는 상속 클래스에서의 재정의를 막는 sealed 키워드를 ToString 메서드에 적용하는 것이 가능해졌다. (단 record struct는 상속이 불가능하므로 사용할 수 없음)

### 구조체 개선

* 구조체에 다음 2가지를 지원하게 되었다.
  - 기본 생성자 지원
  - 필드 초기화 지원

* 이 기능들은 레코드 구조체(record struct)를 지원하기 위해 추가된 것이다.

### 네임스페이스 개선

* 전역 using 지시문
  - 자주 사용하는 네임스페이스들을 파일마다 선언해야 하는 번거로움 때문에 추가된 기능이다.
  - C# 프로젝트에 포함되는 하나의 소스코드 파일에 global 키워들을 이용한 네임스페이스 선언을 포함하면 된다.
  - C# 10부터는 프로젝트 파일(.csproj) 안에 전역 네임스페이스 선언을 자동으로 추가할 수 있는 ImplicitUsings라는 설정이 추가되었고, 이것을 enable 시키면 전역 네임스페이스 선언을 담고 있는 C# 소스코드 파일을 자동으로 생성해 프로젝트와 함께 빌드한다.

* 파일 범위 네임스페이스
  - C# 소스코드에서 네임스페이스를 정의하면 그 영역을 중괄호를 이용한 블록으로 표시한다.
  - C# 10부터는 중괄호를 생략하면 기본적으로 해당 파일에 정의한 전체 타입에 적용된다.

### 보간된 상수 문자열

* "문자열 내에 식(expression) 포함"에서 보간식을 사용하면 string.Format으로 치환된다.
  - 부간식을 사용한 경우 프로그램 실행 시점에 문자열이 결정되기 때문에 상수식이 될 수 없다.
  - 그러나 C# 10부터는 보간식에 사용한 코드가 오직 상수 문자열인 경우, 컴파일 시간에 문자열을 결정할 수 있게 되었다.
  - 이러한 개선과 함께 상수 문자열을 리턴하는 nameof에 대한 문자열 보간식 내에서의 사용이 자유로워졌다.
  - 그러나 이 기능은 오직 상수 문자열만 허용하며 그 외의 상수(숫자형 등)는 지원하지 않는다.

### 확장 속성 패턴

* 타입이 중첩된 경우 내부 인스턴스가 가진 필드에 대한 패턴 매칭을 좀 더 간편하게 지정할 수 있는 문법이 추가됐다.
  - 기존의 경우 필드에 대한 패턴 지정은 중괄호를 이용해야만 했다.
  - C# 10부터는 도트(.) 연산자를 이용해 멤버를 접근하던 것과 동일한 방식으로 중괄호의 사용을 줄일 수 있다.
  - 또한 null 체크까지도 가능하므로 코드의 양을 줄일 수 있게 되었다.

### 람다 기능 향상

* 람다 사용법에 대한 3가지 개선이 이루어졌다.
  - 람다 식에 애트리뷰트 허용
    * 단, 애트리뷰트가 지정된 경우에는 파라미터가 하나만 있는 람다 식에서는 반드시 해당 파라미터에 괄호를 함께 사용해야 한다.
  - 리턴 타입 지정 허용
    * 이제 람다 식의 맅너 값을 명시적으로 지정할 수 있다.
    * 단, 리턴 타입을 명시하는 경우에는 파라미터가 하나라도 반드시 괄호와 함께 지정해야 한다.
  - 람다 식에 대한 var 추론 향상
    * C# 9.0까지는 람다 식에 대해서는 var로 정의한 변수의 타입 추론을 지원하지 않았다.
    * 그래도 타입 정보가 없는 타입에서는 여전히 오류가 발생한다. (타입 정보가 있어야 추론이 가능함, 적어도 인자 값의 타입이라도...)
 
* 이로써 람다 식은 일반 메서드와 다름 없는 수준이 되었다.

### 호출자 인수 식

* C# 5.0에 "호출자 정보"로 다음과 같은 애트리뷰트가 제공되었다.
  - CallerMemberName
  - CallerFilePath
  - CallerLineNumber
 
* C# 10에서는 호출자 인수를 식으로 처리할 수 있는 애트리뷰트가 추가되었다.
  - CallerArgumentExpression
  - 이것을 사용하면, 인자로 넘겨준 표현식을 C# 컴파일러가 자동으로 문자열로 넘겨주기 때문에 단위 테스트, 실행 로그를 남기는 데 유용하다.

### 기타 개선 사항

* C# 10에서 개선된 기능은 다음과 같다.
  - 한정된 할당 분석 개선 (Improved Definite Assignment Analysis)
  - AsyncMethodBuilder 재정의
  - 보간된 문자열 개선
    * 박싱/언박싱으로 인해 GC가 작동하여 성능이 저하했던 이전 코드가 내부적으로 GC 힙 메모리 사용을 줄이는 코드로 바뀌어서 컴파일된다.
  - 분해 구문에서 기존 변수의 재사용 가능
    * Deconstrcut 메서드를 사용한 분해 구문 사용시 값이 대입될 변수를 괄호 안에 모두 선언하든지, 외부에서 모두 선언해야 했는데 이제는 내/외부 변수를 섞어서 받을 수 있게 되었다.
  - Source Generator V2 API
  - 향상된 #line 지시문

## C# 11

### 인터페이스 내에 정적 추상 메서드 정의 가능

### 제네릭 타입의 특성 적용

### 사용자 정의 checked 연산자

### shift 연산자 개선

### IntPtr/UIntPtr과 nint/unint의 통합

### 문자열 개선

### 목록 및 ReadOnlySpan<char> 패턴 매칭

### ref struct 내에 ref 필드 지원

### 파일 범위 내에서 유효한 타입 정의

### 메서드 파라미터에 대한 nameof 지원 확장

### 속성 및 필드에 지정할 수 있는 required 예약어 추가

### 구조체 필드의 기본값 자동 초기화

### 정적 메서드에 대한 delegate 처리 시 캐시(cache) 적용

## C# 12

### 기본 람다 파라미터

### 기본 생성자

### 모든 형식의 별칭

### 인라인 배열

### 컬렉션 식과 스프레드 연산자

### ref readonly 파라미터

### Interceptor (컴파일 싲ㅁ에 메서드 호출 재작성)

### Experimental 특성 지원
