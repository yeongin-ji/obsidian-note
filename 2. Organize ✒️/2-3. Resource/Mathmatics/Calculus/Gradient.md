>(1) 날짜: 2025.04.20
>(2) 태그(주제/카테고리): #math #gradient #calculus 

>(3) Link
- [[Calculus]]
---

> The gradient of a differentiable function $f:\mathbb{R}^2\rightarrow\mathbb{R}$ is defined as:

$$\nabla f(x, y)=(\partial f/\partial x, \partial f/\partial y)$$
이러한 함수에서 gradient는 ==순간적인 함수 증가 방향과 그 최대 변화율을 나타내는 **벡터**==이다. 아래의 예시 함수 gradient를 보면, 3차원 표면에 접하는 부분에 화살표를 긋고 마치 $\mathbb{R}^3$ 벡터인 것으로 착각할 수 있다.
![[Pasted image 20250420013032.png|250]] $\leftarrow\quad f(x, y)=-(cos^2{x}+cos^2{y})^2$

그러나, 실은 아래에 표현된 것과 같이 해당 점에서의 순간적인 함수 증가 방향과 그 최대 변화율을 나타내는 $\mathbb{R}^2$상의 벡터라는 것을 확인할 수 있다. 입력 공간이 $\mathbb{R}^2$상의 평면이기 때문에 한 점에서 움직일 수 있는 방향이 **무한**하므로, gradient는 이러한 방향들 중 **변화율**이 가장 큰 방향을 나타내는 벡터와 일치한다.

## Existence of partial derivatives $\nRightarrow$ Existence of the gradient 
> 해당 함수의 편미분이 존재한다고 해서, 반드시 gradient가 존재하는 것은 아니다.

다음과 같은 함수를 고려해보자.
$$f(x, y)=xy/(x^2+y^2)$$

이 함수는 임의의 점 $(0, 0)$에서의 $x$ 에 대한 partial derivative $f_x$가 존재하며, 그 값은 $0$이다. 이미 $y=0$으로 고정한 시점에서 $f_x=0$ 임을 알 수 있다. 같은 맥락으로 $f_y=0$ 이다.

하지만, 사실 이 함수는 **gradient가 존재하지 않는다.** 심지어 $(0, 0)$ 에서 연속하지도 않다.


>(5) Reference

