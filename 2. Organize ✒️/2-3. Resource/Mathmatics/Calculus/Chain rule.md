>(1) 날짜: 2025.04.19
>(2) 태그(주제/카테고리): #math #calculus #deeplearning #derivatives

>(3) Link
- [[Calculus]]
- [[DL (Deep Learning)]]
---

# Motivation
딥 러닝(Deep Learning) 에서는 각 파라미터에 대한 오차 함수(loss function) 의 기울기를 계산하는 방법으로 ==**역전파(backpropagation)**== 를 활용한다. 아래의 역전파 프로세스에는 [[Partial derivatives]]이 밀접하게 연관되어 있다.

## Backpropagation process
- **Forward pass:** Neural network에 입력값을 전달함으로써 모델의 예측값을 계산한다.
- **Loss calculation:** 원하는 값(정답)과 예측 값의 차이, 즉 error를 계산한다.
- **Backward pass:** Error 값을 역방향으로 전파함으로써 **기울기(gradients)** 를 계산한다.

이 프로세스에서 기울기를 계산할 때 ==**Chain rule**==을 활용한다.

# Priliminary
## Composition function (합성 함수)
> A composition function is formed by applying one function to the results of another.

합성함수란, 어떤 함수의 입력값이 다른 함수의 결과값이 됨으로써 형성되는 함수이다. 만약 $f$ 와 $g$ 라는 함수가 있다면, 두 함수의 합성은 $f\circ g$ 로 표현한다. 이 표현은 아래의 등식을 만족한다.
$$(f \circ g)(x)=f(g(x))$$

# Chain rule
> The chain rule is a formula for computing the derivative of composition of two or more functions

Chain rule은 두 개 이상의 함수가 합성된 함수를 미분하는 방법이다. 고등학교에서 배운 합성함수의 미분법을 다시 표현한 것으로 보아도 무방하다. $F=f\circ g$ 일 때, $F(x)$ 에 대한 미분은 아래와 같이 구할 수 있다.

$$F'(x)=f'(g(x))g'(x)$$

이때, $y=f(u)$, 그리고 $u=g(x)$ 로 합성함수 표현을 분리해보자. 그러면 합성함수의 미분을 아래와 같이 다시 표현할 수 있다.

$$\frac{dy}{dx}=\frac{dy}{du}\cdot\frac{du}{dx}$$

$y$ 는 $u$ 에 대한 식으로 이루어져 있으므로 $x$ 에 대해 바로 미분하는 것이 어렵다. 하지만 **chain rule**을 활용하면 $y$ 의 $u$ 에 대한 미분, $u$ 의 $x$ 에 대한 미분을 ==**연쇄적으로**== 곱함으로써 $y$ 의 $x$ 에 대한 미분을 구할 수 있다.

## Chain rule: Two-variable functions
> If $w=f(x, y)$ is differentiable and if $x=x(t), y=y(t)$ are differentiable functions of $t$, then the composite $w=f(x(t), y(t))$ is a differentiable function of $t$ and

$$\frac{dw}{dt}=f_x(x(t), y(t))\cdot x'(t)\,+\,f_y(x(t), y(t))\cdot y'(t)$$
or
$$\frac{dw}{dt}=\frac{\partial f}{\partial x}\frac{dx}{dt}+\frac{\partial f}{\partial y}\frac{dy}{dt}$$

지금까지는 하나의 변수에 대한 합성함수를 다루었지만, Neural network와 같은 **Multi-variable** 상황에서는 다변수함수에 대한 합성함수 미분이 필수적이다. 이 역시 Chain rule을 통해 해결할 수 있다.

이 식을 외울 필요 없이, 아래와 같이 **Dependency Graph**를 그리면 문제를 쉽게 풀 수 있다.
![[Pasted image 20250419223827.png|200]]

더 많은 변수에 대한 Chain rule도 **DAG(Dependency Acyclic Graph)** 를 응용하면 외우지 않고도 해결할 수 있다.

## Revisited: Backpropagation in deep neural network
![[Pasted image 20250419224719.png|500]]
위와 같은 Dependency graph가 있을 때, $b$ 가 **약간 변하는 경우**를 생각해 보자. 이때 예측 결과값인 $l$ 은 얼마나 변화할까? 앞서 살펴보았던 backpropagation process를 따라가 보며 알아보자.
- **Forward pass:** $u=6$, $v=11$, $l=33$
- **Loss calculation:** 원하는 값이 $l=21$ 이라고 하면 오차 $\Delta l=12$ 이다. 우리가 $b$ 에 대해서 관심이 있다고 할 때 $b$ 를 **얼마나 조정**해야 원하는 $l$ 값을 얻을 수 있는지, 즉 $\Delta b$ 가 궁금하다.
- **Backward pass:** Chain rule을 통해 $\frac{\Delta l}{\Delta b}$, 즉 $\frac{\partial l}{\partial b}$ 을 구할 수 있다. 해당 관계식을 통해 최종적으로 $\Delta b$ 를 구할 수 있다.
### Solution
$$\begin{flalign}\frac{\partial l}{\partial b}=\frac{\partial l}{\partial v}\frac{\partial v}{\partial u}\frac{\partial u}{\partial b}&&\end{flalign}$$
$$\begin{flalign}\frac{\partial l}{\partial v}=3, \quad \frac{\partial v}{\partial u}=1, \quad \frac{\partial u}{\partial b}=2&&\end{flalign}$$
$$\begin{flalign}\therefore\frac{\partial l}{\partial b}=3\cdot1\cdot2=6 &&\end{flalign}$$

$$\begin{flalign}\partial l = \Delta l = 12&&\end{flalign}$$
$$\begin{flalign}\frac{12}{\Delta b}=6&&\end{flalign}$$
$$\begin{flalign}\therefore \Delta b=2&&\end{flalign}$$

즉, 파라미터 $b$ 를 2만큼 **감소**시켜야 원하는 $l$ 값을 얻을 수 있다는 결론에 이른다.

이처럼 Neural network를 **훈련**시킬 때 backpropagation을 사용하여 파라미터(parameter) 혹은 **가중치(weight)** 에 대한 loss function의 partial derivative을 구하게 된다.

>(5) Reference

