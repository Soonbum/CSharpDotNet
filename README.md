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
4.7 ~ 4.7.2, 4.8 | C# 7.0 ~ 7.1 - 패턴 매칭, C# 7.2 - 구조체 성능 향상, C# 7.3 - 문법 보강 | 패턴 매칭, 튜플, Span<T>
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
  - ArrayList를 보완한 List<T> 타입이 도입됨: 여기서 T는 타입으로 대체할 수 있다.
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
  - ArrayList --> List<T>
  - Hashtable --> Dictionary<TKey, TValue>
  - SortedList --> SortedDictionary<TKey, TValue>
  - Stack --> Stack<T>
  - Queue --> Queue<T>

* 제네릭 버전 인터페이스는 다음과 같다. (가능하면 제네릭 버전 인터페이스를 대신 사용하는 것을 권장함)
  - IComparable --> IComparable<T>
  - IComparer --> IComparer<T>
  - IEnumerable --> IEnumerable<T>
  - IEnumerator --> IEnumerator<T>
  - ICollection --> ICollection<T>

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

* nullable 타입: System.Nullable<T> 구조체
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

### 자동 구현 속성

### 개체 초기화 (Object initializers)

### 컬렉션 초기화

### 익명 타입

### 부분 메서드

### 확장 메서드

### 람다 식

### LINQ

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
