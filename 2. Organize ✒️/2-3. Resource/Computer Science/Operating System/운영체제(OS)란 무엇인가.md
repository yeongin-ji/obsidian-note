>(1) 날짜: 2025.02.08
>(2) 태그(주제/카테고리): #CS #OS  

>(3) Link
- [[Operating System]]
---

## 메모
### 운영체제(Operating System)
**컴퓨터 하드웨어를 관리하는 소프트웨어**로, 하드웨어 리소스를 할당하는 정부(Governent)와 같은 역할을 수행한다. 매우 복잡하여 한 단어로 정리하기 어렵다.

### 컴퓨터 시스템 개략적인 구성
운영체제는 응용 프로그램과 컴퓨터 하드웨어 사이에서 **인터페이스(Interface)** 역할을 수행한다.
- 사용자 : 사람 혹은 기계, 또 다른 컴퓨터가 유저가 될 수 있다.
- 응용 프로그램
- **운영체제**
- 컴퓨터 하드웨어 : CPU, 메모리, 입출력 장치 등을 의미한다.

### 운영체제를 바라보는 관점
운영체제는 두 가지 관점으로 바라볼 수 있다.
- 사용자 관점
	- CLI(Command Line Interface) vs. GUI(Graphic User Interface)
	- 상호 작용 방식
		- PC : 키보드, 마우스 등을 이용한 입출력
		- Mobile : 터치스크린 등을 이용한 입출력
- 시스템 관점
	- 자원 할당자(Resource Allocator)
	- 제어 프로그램(Control Program) : **커널(Kernel)** 을 의미한다.

### 컴퓨터 시스템 구성(Organization)
- 인터럽트(Interrupt)
	- 하드웨어는 언제든 시스템 버스(bus)를 통해 CPU에 신호를 보내 인터럽트를 발생시킬 수 있다. 현대의 운영체제는 대부분 Interrupt Driven으로 동작한다.
- 저장장치 구조(Storage Structure)
	- 컴퓨터 시스템에서는 메인 메모리를 비롯한 다양한 형태의 저장장치를 사용한다.
- 입출력 구조(I/O Structure)

### 컴퓨터 시스템 구조(Architecture)
- 단일 처리기 시스템(Single-Processor Systems)
	- 과거의 컴퓨터 시스템은 단일 처리 코어를 가진 하나의 CPU를 포함하는 단일 프로세서를 사용했다.
- 다중 처리기 시스템(Multiprocessor Systems)
	- 최신 컴퓨터에서는 멀티 프로세서 시스템이 지배적이다. 이러한 시스템에는 두 개 이상의 프로세서가 존재한다.
- 클러스터형 시스템(Clustered Systems)
	- 둘 이상의 독자적 시스템 또는 노드들을 연결하여 구성한다.

### 운영체제의 작동(Operations)
- 다중 프로그래밍과 멀티태스킹(Multiprogramming and Multitasking)
	- 다중 프로그래밍 : 운영체제는 일반적으로 여러 프로세스를 메모리에 유지하며 각 프로세스 간 전환을 통해 CPU가 유휴 상태(Idle)로 머물지 않도록 하여 사용자의 만족도를 높인다.
	- 멀티태스킹 : 다중 프로그래밍의 논리적 확장으로, 프로세스의 CPU 시간을 매우 작게 쪼개어 프로세스를 번갈아가며 실행하도록 한다. 이렇게 하면 하나의 CPU로 여러 프로그램을 동시에 실행하는 것 처럼 보이게 만들 수 있다.
- 이중 모드, 다중 모드 운용(Dual-mode and Multimode Operation)
	- 악의적인 프로그램 등으로 인한 운영체제의 잘못된 실행을 막기 위하여 대부분의 컴퓨터 시스템은 사용자 모드(User mode)와 커널 모드(Kernel mode)를 분리하는 방식을 취한다. 현재의 모드를 나타내기 위한 모드 비트가 존재한다.
- 타이머(Timer)
	- 운영체제가 CPU에 대한 제어를 유지하도록 하기 위해서, 사용자 프로그램이 무한 루프에 빠지는 등 제어가 운영체제로 복귀하지 않는 경우가 없도록 보장한다. 이러한 목적을 달성하기 위해 타이머를 사용한다. 이 타이머는 지정된 시간 이후 컴퓨터를 인터럽트하도록 설정할 수 있다.

### 자원 관리(Resource Management)
- 프로세스 관리(Process Management)
- 메모리 관리(Memory Management)
- 파일 시스템 관리(File System Management)
- 대용량 저장장치 관리(Mass-Storage Management)
- 캐시 관리(Cache Management)
- 입출력 시스템 관리(I/O Systems Management)

### 보안과 보호
- 보호(Protection) : 컴퓨터 시스템이 정의한 자원에 대해 프로그램, 프로세스, 또는 사용자들의 **접근을 제어**하는 기법이다.
- 보안(Security) : 컴퓨터 시스템은 충분한 보호 기능이 있더라도 여전히 고장이 나거나 부적절한 접근을 허용할 수 있으므로 이러한 **외부 또는 내부의 공격을 방어**하는 것을 의미한다.

### 가상화(Virtualization)
단일 컴퓨터의 하드웨어(CPU, 메모리, 디스크 드라이브, 네트워크 인터페이스 카드 등)를 **여러 가지 실행 환경으로 추상화**하여 개별 환경이 자신만의 컴퓨터에서 실행되고 있다는 환상을 만들 수 있는 기술을 의미한다. 대표적으로 **가상 머신**을 이용한다.

### 분산 시스템(Distributed Systems)
분산 시스템은 물리적으로 떨어져 있는 이기종 컴퓨터들의 집합이다. 분산 시스템의 컴퓨터들은 사용자가 시스템 내의 다양한 자원들을 접근할 수 있도록 **네트워크**로 연결되어 있다.

### 커널 자료구조(Kernel Data Structures)
- 리스트, 스택 및 큐(Lists, Stacks, and Queues)
- 트리(Trees)
- 해시 함수와 맵(Hash Functions and Maps)
- 비트맵(Bitmaps)

### 다양한 컴퓨팅 환경(Computing Environments)
- 전통적 계산(Traditional Computing)
- 모바일 컴퓨팅(Mobile Computing)
- 클라이언트 서버 컴퓨팅(Client-Server Computing)
- 피어 간 컴퓨팅(Peer-to-Peer Computing)
- 클라우드 컴퓨팅(Cloud Computing)
- 실시간 임베디드 시스템(Real-Time Embedded Systems)

### 무료 및 오픈 소스 운영체제
- 리눅스(Linux), 유닉스(Unix) 역사


>(5) Reference
- 공룡책
