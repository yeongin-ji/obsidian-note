>(1) 날짜: 2024.06.05
>(2) 태그(주제/카테고리): #Architecture #MVC

>(3) Link
- [[App Architecture]]
---

## MVC

> Model, View, Controller의 약자이다.
![[Pasted image 20240605235840.png]]

- **Model**
	- 앱에서 사용하는 데이터, 상태, 비즈니스 로직을 포함.
	- 여기서 `상태`는 UI의 상태를 의미한다.
	- `비즈니스 로직`이란 앱에 필요한 동작을 수행하기 위해서 *데이터를 처리하기 위한 알리즘*을 의미한다.
- **View**
	- *사용자가 보는 화면*을 의미한다.
	- 다만 사용자의 입력에 대해 어떤 동작을 해야 하는지 모른다.
	- 안드로이드 MVC 패턴에서 View는 레이아웃 파일인 `.xml`형태를 포함하고 있다.
	- `xml`파일에는 어떤 동작을 처리하기 위한 코드를 담기 어렵다.
	- 따라서 실제 동작 처리는 다른 파일에 정의된 함수에서 해야 한다.
- **Controller**
	- Model과 View의 인터페이스 역할을 한다.
	- View가 사용자 입력을 받으면 Controller에게 알린다.
	- Controller는 적절한 조치를 취하기 위한 동작을 한다. (ex. Model과 상호작용하여 UI상태를 갱신)
	- *Activity* 혹은 *Fragment*가 Controller의 역할을 수행한다.
	- 안드로이드에서는 View(xml)과 Controller(Activity, Fragment)를 묶어서 보기 때문에 사실상 둘을 묶어서 View라고 표현하기도 한다.
	- Controller는 여러 개의 View를 선택할 수 있는 1:n 구조이다.

![[Pasted image 20240606002415.png]]
> MVC의 문제점: View와 Controller가 강하게 연결되어있다.
- Controller를 Activity, Fragment에 구현함
- View를 수정할 경우 Controller를 같이 수정해야 하는 경우가 생김
- Controller를 수정할 경우 Model을 같이 수정해야 하는 경우가 생김
- 연쇄적인 수정이 일어나 리소스가 많이 듦.

## MVC 예시
![[Pasted image 20240606003140.png]]
- **View**
	- 사용자에게 보여지는 화면UI를 구성: `activity_order.xml`
- **Controller**
	- View를 통해 입력을 받으면 Controller가 다음을 처리한다.
		- Model에게 메뉴 수량 증감 요청
		- View에게 수량 변경에 따른 UI 갱신
		- Model에게 수량 증감에 따른 합계 가격 증감 요청
		- View에게 합계 가격 UI 갱신
		- 등등...
	- Controller 내부에는 *직접적인 데이터 변경 작업이나 비즈니스 로직이 없다!!*
- **Model**
	- View와 연결된 부분이 전혀 없고 *의존성 없이 독립적이다.*

## 용어 Tip
- **Presentation Logic**: 실제 눈에 보이는 GUI(Graphic User Interface) 화면을 구성하는 코드
- **Business Logic**: 데이터를 보여주기 위해서 DB를 검색하는 코드 및 GUI 화면에서 새롭게 발생된 데이터를 DB에 저장하는 코드 등 실제적인 작업 동작이 이루어지는 코드

>(5) Reference

