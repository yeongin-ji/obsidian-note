>(1) 날짜: 2025.04.03
>(2) 태그(주제/카테고리): #datascience #process 

>(3) Link
- [[데이터 분석 프로세스]]
---

> Data Inspection은 Data Exploration 작업과 Suitability check 작업으로 나눌 수 있다.

## Data Exploration
수집한 데이터를 쭉 살펴보며 해당 데이터의 일반적인 특징을 이해하는 과정이다. 
**EDA(Exploratory Data Analysis)** 라고도 부른다.

1. 자료 전체를 대표할 수 있는 값 **(Central Tendency)** 를 확인한다.
	- 평균(mean)
	- 중앙값(median)
	- 범위(range): `max - min`
	- 분산(variance)
	- 표준 편차(standard deviation)
2. **데이터 분포(distribution)** 확인한다.
	- 정규 분포(Normal distribution)
3. **이상치(outliers)** 확인한다.
4. 속성 사이의 **상관 관계(correlation)** 확인한다.

이러한 작업을 할 때에 여러 가지 시각화 툴을 사용할 수 있는데, 대표적으로 **matplotlib**이 있다.
- Box Plot
- Histogram
- Scatter Plot
- Pie Chart
- etc..

## Suitability Check
데이터 탐색 후, 해당 데이터가 비즈니스 목적과 부합하는지를 확인하는 과정이다. 경우에 따라 **Data Curation** 과정에서 진행하기도 한다. 이 단계에서는 비즈니스 도메인에 대한 **전문성**을 가진 사람이 필요하다.


>(5) Reference

