>(1) 날짜: 2025.03.13
>(2) 태그(주제/카테고리): #Lambda #필터함수 #맵함수 

>(3) Link
- [[Python]]
---

> **람다 함수(lambda function)** 는 함수를 간결하게 표현할 수 있는 **축약 표현**이다. **람다 표현식(lambda expression)** 이라고도 불리며 일반 함수와 다르게 `return`문도 없고 **지역 변수**를 선언할 수도 없다.

``` python
# 람다 함수를 이용한 덧셈
add = lambda x, y: x + y
print('100과 200의 합: ', add(100, 200))

# 인라인 람다 함수와 인자를 이용한 덧셈
print('100과 200의 합: ', (lambda x, y: x + y)(100, 200))
```
간단하게 **변수에 할당**하여 사용하거나 두 번째 예시처럼 **인라인**으로 사용할 수도 있다.
그런데 위와 같이 사용하기보다는 **필터 함수**, **맵 함수**와 더 자주 사용한다.

# 필터 함수(Filter function)
> `filter()` 함수는 반복 가능한 요소들을 넣어 그 리턴 값이 참인 것만 묶어서 반환한다. 적용시킬 함수와 반복가능 객체만 전달해 주면 되기 때문에 lambda 함수와 함께 쓰면 유용하다.

## lambda 함수를 이용한 간략화된 filter 사용
``` python
ages = [34, 39, 20, 18, 13, 54]

print('성년 리스트: ')
for a in filter(lambda x: x >= 19, ages):
	print(a, end=' ')
```

## 결과 리스트 추출 (람다 응용)
``` python
n_list = [-30, 45, -5, -90, 20, 53, 77, -36]  # 음수 추출하는 것이 목적
minus_list = list(filter(lambda x: x < 0, n_list))  # filter 결과는 iterator 객체
print('음수 리스트: ', minus_list)
```

# 맵 함수(Map function)
> `map()` 함수는 **반복 가능한 자료형**의 각 요소에 대해서 지정된 **매핑 함수**를 적용하여 **반복 가능한 자료형**을 반환한다.

## lambda 함수를 이용한 간략화된 map 사용
``` python
a = [1, 2, 3, 4, 5, 6, 7]  # 제곱 리스트 만들기가 목적
square_a = list(map(lambda x: x**2, a))  # map 결과는 iterator 객체
print(square_a)
```


>(5) Reference

