>(1) 날짜: 2024.06.06
>(2) 태그(주제/카테고리): #Architecture #MVP

>(3) Link
- [[App Architecture]]
---

## MVP Pattern
> Model, View, Presenter의 약자로, MVC 패턴에서 한 단계 보완된 버전이라고 볼 수 있다. (느슨한 결합 원칙, Loose Coupling)

![[Pasted image 20240606005855.png]]
- MVC에 비해 *View와의 결합을 조금 느슨하게 해준다..?*
- MVP 동작 순서
	- 사용자의 Action은 View를 통해 들어온다.
	- View는 데이터를 Presenter에게 요청한다.
	- Presenter는 Model에게 데이터를 요청한다.
	- Model은 Presenter에서 요청받은 데이터를 응답한다. 혹은 비즈니스 로직을 처리한다.
	- Presenter는 View에게 데이터를 응답한다.
	- View는 해당 데이터를 이용하여 화면에 나타낸다.
- **사실 MVC랑 뭔차인지 잘 모르겠다!!!**


>(5) Reference
- https://android-developer.tistory.com/23