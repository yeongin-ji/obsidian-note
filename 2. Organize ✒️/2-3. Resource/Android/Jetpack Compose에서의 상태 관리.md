>(1) 날짜: 2024.06.05
>(2) 태그(주제/카테고리): #안드로이드 #Compose #State #호이스팅 #remember

>(3) Link
- [[Android]]
- [[Jetpack Compose]]
---

## 앱의 상태(State)란?
> 기본적으로 앱의 상태는 시간이 지남에 따라 변할 수 있는 값입니다. 모든 Android 앱에서는 사용자에게 상태가 표시됩니다.

- 다음은 Android 앱 상태의 예시입니다.
	- 네트워크 연결을 설정할 수 없을 때 표시되는 메시지
	- 양식(ex. 등록 양식): 상태를 작성하고 제출할 수 있습니다.
	- 버튼과 같이 탭할 수 있는 컨트롤: 상태는 *탭하지 않음*, *탭하는 중*(디스플레이 애니메이션) 또는 *탭함*(`onClick`동작) 중에 선택할 수 있습니다.


## 컴포지션(Composition)
> 컴포지션은 Compose가 컴포저블을 실행할 때 빌드한 UI에 관한 설명입니다.

- Compose 앱은 컴포저블 함수를 호출하여 *데이터를 UI로 변환합니다.*
- 상태가 변경되면 Compose는 영향을 받는 컴포저블 함수를 새 상태로 다시 실행합니다.
- 이때 **리컴포지션**이라는 업데이트된 UI가 만들어집니다.
- Compose는 *자동으로 리컴포지션을 예약합니다.*


## 리컴포지션
> 리컴포지션은 Compose가 데이터 변경사항에 따라 변경될 수 있는 컴포저블을 다시 실행한 다음 변경사항을 반영하도록 컴포지션을 업데이트하는 것입니다.

- 컴포지션은 *초기 컴포지션*을 통해서만 생성되고 *리컴포지션*을 통해서만 업데이트될 수 있습니다.
- 컴포지션을 수정하는 유일한 방법은 리컴포지션을 통하는 것입니다.
- 이렇게 하려면 *Compose가 추적할 상태를 알아야 합니다.*
- 그래야 Compose가 업데이트를 받을 때 리컴포지션을 예약할 수 있습니다.

- 예를 들어 다음의 컴포저블에서 `amountInput` 변수를 추적하여 해당 값이 변경될 때마다 리컴포지션을 예약하는 것을 들 수 있습니다.
```
@Composable  
fun EditNumberField(modifier: Modifier = Modifier) {  
    val amountInput = "0"  
    TextField(  
        value = amountInput,  
        onValueChange = {},  
        modifier = modifier  
    )  
}
```


## 앱의 상태 추적하기
> Compose에서 `State` 및 `MutableState` 유형을 사용하여 앱의 상태를 Compose에서 관찰 가능하거나 추적 가능한 상태로 설정할 수 있습니다.

- `State` 유형은 변경할 수 없어 그 유형의 *값만 읽을 수 있습니다.*
- `MutableState` 유형은 *변경 가능*합니다.
- **`mutableStateOf()`** 함수를 사용하여 관찰 가능한 `MutableState`를 만들 수 있습니다.
	- 이 함수는 초기값을 `State` 객체에 래핑된 매개변수로 수신한 다음 `value`의 값을 관찰 가능한 상태로 만듭니다.

- `mutableStateOf()` 함수에서 반환하는 값은 다음과 같은 특성을 지닙니다.
	- 상태(ex. 청구 금액)을 보유합니다.
	- 변경 가능하므로 *값을 변경할 수 있습니다.*
	- 관찰 가능하므로, Compose는 *값의 변경을 관찰하고 리컴포지션을 트리거*하여 UI를 업데이트합니다.


## remember 함수를 이용한 상태 저장
> 리컴포지션으로 인해 컴포저블 함수가 여러 번 호출될 수 있습니다. 이때마다 상태를 재설정하게 되면 **이전의 상태가 보존되지 않는 문제가 발생합니다.** 따라서 `remember` 함수를 통해 이러한 문제를 해결합니다.

- 컴포저블 함수는 `remember`를 사용하여 리컴포지션에서 객체를 저장할 수 있습니다. 
- `remember` 함수로 계산된 값은 초기 컴포지션 중에 저장되고 저장된 값은 리컴포지션 중에 반환됩니다.
- 상태와 업데이트가 UI에 적절하게 반영되도록 일반적으로 컴포저블 함수에 `remember` 및 `mutableStateOf` 함수가 함께 사용됩니다.

```
var amountInput by remember { mutableStateOf("") }
```
-  이렇게 하면 `MutableState`의 `value` 속성을 참조하지 않고도 `amountInput`을 읽고 설정할 수 있습니다.

![[Pasted image 20240609005743.png]]


## 상태 호이스팅
> 상태 호이스팅은 구성요소를 Stateless로 만들기 위해 상태를 호출자로 이동하는 패턴입니다. 쉽게 말해 Stateful Composable에서 상태를 추출하여 Stateless Composable로 만드는 방법입니다.

- Stateful vs. Stateless 컴포저블
	- **Stateless Composable**: *상태가 없는 컴포저블입니다.* 즉, 새 상태를 보유하거나 정의하거나 수정하지 않습니다.
	- **Stateful Composable**: 시간이 지남에 따라 변할 수 있는 *상태를 소유하는 컴포저블*입니다.

- 다음과 같은 경우 상태를 호이스팅해야 합니다.
	- *상태를 여러 컴포저블 함수와 공유*하는 경우
	- 앱에서 *재사용할 수 있는 Stateless Composable을 만드는 경우*

![[Pasted image 20240609084505.png]]

- 이 패턴이 컴포저블에 적용되는 경우 컴포저블에 매개변수 2개가 추가될 때가 많습니다.
	- `value: T` 매개변수 - 표시할 현재 값
	- `onValueChange: (T) -> Unit` - 값이 변경될 때 상태가 업데이트될 수 있도록 트리거되는 콜백 람다


>(5) Reference
- https://developer.android.com/codelabs/basic-android-kotlin-compose-using-state?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-2-pathway-3%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-using-state#3