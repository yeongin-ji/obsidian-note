>(1) 날짜: 2025.03.11
>(2) 태그(주제/카테고리): #Python #Iterable

>(3) Link
- [[Python]]
---

# Iterable
> Iterable 객체는 반복 가능한 객체를 의미한다.

대표적인 **iterable** 타입 객체는 다음과 같다.
- list/ dict/ set/ str/ file/ tuple/ range

# Iterator
> 값을 차례대로 꺼낼 수 있는 객체를 의미한다.

iterable 객체의 메소드 혹은 파이썬 자체 내장함수 `iter()`를 통해 iterator 객체를 생성할 수 있습니다.
``` Python
iterable_ex = [1, 2, 3]
iterator_ex = iterable_ex.__iter__()
```

### Iterator 활용 예시
Python 자체 내장함수 `next()`를 통해 iterator 객체의 값을 하나씩 꺼낼 수 있다.
더 이상 값이 없을 때는 `StopIteration` 예외가 발생한다.
``` python
>>> next(iterator_ex) 
1 
>>> next(iterator_ex) 
2 
>>> next(iterator_ex) 
3 
>>> next(iterator_ex) 
Traceback (most recent call last): 
	File "<stdin>", line 1, in <module> StopIteration
```


>(5) Reference
- https://wikidocs.net/16068

