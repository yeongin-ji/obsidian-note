>(1) 날짜: 2024.06.06
>(2) 태그(주제/카테고리): #안드로이드 #Activity #Lifecycle

>(3) Link
- [[Android]]
---

> Activity는 전체 기간동안 여러 상태로 전환되고 때에 따라 이전 상태로 돌아가기도 합니다. 이러한 상태 전환을 Activity Life Cycle이라고 합니다.

> Android에서 Activity는 사용자와 상호작용하는 진입점입니다. 이전에는 하나의 Activity가 앱에서 하나의 화면을 표시했지만 현재 권장사항은 한 Activity가 필요에 따라 화면을 교체하여 여러 화면을 표시할 수 있습니다.


## Activity 수명 주기의 개념
> 모든 Activity에는 수명 주기가 있습니다. 나비가 알로 태어나 번데기를 거쳐 나비가 되고 죽음에 이르기까지 여러 단계를 거치는 것처럼, Android 역시 Activity가 처음 초기화될 때부터 소멸될 때까지 거쳐가는 여러 상태로 구성됩니다.
![[Pasted image 20240611033846.png]]

- Android Activity는 `onCreate()` 메서드로 시작합니다.
- 다음 다이어그램은 모든 Activity 수명 주기 상태를 보여줍니다.
- 나비의 수명 주기와 달리 Activity 수명 주기는 한 방향으로만 이동하는 것이 아니라 *수명 주기 내내 상태 간에 전환할 수 있습니다.*
- 이러한 수명 주기의 시점을 알아보려면 **로깅**을 하면 좋습니다.


## `Log` 클래스를 통한 로깅
> Log 클래스는 Logcat에 메시지를 씁니다. Logcat은 메시지를 기록하는 콘솔입니다. 개발자는 Log 클래스 메서드를 사용하여 이곳에 메시지를 명시적으로 전송할 수 있으며, 앱에 관한 Android의 메시지가 여기에 표시됩니다.

- `Log` 명령의 세 가지 중요한 점
	- 로그 메시지의 **우선순위**
		- `Log.v()`: 상세 메시지 기록
		- `Log.d()`: 디버그 메시지 기록
		- `Log.i()`: 정보 메시지 기록
		- `Log.w()`: 경고 메시지 기록
		- `Log.e()`: 오류 메시지 기록
	- 로그 메시지의 **태그**
		- 태그는 Logcat에서 로그 메시지를 더 쉽게 찾을 수 있도록 합니다. *태그는 보통 클래스 이름입니다.*
	- 실제 **로그 메시지**
		- 표시하고자 하는 짧은 문자열입니다.


## `onCreate()`
> `onCreate()` 수명 주기 메서드는 *Activity가 초기화된 직후*, 즉 OS에서 메모리에 새 Activity 객체를 만들 때 한 번 호출됩니다. `onCreate()`가 실행되면 Activity가 *생성됨*으로 간주됩니다.

![[Pasted image 20240611034107.png]]


## `onStart()`
> `onStart()` 수명 주기 메서드는 *`onCreate()` 직후에 호출*됩니다. `onStart()`가 실행되면 Activity가 화면에 표시됩니다. Activity를 초기화하는 데 한 번만 호출되는 `onCreate()`와 달리 `onStart()`는 시스템에서 Activity의 수명 주기 동안 *여러 번 호출할 수 있습니다.*

![[Pasted image 20240612115135.png]]
- `onStart()`는 상응하는 `onStop()` 수명 주기 메서드와 페어링됩니다.
- 사용자가 앱을 시작한 후 기기 홈 화면으로 돌아오면 활동이 중지되고 더 이상 화면에 표시되지 않습니다.


## `onResume()`
> 앱을 Foreground로 가져오고 사용자는 이제 앱과 상호작용할 수 있습니다.

![[Pasted image 20240612120034.png]]
- 지금까지 소개한 메서드의 차이점은 다음과 같습니다.
	- `onCreate()`: 시스템이 앱을 생성할 때 호출됩니다.
	- `onStart()`: 앱이 화면에 표시되도록 하지만 사용자는 *아직 앱과 상호작용할 수 없습니다.*
	- `onResume()`: 앱을 포그라운드로 가져오고 사용자는 *이제 앱과 상호작용할 수 있습니다.*


## Activity에서 이동하거나 Activity로 이동
- 사용자가 Activity에서 벗어나는 경우에도 Activity는 완전히 닫히지 않습니다.
- 활동이 화면에 더 이상 표시되지 않으면 **백그라운드**에 배치됩니다.
- 이와 반대의 경우는 포그라운드에 있거나 화면에 표시되는 것입니다.
- 사용자가 앱으로 돌아오면 동일한 활동이 다시 시작되어 화면에 다시 표시됩니다.
- 수명 주기에서 이 부분을 앱의 *표시 수명 주기*라고 합니다.


## 포커스와 가시성의 차이
> 앱이 백그라운드로 이동하면 `onPause()` 후에 포커스가 상실되고 `onStop()` 후에 더 이상 앱이 표시되지 않습니다. 포커스와 가시성의 차이가 중요합니다. 활동이 화면에 _부분적으로_ 표시되지만 사용자 포커스는 없을 수 있습니다.


## 구성 변경이 발생하는 경우
> 가로/세로 모드 간 변경과 같이 앱의 상태가 급격하게 변하는 경우, Activity 수명 주기는 `onDestroy()` 를 통해 활동을 소멸시켰다가 `onCreate()` 를 통해 다시 생성됩니다. 이때 소멸 및 생성 과정을 거치면서 데이터가 손실됩니다. 데이터 손실을 막으려면 `remember()` 함수 대신 **`rememberSavable()`** 함수를 통해 앱이 종료되어도 값을 유지할 수 있도록 합니다.


## `ViewModel` 개요
> 그러나 `rememberSavable()` 함수를 사용하면 해당 값과 관련된 로직을 유지해야 할 수 있습니다. 따라서 Android Jetpack 라이브러리의 아키텍쳐 구성요소 중 하나인 ViewModel을 사용함으로써 *빠른 활동 재생성을 통해서만 데이터를 캐시합니다.*


>(5) Reference
- https://developer.android.com/codelabs/basic-android-kotlin-compose-activity-lifecycle?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-4-pathway-1%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-activity-lifecycle#0