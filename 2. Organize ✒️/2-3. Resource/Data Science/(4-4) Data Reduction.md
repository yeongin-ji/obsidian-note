>(1) 날짜: 2025.04.03
>(2) 태그(주제/카테고리): #datascience #preprocessing #process 

>(3) Link
- [[(4) Data Preprocessing]]
---

> 데이터 분석에 필요한 정보는 최대한 **보존**하면서 **크기를 줄이는 과정**을 의미한다. Feature reduction은 변수를 줄이는 과정이라면, Data reduction은 **전체 데이터 크기를 줄이는 과정**으로 볼 수 있다. Data reduction이 더 **상위**의 개념이고, 따라서 feature 뿐만 아니라 observation을 줄이는 과정 등도 포함한다.

# Feature Selection/ Reduction
- 이전 단계에 명시된 Feature Selection/ Reduction 과정을 의미한다. 데이터를 줄이는 과정에는 당연히 feature를 줄이는 과정도 포함되기 때문이다. 이 단계에서는 데이터 분석에 유용할 것 같지 않은 feature를 **제거**한다.
# Data Filtering
- 비즈니스 목적에 관련되지 않거나 유용할 가능성이 낮은 데이터를 제거한다. 이 경우에는 **행(row)** 데이터를 의미한다. `age < 30`과 같이 **조건**을 부여하기도 한다.
# Data Summarization
- 경우에 따라 모든 상세 데이터를 보관할 필요는 없다. 요약된 데이터만 보유해도 **처리 속도**는 빨라질 뿐더러 분석도 용이해질 수 있기 때문이다.
- 예를 들어 **군집화(Clustering)** 상황에서는 모든 데이터 값을 저장하기보다, 각 클러스터의 **대표값(평균값, 중심점 등)** 만 남기는 것이 더 효율적일 수 있다.
- 점수 데이터를 **빈닝(Binning)** 을 통해 구간 별로 나누는 경우에는 모든 점수 데이터를 저장하는 것 보다 각 **구간 별 데이터**만 가지고 있는 것이 더 효율적일 것이다.
# Concept Hierarchy
- 데이터가 계층적인 구조를 형성할 때, **하위** 개념을 **상위** 개념으로 **교체**하여 데이터의 양을 줄이는 기법이다.
- 이는 **Data Summarization과 비슷**하며, 같은 내용을 어렵게 풀어 쓴 것 같은 느낌도 있다. (내의견)
- 예를 들어, 어떤 회사 조직이 `Company-Department-Section` 와 같은 **계층**을 이루고 있을 때, 상위 계층인 Department-level에서의 분석으로도 **충분**하다면, 하위 계층인 Section-level은 **생략**하는 것이 더 효율적일 수 있다.
# Data Compression
> 원본 데이터를 압축하기 위해 인코딩(encoding) 혹은 변환(transformation) 을 사용한다. 압축은 크게 무손실 압축과 손실 압축으로 나누어진다.
## 무손실 압축(Lossless Compression)
데이터를 압축했다가 풀었을 때, 즉 **재구성(Reconstructing)** 했을 때 원본 데이터가 **100% 복원**되는 방식이다. 관련된 아래의 기법들을 참고할 수 있다.
- Run-length encoding
- Area image compression
- DPCM and predictive coding
- Entropy encoding
- Adaptive dictionary algorithms (ex. LZW)
- DEFLATE
- Chain codes
## 손실 압축(Lossy Compression)
데이터를 압축했다가 **재구성**할 때, 완전히 복원하지 못하고 원본 데이터의 **근사치(approximation)** 만 복원할 수 있는 방식이다. 관련된 아래의 기법들을 참고할 수 있다.
- Reducing the color space to the most common colors in the image
- Chroma subsampling
- Transform coding
- Fractal compression
# Numerosity Reduction
> Numerocity는 'a large number'를 의미한다. 따라서 크기가 큰 데이터를 **대체 가능한(alternative)** **더 작은(smaller)** 데이터 표현을 선택함으로써 데이터의 양을 줄이는 기법을 의미한다.
## Parametric methods
데이터는 **수학적 모델(model)** 을 학습하는데 사용하고, 학습된 모델의 파라미터(parameter) 만 저장하는 방식이다.
### 선형 회귀 모델(Linear Regression Model)
예를 들어, 주어진 몸무게, 키 데이터 셋이 있다면 이를 선형 회귀 알고리즘을 통하여 데이터를 가장 잘 나타낼 수 있는 직선을 그리고, 그 직선에 대한 **파라미터만 저장**한다.
## Non-parametric methods
데이터를 줄이는 데 모델을 사용하지 않는 방식이다. 대표적으로 아래 세 가지 방식이 있다.
### Discretization (Binning)
연속형 수치 데이터를 **범주화**하여 각 구간에 대한 정보만 저장하는 방식이다. 구간을 나눌 때에는 **bin의 개수**를 정하는 것이 중요하다. 데이터 수가 적을 경우에는 구간을 달리하면 분포가 달라 보일 수 있다.

- **Equal width bins**
	- 데이터의 분포에 상관없이 전체 범위를 **동일한 간격**으로 나누는 방식이다.
	- 각 구간의 **폭(Width)** 은 **(최대값 - 최소값) / N** 이다.
	- 단순하지만, **치우친(skewed)** 데이터에는 적합하지 않을 수 있다.
	- 이 방법은 데이터를 **평활화(smoothing)** 하거나 **노이즈(noise)** 가 있는 데이터를 처리하는 데 사용된다. 먼저 데이터를 **정렬**한 후, 계산된 값을 각각의 구간에 분배한다. 아래의 세 가지 접근법을 참고하자.
		- Smoothing by bin **means**
			- 각 구간의 값이 해당 구간의 **평균값**으로 대체된다.
		- Smoothing by bin **median**
			- 각 구간의 값이 해당 구간의 **중앙값**으로 대체된다.
		- Smoothing by bin **boundary**
			- 각 구간의 **경계(boundary)** 가 최소값, 최대값으로 정의된다.
			- 각 구간의 값은 **가장 가까운 경계**의 값으로 대체된다.
- **Equal frequency bins**
	- 데이터의 각 구간이 **같은 빈도 수**를 가지도록 범주화하는 방식이다.
	- 치우친 데이터를 다루는 데 좋은 방법이지만, 범주형 특징을 다룰 때 **문제**가 발생할 수 있다.
- **Entropy-based Partitioning**
	- **의사결정 트리(decision tree)** 를 사용하는 방법이다.
	- 이러한 접근 방식은, 구간의 대부분 값이 동일한 클래스 레이블에 해당하도록 최적의 분할을 찾습니다.
	- ==(이해 안됨 나중에 다시 보기)==
### Clustering
클러스터링 알고리즘을 사용하여 데이터의 **군집(Cluster)** 을 만드는 기법이다. 각 클러스터의 대표값만 유지하고 세부적인 데이터는 버린다.
### Sampling
원본 데이터에서 더 작은 샘플을 추출하는 기법이다.
- Simple random sampling
- Systematic sampling
- Stratified random sampling
- Probability-Proportional-to-Size random sampling


>(5) Reference

