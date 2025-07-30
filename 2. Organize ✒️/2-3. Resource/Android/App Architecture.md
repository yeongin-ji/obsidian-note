>(1) 날짜: 2024.06.12
>(2) 태그(주제/카테고리): #안드로이드 #Architecture #ViewModel #State

>(3) Link
- [[Android]]
---

> 앱의 아키텍처는 클래스 간에 앱 책임을 할당하는 데 도움이 되는 가이드라인을 제공합니다. 앱 아키텍처가 잘 디자인되어 있으면 앱을 확장하고 더 많은 기능을 포함할 수 있습니다. 아키텍처는 팀 공동작업을 간소화할 수도 있습니다.

- 가장 일반적인 아키텍처 원칙은 **관심사 분리**와 **모델에서 UI 만들기**입니다.
	- 관심사 분리
		- 관심사 분리 디자인 원칙은 각각 별개의 책임이 있는 여러 함수 클래스로 앱을 나눠야 한다는 원칙입니다.
	- 모델에서 UI 만들기
		- 모델은 앱의 데이터 처리를 담당하는 구성요소로, 앱의 UI 요소 및 앱 구성요소와 독립되어 있으므로 앱의 수명 주기 및 관련 문제의 영향을 받지 않습니다.

- 권장 앱 아키텍쳐
	- UI와 데이터 레이어 간의 상호작용을 간소화하고 재사용하기 위해 *Domain Layer*라는 레이어를 추가할 수 있습니다. (optional)
		![[Pasted image 20240612141525.png]]


## UI 레이어 (Presentation Layer)
> UI 레이어(프레젠테이션 레이어)의 역할은 화면에 애플리케이션 데이터를 표시하는 것입니다. 버튼 누르기와 같은 사용자 상호작용으로 인해 데이터가 변경될 때마다 UI가 변경사항을 반영하여 업데이트되어야 합니다.

- UI 레이어 구성요소
	- **UI 요소**
		- 화면에 데이터를 렌더링하는 구성요소로, Jetpack Compose를 이용하여 빌드
	- **상태 홀더**
		- 데이터를 보유하고 UI에 노출하며 앱 로직을 처리하는 구성요소로, ViewModel을 예로 들 수 있다.

![[Pasted image 20240612141823.png]]

### ViewModel

### UI 상태
![[Pasted image 20240612142103.png]]
>(5) Reference
- https://developer.android.com/codelabs/basic-android-kotlin-compose-viewmodel-and-state?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-4-pathway-1%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-viewmodel-and-state#3