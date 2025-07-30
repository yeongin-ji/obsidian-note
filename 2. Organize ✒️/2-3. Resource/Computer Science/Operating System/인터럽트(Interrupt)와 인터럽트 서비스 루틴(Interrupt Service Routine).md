>(1) 날짜: 2025.02.09
>(2) 태그(주제/카테고리): #CS #OS #Interrupt 

>(3) Link
- [[Operating System]]
- [[운영체제(OS)란 무엇인가]]
---

# 인터럽트(Interrupt)
입출력 연산은 일반적으로 CPU 사이클보다 느리다. CPU와 입출력 장치는 병렬적으로 실행되므로, CPU Utilization을 높이기 위해서는 *CPU가 입출력 장치를 기다리는 동안 다른 작업을 수행할 수 있어야 한다.*

그런데, 이것이 가능하려면 장치 컨트롤러가 작업을 완료했을 때 CPU에게 해당 사실을 알릴 수 있어야 한다. 결국 장치 컨트롤러는 **인터럽트(Interrupt)** 를 통해 CPU에게 작업 완료를 알린다.

>인터럽트는 **CPU의 관심이 필요한 이벤트**이다. 그 이벤트는 에러, 작업의 완료 등을 포함한다. 인터럽트는 **하드웨어 인터럽트(Hardware Interrupt)** 와 **소프트웨어 인터럽트(Software Interrupt)** 로 나누어진다.

인터럽트는 운영체제가 하드웨어와 상호작용 하는 핵심적인 부분(Key Part)이다. 대표적으로 Windows, Unix 운영체제가 Interrupt Driven이다.

## 하드웨어 인터럽트(Hardware Interrupt)
하드웨어 입출력 장치에 의해 제공되는 인터럽트를 의미한다. 인터럽트의 종류에는 아래와 같은 항목이 포함된다.
- 마우스 움직임
- 키보드 타이핑
- 이더넷 패킷 전송
- 디스크/CD/테이프 드라이버
- 타이머
- 사운드(마이크)

## 소프트웨어 인터럽트(Software Interrupt) (=traps)
### System calls
> 유저 프로그램에 의해 커널(Kernel)이 호출되는 경우

### Exceptions
> `divide by zero` 와 같이 주요한 예외를 처리하기 위한 인터럽트

## 인터럽트 핸들러(Interrupt handler)
CPU는 인터럽트를 감지하는 경우, 하고 있던 작업을 멈추고 즉시 인터럽트 핸들링에 돌입한다. 이때 해당 서비스 루틴의 시작 주소를 참조하는데, 이를 인터럽트 벡터(Interrupt vector)라고 한다. 인터럽트 벡터는 low memory에 저장되어 있다.

CPU는 요청에 맞는 인터럽트 서비스 루틴(Interrupt Service Routine, ISR)을 처리한 뒤, 기존 작업으로 복귀한다.



>(5) Reference
- 공룡책
