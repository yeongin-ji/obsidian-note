>(1) 날짜: 2024.06.07
>(2) 태그(주제/카테고리): #Kotlin #Null #Elvis

>(3) Link
- [[Kotlin]]
---

## `null`의 정의
> Kotlin에서는 `null`을 사용하여 변수와 연결된 값이 없음을 나타낼 수 있습니다.


## `null`의 허용
- `null`을 허용하는 유형: `null`을 보유할 수 *있음*
- `null`을 허용하지 않는 유형: `null`을 보유할 수 *없음*

- `null`을 보유하도록 명시적으로 지정하는 경우에만 `null`을 할당할 수 있음
- **변수를 Nullable type으로 정의해야 함!**
	- 유형 끝에 `?`연산자를 추가
	- ex. `String?`


## Nullable 변수의 처리
- 다음과 같은 코드는 오류가 발생합니다.
```
fun main() {
    var favoriteActor: String? = "Sandra Oh"
    println(favoriteActor.length)
}
```
- Kotlin은 **Null Safety**를 위해서 잠재적으로 `null`이 될 수 있는 변수에서 호출이 발생하지 않도록 보장하기 때문입니다.
- 변수의 멤버에 엑세스하는 경우 해당 변수는 `null`일 수 없습니다.
	- 그럼에도 불구하고 엑세스 하려는 경우 **런타임 오류**가 발생합니다.

## `null`검사
-  변수에 엑세스하여 `null`을 허용하지 않는 유형을 처리하기 전에변수가 `null`인지 확인하는 프로세스를 의미합니다.
- Kotlin 컴파일러는 `null`을 허용하는 유형에 대해 `null` 검사를 강제하여 런타임 오류를 방지합니다.
- `null`을 허용하는 값을 `null`을 허용하지 않는 유형으로 사용하려면 `null` 검사를 명시적으로 실행해야 합니다.


## `?.` 안전 호출 연산자
![[Pasted image 20240607204127.png]]
- `null`이 될 수 있는 값의 멤버에 엑세스 할 때는 `?.` 연산자를 통해 *안전하게 호출*해야 합니다.
- 만약 해당 값이 실제로 `null`이 되는 경우, 컴파일러는 `null` 참조에 관한 멤버 *엑세스 시도를 중지*하고 `null`을 반환합니다.
- nullable이 아닌 변수에도 `?.` 연산자를 사용할 수 있으나 이는 불필요한 작업입니다. (`null`을 허용하지 않는 변수의 메서드나 속성에 관한 엑세스는 항상 안전하다고 가정하기 때문입니다.)


## `!!` 어설션 연산자
![[Pasted image 20240608074609.png]]
- 변수의 값이 실제 `null`인지 여부와 관계없이 `null`이 아님을 단언합니다.
- 이때 변수가 실제로 `null`값을 가지게 되는 경우에는 `NullPointerException` 오류가 발생할 수 있습니다.
- 따라서 변수가 항상 `null` 비허용 변수이거나 적절한 예외 처리가 설정된 경우에만 실행해야 합니다.


## `if/else` 문을 이용한 `null`검사
- null check를 수행한 경우, 이후의 본문에서는 해당 변수를 *nullable이 아닌 변수인 것처럼 처리*할 수 있습니다.
- `else` 브랜치에서는 변수가 `null`이라고 가정하고 적절한 처리에 대한 코드를 추가합니다.


## `?:` Elvis 연산자
![[Pasted image 20240608080225.png]]
- `?:` Elvis 연산자를 사용하면 `?.`안전 호출 연산자가 `null`을 반환할 때 기본값을 추가할 수 있습니다.
- `if/else` 표현식과 비슷하지만 더 직관적인 방식으로 표현됩니다.
![[Pasted image 20240608080501.png]]
- ??ㅋㅋㅋㅋㅋ

>(5) Reference
- https://developer.android.com/codelabs/basic-android-kotlin-compose-nullability?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-2-pathway-1%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-nullability#0