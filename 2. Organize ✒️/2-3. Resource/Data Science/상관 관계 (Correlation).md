>(1) 날짜: 2025.05.20
>(2) 태그(주제/카테고리): #correlation #datascience 

>(3) Link
- [[Data Science]]
- [[Statistics]] : 수학적으로 직접적인 연관이 있음
---

> Correlation은 두 변수가 얼마나 관련이 있는지를 판단하는 데 사용되는 통계적 기술이다. 두 정량적인 변수(quantitative variables) 사이의 인과 관계를 추론할 수 없을 때 사용한다.

## Scatter Plot으로 두 변수 간 패턴을 확인하자.
두 변수를 산점도(Scatter Plot)를 통해 시각화하면 관계를 대략적으로 확인할 수 있다.
- 양의 관계(positive relationship)
- 음의 관계(negative relationship)
- 관계 없음(no relationship)

## Variance and Covariance

### Variance
분산(variance)은 한 변수에 대한 **산포도**이다. 산포도는 **평균으로부터 흩어진 정도**를 의미한다. 편차를 제곱하는 것은 양수와 음수가 상쇄되어 없어지지 않도록 하기 위해서이며, `n-1`로 나누는 것은 **표본(sample)** 에서의 분산이 더 작게 나오는 경향을 보정하기 위해 **자유도(degree of freedom)** 개념을 도입한 것이다. 만약 **모집단(population)** 에 대한 분산을 계산하는 것이 목적이라면 `n`으로 나누면 된다.
# $$ S_x^2=\frac{\sum_{i=1}^{n}(x_i-\bar{x})^2}{n-1} $$

### Covariance
공분산(covariance)은 두 변수가 함께 움직이는 정도를 계산한 값이다. 여기서의 `n-1`도 분산에서와 동일한 의미를 갖는다. 값이 양수라면 positive relationship, 음수라면 negative relationship, 0에 가까운 경우 관계가 없다고 할 수 있다.
# $$ cov(x, y)=\frac{\sum_{i=1}^{n}(x_i-\bar{x})(y_i-\bar{y})}{n-1} $$

### Covariance의 한계
covariance는 표준 편차(standard deviations) 의 크기에 의존한다는 문제점이 있다. 표준 편차가 크면 당연히 공분산도 크게 나온다. 데이터의 스케일은 모두 다르기 때문에, 이는 적절한 판단 기준이 될 수 없다.

## Correlation Coefficients
상관 계수(correlation coefficients) 는 데이터 크기에 상관없이 두 변수의 관계만 반영한 수치이다.

### Pearson's Coefficient r

# $$ r_{xy}=\frac{cov(x, y)}{S_xS_y} $$

### Spearman's Coefficient rho
위 공식의 한계를 보완하기 위해 고안되었다.


>(5) Reference

