>(1) 날짜: 2025.03.11
>(2) 태그(주제/카테고리): #PyLongObject 

>(3) Link
- [[Python]]
---

C, Java와 같은 프로그래밍 언어와는 다르게 Python은 메모리 크기가 허용하는 한 숫자를 **무한히** 크게 표현할 수 있다.

## PyLongObject
내부적으로 배열 형태로 숫자를 저장하며, 여러개의 워드를 이용해 숫자를 표현한다.
```
struct _longobject {
    PyObject_VAR_HEAD
    digit ob_digit[1];
};
```

## Pros.
- 정수 표현 범위가 늘어난다!

## Cons.
- 너무 큰 숫자를 다루게 되면 연산 속도가 느려짐


>(5) Reference

