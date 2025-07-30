>(1) 날짜: 2024.06.05
>(2) 태그(주제/카테고리): #안드로이드 #Compose 

>(3) Link
- [[Android]]
---

## Jetpack Compose
> 네이티브 UI를 빌드하는 안드로이드의 최신 도구 키트로, UI개발을 간소화하고 가속화합니다. 안드로이드 뷰 시스템에 비해 UI를 구현하는 데 필요한 코드가 더 적으므로 앱을 더 쉽게 유지할 수 있습니다.


## Surface
- `Surface`는 배경 색상이나 테두리와 같은 모양을 개발자가 변경할 수 있는 UI섹션을 나타내는 컨테이너 입니다.

```
@Composable
fun Greeting(name: String) {
    Surface(color = Color.Magenta) {       
        Text(text = "Hi, my name is $name!")   
    }
}
```


## Modifier
- `Modifier`는 컴포저블을 강화하거나 장식하는 데 사용됩니다. 예를 들어 padding 수정자를 사용하여 요소 주위에 공백을 적용할 수 있습니다. 예를 들어 `Modifier.padding()` 함수를 사용하여 실행합니다.
- 이 밖에도 특정 동작을 추가할 수 있습니다.
- 이를 설정하려면 컴포저블이나 레이아웃에서 *수정자를 매개변수로 허용*해야 합니다.

- `Row` 내에서 하위 요소의 위치를 설정하려면 `horizontalArrangement` 및 `verticalAlignment` 인수를 설정해야 합니다. `Column`의 경우 `verticalArrangement` 및 `horizontalAlignment` 인수를 설정합니다.
- `verticalArrangement`에서의 [다양한 세로 정렬을 보여주는 예](https://developer.android.com/static/codelabs/basic-android-kotlin-compose-add-images/img/df69881d07b064d0.gif?hl=ko)를 참고하세요.
- `horizontalArrangement`에서의 [다양한 가로 정렬을 보여주는 예](https://developer.android.com/static/codelabs/basic-android-kotlin-compose-add-images/img/c1e6c40e30136af2.gif?hl=ko)를 참고하세요.

## Composable 함수
- Compose에서 *UI의 기본 빌드 블록을 의미합니다.*
- Composable 함수 특징
	- UI일부를 설명합니다.
	- 아무것도 반환하지 않습니다.
	- 몇 개의 입력을 받아서 화면에 표시되는 내용을 생성합니다.
- 모든 Composable 함수에는 `@Composable` 주석이 있어야 합니다.
- 이 주석을 통해 이 함수가 데이터를 UI로 변환하게 되어 있다는 것을 Compose 컴파일러에 알립니다.

```
@Composable
fun Greeting(name: String) {
    Text(text = "Hello $name!")
}
```
- Composable 함수를 이용하면 UI의 구성 과정에 집중하기보다는 앱의 모양을 설명하여 앱의 UI를 **프로그래매틱** 방식으로 정의할 수 있습니다.
- Composable 함수는 *인수를 허용*하여 앱 로직이 UI를 설명하거나 수정할 수 있게 해줍니다.

## 주석
![[Pasted image 20240606223420.png]]
- 주석은 *코드에 추가 정보를 첨부하는 방법입니다.*
- 주석 선언의 시작 부분에 `@`문자를 접두사로 추가하여 적용합니다.
- 속성, 함수, 클래스를 비롯한 다양한 코드 요소에 주석을 달 수 있습니다.
- 주석은 **매개변수**를 받을 수 있습니다.
- 매개변수는 주석을 처리하는 도구에 추가 정보를 제공합니다.
	- ex. `@Preview(showBackground = true)`


## Compose UI 계층구조
- Composable 함수는 여러 UI 요소를 설명할 수 있습니다.
- 그러나 개발자가 *UI 요소 정렬 방법에 관한 가이드*를 제공하지 않으면 Compose는 개발자가 원지 않는 방식으로 요소를 정렬할 수도 있습니다.
- 따라서 **계층 구조**를 이용해 하위 구성요소를 포함하는 방법을 알아봅니다. 
- Compose의 세 가지 기본 표준 레이아웃 요소는 Composable 함수인 `Column`, `Row`, `Box`입니다.

![[Pasted image 20240606225840.png]]
- `Row` 컴포저블 내의 각 하위 요소는 *한 행에 가로로 나란히 배치됩니다.*


## 후행 람다 문법
- Kotlin은 *마지막 매개변수가 함수일 때* 함수를 매개변수로 함수에 전달하는 특수한 문법을 제공합니다.
- 함수를 매개변수로 전달하면 **후행 람다 문법**을 사용할 수 있습니다.
- 괄호 안에 함수를 넣는 대신 괄호 밖 중괄호 안에 넣을 수 있습니다.

- 괄호 안에 함수를 넣는 방법 (번거로움)
```
Row(
    content = {
        Text("Some text")
        Text("Some more text")
        Text("Last text")    
    }
)
```

- 괄호 밖 중괄호 안에 후행 람다 문법을 이용하여 처리하는 방법 (깔끔함)
```
Row {
    Text("Some text")
    Text("Some more text")
    Text("Last text")
}
```


## Jetpack Compose의 리소스
- 리소스는 코드에서 사용하는 추가 파일과 정적인 콘텐츠를 의미합니다.
- 예를 들어 비트맵, 사용자 인터페이스 문자열, 애니메이션 지침 등이 있습니다.
- 이미지와 문자열 등 애플리케이션 리소스는 독립적인 유지관리가 가능하도록 항상 코드로부터 분리해야 합니다.
- **리소스 엑세스**
	- 프로젝트의 `R` 클래스에서 생성된 리소스 ID로 리소스에 엑세스할 수 있습니다.
	- `R` 클래스는 안드로이드에서 자동으로 생성되는 클래스로, 프로젝트에 있는 *모든 리소스의 ID를 포함*합니다.


## 앱에 이미지 추가
- `painterResource()` 함수는 **드로어블 이미지 리소스를 로드**하고 리소스 ID(ex. `R.drawable.androidparty`)를 인수로 사용합니다.
- `painterResource()` 함수를 호출한 후 `Image` 컴포저블을 추가하고 `painter`의 인수로 전달합니다.


## Padding
![[Pasted image 20240607010046.png]]
- 패딩은 수정자로 사용되므로 모든 컴포저블에 적용할 수 있습니다.
- `padding` 수정자는 패딩 값을 정의하는 선택적 인수를 사용합니다.
```
// This is an example.
Modifier.padding(
    start = 16.dp,
    top = 16.dp,
    end = 16.dp,
    bottom = 16.dp
)
```


>(5) Reference
- https://developer.android.com/codelabs/basic-android-kotlin-compose-text-composables?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-3%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-text-composables#2