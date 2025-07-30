>(1) 날짜: 2025.06.15
>(2) 태그(주제/카테고리): #golang #goroutine

>(3) Link
- 
---

- goroutine은 편리하지만 무분별하게 사용하면 예상치 못한 오류가 발생할 수 있으므로 잘 사용해야 한다.

- go의 동시성 패턴을 배우기 전 사전지식: goroutines/ channels/ select

- go가 따르는 동시성 모델: fork-join model

- fork/join 모델은 특정 지점에서 분기(fork)하여 병렬 실행을 이어가다 이후 지점에서 join하여 결과를 모으고 순차적 실행 흐름을 이어가는 병렬 디자인 패턴이다.

- join point를 만드는 것은 개발자의 책임이다. join point에 도달하기 전에 프로그램이 끝나버릴 수 있다.

- channel은 주로 goroutine 간 정보 전달에 이용된다.

- select문: goroutine이 여러 통신 작업을 기다리도록 하는 것!

- select문이 하는 역할은 기본적으로 정의된 case중 하나가 실행 가능해질 때 까지 기다리는 것임 (동시에 실행 가능해질 경우 무작위로 선택)

- 가장 중요한 동시성 패턴 3가지가 있음: for-select loop/ done channel/ pipelines

- for loop의 각 반복에 대해 select문을 사용하는 것

- buffered channel은 goroutine간 비동기 통신에 사용하지만, unbuffered channel은 동기화하는데 사용된다. 그 이유는 unbuffered channel은 크기가 1이라 두 고루틴 간의 교환이 송수신이 발생하는 순간에 수행되도록 보장하기 때문이다.

- goroutine간 동기 통신: unbuffered channel, 송신자는 수신자가 있을 때 까지 기다림. 수신자가 데이터를 가져가야 재개됨

- goroutine간 비동기 통신: buffered channel, 송신자는 채널에 데이터를 넣고 잊어버림

- goroutine leakage(누수): 백그라운드에서 계속 돌아가는 것을 원하지 않는 고루틴이 계속 돌아가는 것 -> 방지하려면 부모 고루틴이 자식을 취소할 수 있도록 하는 메커니즘을 구현 -> 이것이 done channel!

- pipeline 패턴은 각 단계의 관심사를 분리할 수 있다. 수정사항이 발생할 경우 각 단계에서만 수정하면 되므로 유지보수가 용이해진다.

- generator: 채널에서 데이터 스트림을 생성하는 방법 중 하나로, 이렇게 생성된 데이터 스트림을 파이프라인 개념과 통합할 예정

















>(5) Reference

