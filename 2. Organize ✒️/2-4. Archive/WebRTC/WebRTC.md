>(1) 날짜: 2024.06.07
>(2) 태그(주제/카테고리): #WebRTC

>(3) Link
- [[Android]]: WebRTC를 통해 안드로이드에서도 실시간 통신이 지원될 수 있다.
- [[Say Better]]: 해당 프로젝트에서 WebRTC를 통해 실시간 통신을 구현했다.
---

## WebRTC란?

> WebRTC (Web Real-Time Communications)란, 웹/앱 어플리케이션들이 별도의 소프트웨어 없이 음성, 영상 미디어 혹은 텍스트, 파일 같은 데이터를 브라우저끼리 주고 받을 수 있게 만든 기술

- **Android** 및 IOS도 지원한다.
- WebRTC로 구성된 프로그램들은 별도의 플러그인이나 소프트웨어 없이 P2P 화상회의 및데이터 공유가 가능하다.



## WebRTC 통신 원리

크게 3가지 클래스에 의해 실시간 데이터 교환이 이루어짐

- MediaStream : 카메라와 마이크 등의 데이터 스트림 접근
- **RTCPeerConnection** : 암호화 및 대역폭 관리, 오디오/비디오의 연결
- RTCDataChannel : 일반적인 데이터의 P2P 통신

### Signaling Server

- PeerConnection은 **Caller(송신자)** 와 **Callee(수신자)** 의 쌍으로 이루어진다.
- Caller와 Callee가 통신하기 위해서는 **SessionDescription**을 서로 주고 받아야 한다.
- SessionDescription을 주고 받기 위해서는 중개 서버, 즉 **Signaling Server**가 필요하다.



## Stun Server

> STUN (Session Traversal Utilities for NAT):
> 요청받은 기기의 외부 관점에서의 IP:port 정보를 반환하는 서버

![[Pasted image 20240328164021.png]]

- Peer간의 직접적인 연결을 수행하는 경우 공개적으로 배포된 서버를 이용하는 것 보다 복잡한 과정을 수반한다.
- 대부분 앱이 **NAT** 뒤에서 실행되기 때문에 **Private IP** 주소로는 서로에게 접근할 수 없다.
- 따라서 각 Peer는 SessionDescription을 작성할 때 **STUN** 서버를 통해 스스로의 외부 관점에서의 **Public IP:Port** 주소를 받는다.
- STUN 서버의 일은 간단하기 때문에 저사양이어도 상관없다.
- 대부분의 WebRTC 호출은 STUN을 사용하여 성공적으로 연결되지만(86%), *방화벽 뒤의 Peer간 호출과 복잡한 NAT 구성의 경우에는 TURN 서버를 통한 우회가 필요하다.*



## TURN Server

> TURN (Traversal Using Relays around NAT):
> Peer간 직접 통신이 실패할 경우 종단점들 사이에 데이터 릴레이를 수행한다.

![[Pasted image 20240328165409.png]]

- `RTCPeerConnection`은 UDP를 통해 Peer 간의 직접 통신을 설정하려고 시도한다.
- 실패 시 TCP를 사용하려고 시도한다.
- 이 방법이 실패하면 TURN 서버를 대체 엔드포인트로 사용하여 실제 엔드포인트 간에 데이터를 릴레이 할 수 있다.
- TURN 서버는 *신호를 보내는 것이 아니라 Peer 간 오디오/동영상/데이터 스트리밍을 전달*는데 사용된다.
- TURN 서버는 스트림을 릴레이해야 하므로 많은 대역폭을 소비한다. 즉, TURN 서버의 성능이 속도에 관여한다.



## ICE 프레임워크

> ICE (Interactive Connectivity Establishment):
> 두 단말이 서로 통신할 수 있는 최적의 경로를 찾을 수 있도록 도와주는 프레임워크

### ICE Candidate Gathering

- **Candidate**는 IP 주소와 Port number의 조합으로 표시된 주소를 의미한다.
	- 후보1) Local Address Candidate
	- 후보2) STUN 서버를 통해 얻은 Public Candidate
	- 후보3) TURN 서버를 통해 얻은 Relayed Candidate

- **ICE Candidate Gathering**은 SDP(Session Description Protocol) Offer의 3개의 Candidate와 SDP Answer의 3개의 Candidate를 *우선순위를 정하여 교환*하는 것을 의미한다.

### SDP 메시지 예시

![[Pasted image 20240328173347.png]]

- `a=candidate` 속성에 우선순위를 정하여 IP주소와 UDP 포트 넘버를 명시한다.

### ICE 연결성 체크 (Connectivity Checks)

![[Pasted image 20240328173624.png]]

- 두 단말은 TURN 서버와 메시지 교환을 통해 자신의 3개 Candidate 주소를 확인하고 SDP Offer와 SDP Answer를 통해 상대방의 3개 Candidate 주소를 확인한다.
- ICE 프레임워크는 *각 후보 간의 연결 가능 여부를 확인*한다.

![[Pasted image 20240328173903.png]]

- 주어진 모든 Candidate에 대한 확인을 마치면 *사용 가능한 주소 리스트가 만들어진다.*



## TLS를 이용한 보안 연결

> TLS (Transport Layer Security):
> Transport Layer에 적용되는 보안 프로토콜

- 모든 WebRTC 구성 요소에 필수적이다.
- WebRTC는 실시간 데이터 스트림에만 관여하고 *연결 메커니즘은 지원하지 않기 때문이다.*


>(5) Reference

