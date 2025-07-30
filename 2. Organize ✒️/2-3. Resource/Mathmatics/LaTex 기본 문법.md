>(1) 날짜: 2025.04.14
>(2) 태그(주제/카테고리): #Math #LeTex 

>(3) Link
- [[Mathmatics]]
---

> 옵시디언에서 LaTex를 이용하여 수식을 표현해보자!

# LaTex란?
고급 문서 조판 시스템으로, 학술 문서, 기술 문서, 과학 및 수학 관련 문서를 포함한 다양한 유형의 문서를 만드는데 주로 사용된다. 특별히 무엇인가의 약자는 아니고, 그리스어에서 차용된 TeX(=Technique)와 Lamport라는 사람의 이름을 따서 LaTex라고 부른다.

# LaTeX 사용 방법
## 인라인(Inline)
아래와 같이 인라인 수식을 `$$`로 감싸서 표현한다.
``` LaTeX
$E=mc^2$
```
$E=mc^2$

## 블록(Block)
독립된 수식 줄을 만들고 싶을 때는 아래와 같이 `$$ ... $$` 로 표현한다.
``` LaTeX
$$\frac{-b \pm \sqrt{b^2-4ac}}{2a}$$
```
$$
\frac{-b\pm\sqrt{b^2-4ac}}{2a}
$$
# LaTeX 기본 문법
## 첨자
- `\dot{a}` 
	- $\dot{a}$
- `\hat{a}`
	- $\hat{a}$
- `\vec{a}`
	- $\vec{a}$
- `a^2`
	- $a^2$
- `a^{2+2}`
	- $a^{2+2}$
- `a_n`
	- $a_n$
- `a_{m,n}`
	- $a_{m,n}$
- `x_i^2`
	- $x_i^2$
## 연산자
- `\pm`
	- $\pm$
- `\mp`
	- $\mp$
- `\times`
	- $\times$
- `\div`
	- $\div$
- `\nabla`
	- $\nabla$
- `\cdot, \ast, \star, \circ, \bullet`
$$\cdot, \ast, \star, \circ, \bullet$$
- `\frac{\partial f}{\partial x} \hat{\imath}`
$$\frac{\partial f}{\partial x} \hat{\imath}$$
## 관계
- `=, \ne, \neq, \equiv, \not\equiv`
$$=, \ne, \neq, \equiv, \not\equiv$$
- `\approx, \propto`
$$\approx, \propto$$
- `\le, \leq, \lneq`
$$\le, \leq, \lneq$$
- `\ge, \geq, \gneq`
$$\ge, \geq, \gneq$$
## 기하
- `\bar{q}, \bar{abc}, \overline{q}, \overline{abc}`
$$\bar{q}, \bar{abc}, \overline{q}, \overline{abc}$$
## 루트
- `\sqrt{x}`
$$\sqrt{x}$$
- `\sqrt[n]{x}`
$$\sqrt[n]{x}$$
## 분수
- `\frac{a}{b}`
$$\frac{a}{b}$$
- `\frac{\frac{a}{b}}{\frac{c}{d}}`
$$\frac{\frac{a}{b}}{\frac{c}{d}}$$
## 정적분
- `\int_a^b f(x) \, dx`
$$\int_a^bf(x)\,dx$$
## 부정적분
- `\int f(x) \, dx`
$$\int f(x) \, dx$$
## 미분
- `\frac{d}{dx} f(x)`
$$\frac{d}{dx} f(x)$$
## 시그마(합계)
- `\sum_{i=1}^{n} i`
$$\sum_{i=1}^{n} i$$
## Product
- `\prod_{i=1}^{n} i`
$$\prod_{i=1}^{n} i$$
## 한계값
- `\lim_{x \to \infty} f(x)`
$$\lim_{x \to \infty} f(x)$$
## 행렬

``` LaTex
$$
\begin{matrix}
a & b \\
c & d
\end{matrix}
$$
```
$$
\begin{matrix}
a&b \\
c&d
\end{matrix}
$$
``` LaTex
$$
\begin{pmatrix}
a&b \\
c&d
\end{pmatrix}
$$
```
$$
\begin{pmatrix}
a&b \\
c&d
\end{pmatrix}
$$
## 그리스 문자
`\alpha, \beta, \gamma, \theta, \lambda`
$$\alpha, \beta, \gamma, \theta, \lambda$$
`\Gamma, \Delta, \Theta, \Lambda, \Omega`
$$\Gamma, \Delta, \Theta, \Lambda, \Omega$$




>(5) Reference
- [옵시디언 심화: LaTeX](https://kaminik.tistory.com/entry/%EC%98%B5%EC%8B%9C%EB%94%94%EC%96%B8-%EC%8B%AC%ED%99%94-LaTeX#LaTeX%EB%9E%80?)
- [LaTex 문법 정리](https://blog.naver.com/songsite123/222851026847)
- https://www.latex-project.org/
- [더 많은 문자](https://jjycjnmath.tistory.com/117)

