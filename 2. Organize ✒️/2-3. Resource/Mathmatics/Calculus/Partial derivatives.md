>(1) 날짜: 2025.04.19
>(2) 태그(주제/카테고리): #math #partial #derivatives #calculus 

>(3) Link
- [[Calculus]]
---

> ==왜 배우는가?==

Deep Neural Network에서는 Computational graph(=dependency draph)를 통해 입력과 출력의 관계를 나타낸다. 그래프의 각 node는 변수(variable)를 의미하며 edge는 input/output relationship을 의미한다.

이 그래프에서 하나의 변수 값을 조정한다고 할 때, **Final output**은 어떻게 변화할 것인가? 이는 앞으로 살펴볼 **편미분(Partial derivatives)** 과 관련이 있다.

# 사전 지식(Priliminary)
## Euclidean space
> The Euclidian space $\mathbb{R}^n$ is =the set of all ==ordered n-tuples== of real numbers= with the **operation** ($+$, $\cdot$)

$$\mathbb{R}^n=\{ (x_1, x_2, ..., x_n) \ | \ x_i \in{\mathbb{R} \ \text{for} \ i=1, 2, ..., n}\}$$

여기서 핵심은 ($+$, $\cdot$) 에 대한 **연산**이 함께 정의되어야 한다는 것이다.
벡터 공간이 정의되기 위해서는 벡터 집합 $V$와 ($+$, $\cdot$) 연산이 정의되어야 한다.
각각은 벡터 덧셈($+$), 스칼라 곱($\cdot$)을 의미하며, 각 연산은 **공리(axiom)** 를 만족해야 한다.

- 벡터 덧셈($+$)
	임의의 두 벡터 $u, v \in {\mathbb{R}^n}$에 대해 다음을 만족한다.
$$	u+v=(u_1+v_1, u_2+v_2+...+u_n+v_n)	$$
- 스칼라 곱($\cdot$)
	스칼라 $a\in{\mathbb{R}}$과 벡터 $v\in{\mathbb{R^n}}$에 대해 다음을 만족한다.
$$a\cdot v=(av_1, av_2, ..., av_n)$$

## Euclidean norm ($L_2$ norm)
> $L_2$ norm of a vector $a=(a_1, ..., a_n)$

$$\|a\|_2 \ = \ \sqrt{a_1^2+a_2^2+\cdot\cdot\cdot+a_n^2}$$
norm은 벡터의 size를 의미한다.
차원에 따라 $L_1$ norm, $L_2$ norm 등으로 확장 가능하다.
특히 $L_1$ norm은 **Manhattan norm**으로 불린다.

## Ordinary derivative (상미분)
> The derivative of a function of ==one variable== measures the sensitivity to change of the function value (output value) with respect to a change in its argument (input value)

$$f'(x)=\frac{df}{dx}=\lim_{\Delta x \to 0} \frac{f(x+\Delta x)-f(x)}{\Delta x}=\lim_{\Delta x \to 0} \frac{\Delta f}{\Delta x}$$

상미분은 일변수함수에 대한 미분을 의미하며, 입력 값의 변화에 대한 출력 값의 변화의 민감도, 즉 **순간변화율**을 측정하는 것이다.

# Partial derivative
> A bivariate function (or ==two-variable function==) is a function whose inputs consist of two numbers

## Motivation
다음의 **이변수함수**를 고려해보자.
$$f(m, h)=m/h^2$$
우리가 고등학교 과정에서 배웠던 $f:\mathbb{R}\rightarrow \mathbb{R}$ 형태의 함수와는 다르게, $f:\mathbb{R}^2\rightarrow \mathbb{R}$ 형태로 두 개의 변수가 입력된다. 시각화를 한다면 (weight, height) 의 모든 순서쌍에 대응되는 함수값을 표현해야 하므로 3차원 그래프가 될 것이다.

이러한 $z=f(x, y)$ 형태의 함수를 **미분**하려면 어떻게 해야 할까?

## Approach
> ==Fix one variable== and treat it as ordinary derivative

이 문제의 접근은 간단하게 하나의 변수를 **고정**하여 나머지 한 변수에 대한 상미분(ordinary derivative)을 푸는 것으로 해결할 수 있다. 즉, $(x_0, y_0)$ 에서의 $x$ 에 대한 $f$ 의 **편미분(partial derivative)** 을 고려할 수 있다.

다시 말하면, $y$ 를 특정 상수로 고정한 $z=f(x, y_0)$ 를 $x$에 대해 미분하는 것으로 이해할 수 있다.

## Partial derivative for two-variable function
> The **partial derivative** of $f(x, y)$ with respect ro $x$ at the point $(x_0, y_0)$ is

$$\left.\frac{\partial f}{\partial x}\right|_{(x_0, y_0)}=\lim_{h \to 0} \frac{f(x_0+h, y_0)-f(x_0, y_0)}{h}$$
미분에 대한 기호는 Ordinary derivative와 Partial derivative를 **구분**하기 위해 $d$ 가 아닌 $\partial$ 을 쓴다.

$$\left.\frac{d}{dx} f(x, y_0)\right|_{x=x_0}$$
혹은 위와 같이 표현하기도 한다. 이때에는 $\partial$ 이 아닌 $d$ 를 사용했는데, $y$ 를 상수로 고정한 상황에서는 ordinary derivative가 되기 때문이다.

## Second-order partial derivative
> When we differentiate a function $f(x, y)$ twice, we produce its ==second-order derivatives==. Several notations are as follows:

$$\frac{\partial^2 f}{\partial x^2} \, \text{or} \, f_{xx}, \quad \frac{\partial^2 f}{\partial y^2} \, \text{or} \, f_{yy}, \quad \frac{\partial^2 f}{\partial x \partial y} \, \text{or} \, f_{yx}, \quad \frac{\partial^2 f}{\partial y \partial x} \, \text{or} \, f_{xy},$$
where
$$\frac{\partial^2 f}{\partial x^2}=\frac{\partial}{\partial x}\left(\frac{\partial f}{\partial x}\right), \quad \frac{\partial^2 f}{\partial x \partial y}=\frac{\partial}{\partial x}\left(\frac{\partial f}{\partial y}\right)$$

이계도함수, 즉 Second-order derivative를 구할 때에도 partial derivative를 적용할 수 있다. $f_{xy}$ 와 같이 간단하게 표현이 가능하며, **순서**에 유의해야 한다.

>(5) Reference

