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
  - 단, 해당 컬렉션 타입이 반드시 ICollection<T> 인터페이스를 구현해야 한다.

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
  - 쿼리 문은 IEnumerable<T> 타입으로 저장된다.
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

...

### 동시성 컬렉션

## C# 5.0

### 호출자 정보

### 비동기 호출

## C# 6.0

### 자동 구현 속성의 초기화 구문 추가

### 표현식을 이용한 메서드, 속성 및 인덱서 정의

### using static 구문을 이용한 타입명 생략

### null 조건 연산자

### 문자열 내에 식(expression) 포함

### nameof 연산자

### Dictionary 타입의 인덱스 초기화

### 예외 필터

### 컬렉션 초기화 구문에 확장 메서드로 정의한 Add 지원

### 기타 개선 사항

## C# 7.0

### 더욱 편리해진 out 파라미터 사용

### 리턴값 및 로컬 변수에 ref 기능 추가

### 튜플

### Deconstruct 메서드

### 람다 식을 이용한 메서드 정의 확대

### 로컬 함수

### 사용자 정의 Task 타입을 async 메서드의 리턴 타입으로 사용 가능

### 자유로워진 throw 사용

### 리터럴에 대한 표현 방법 개선

### 패턴 매칭

## C# 7.1

### Main 메서드에 async 예약어 허용

### default 리터럴 추가

### 타입 추론을 통한 튜플의 변수명 자동 지정

### 기타 개선 사항

## C# 7.2

### 메서드의 파라미터에 in 변경자 추가

### 읽기 전용(readonly) 구조체

### 메서드의 리턴 값 및 로컬 변수에 ref readonly 추가

### 스택에만 생성할 수 있는 값 타입 지원 - ref struct

### 신규 추가 타입: Span<T>

### 3항 연산자에 ref 지원

### private protected 접근자 추가

### 숫자 리터럴의 선행 밑줄

### 뒤에 오지 않는 명명된 인수

## C# 7.3

### 신규 제네릭 제약 조건 - Delegate, Enum, unmanaged

### 사용자 정의 타입에 fixed 적용 가능

### 힙에 할당된 고정 크기 배열의 인덱싱 개선

### 초기화 식에서 변수 사용 가능

### 자동 구현 속성의 특성 지원

### 튜플의 ==, != 연산자 지원

### ref 지역 변수의 재할당 가능

### stackalloc 배열의 초기화 구문 지원

## C# 8.0

### #nullable 지시자와 nullable 참조 형식

### 비동기 스트림

### 새로운 연산자 - 인덱스, 범위

### 간결해진 using 선언

### Dispose 호출이 가능한 ref struct

### 정적 로컬 함수

### 패턴 매칭 개선

### 기본 인터페이스 메서드

### ??= (널 병합 할당 연산자)

### 문자열 @, $ 접두사 혼합 지원

### 기본 식으로 바뀐 stackalloc

### 제네릭 구조체의 unmanaged 지원

### 구조체의 읽기 전용 메서드

## C# 9.0

### 레코드

### 대상에 따라 new 식 추론

### 달라진 조건식 평가

### 로컬 함수에 특성 지정 가능

### 익명 함수 개선

### 최상위 문

### 패턴 매칭 개선

### 모듈 이니셜라이저

### 공변 반환 형식

### foreach 루프에 대한 GetEnumerator 확장 메서드 지원

### 부분 메서드에 대한 새로운 기능

### localsinit 플래그 내보내기 무시

### 원시 크기 정수

### 함수 포인터

### 제약 조건이 없는 형식 파라미터 주석

## C# 10

### 레코드 개선

### 구조체 개선

### 네임스페이스 개선

### 보간된 상수 문자열

### 확장 속성 패턴

### 람다 기능 향상

### 호출자 인수 식

### 기타 개선 사항

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
