>(1) 날짜: 2024.06.05
>(2) 태그(주제/카테고리): #Architecture #MVVM

>(3) Link
- [[App Architecture]]
---

## MVVM Pattern이란
> Model, View, ViewModel의 약자로, MVC, MVP의 "결합도가 너무 높다"는 단점을 보완하는 패턴이다.

![[Pasted image 20240606012640.png]]
- View의 상태를 알 수 있는 ViewModel이 등장하면서 View와 ViewModel간의 완전한 분리가 가능해졌다.
- 따라서 ViewModel에서는 *UI에 대한 작업을 하지 않는다.*
- **ViewModel**에서는 오직 데이터의 업데이트만 실시한다.
- **View**에서는 해당 데이터를 보여주기만 한다.


## MVVM 장점
- 상태 관찰을 통한 Reactive 프로그래밍이 가능
- ViewModel에서 등장한 `viewBinding`, `dataBinding`으로 인해 작성 코드가 많이 줄어들고 쉽게 UI를 변경할 수 있게 되었다.
	- viewBinding 특징
		- 컴파일 타임에 XML 파일과 매핑되는 바인딩 클래스를 생성
		- 바인딩 클래스를 통해 View를 참조할 수 있음
		- `findViewById()` 메서드보다 빠른 성능
		- 런타임 시에 불필요한 `xml` 파일 분석이 필요하지 않음
	- dataBinding 특징
		- 런타임 시에 View와 `xml` 파일 간의 데이터 바인딩을 수행
		- `xml` 파일에 직접 표현식을 작성하여 UI를 업데이트 할 수 있음
		- 다만 `findViewById()` 메서드보다 느린 성능
		- 데이터 바인딩의 복잡도가 높아질수록 성능 저하 발생 우려
- 독립적인 특성으로 인해 *테스트가 용이하다.*

>(5) Reference

