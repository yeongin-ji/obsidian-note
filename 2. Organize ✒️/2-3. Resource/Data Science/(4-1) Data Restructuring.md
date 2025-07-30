>(1) 날짜: 2025.04.03
>(2) 태그(주제/카테고리): #datascience #preprocessing #process 

>(3) Link
- [[(4) Data Preprocessing]]
---

> 데이터의 구조를 재정비하는 과정이다. 이는 주로 **테이블 단위의 조작**을 의미한다.
# Table Decomposition
재구조화를 위해 테이블을 분해하는 방법이다. 테이블을 두 개, 혹은 그 이상 분해한다. 분해된 테이블 중 하나만 분석하기도 하고, 둘 다 사용하기도 한다.
## Horizontal Decomposition
모든 Column을 유지하고 Record 단위로 분해한다. 
Record를 그룹핑하기 위한 **Splitting condition**을 사용한다. e.g. `Age<30`
## Vertical Decomposition
모든 Record를 유지하고 Column 단위로 분해한다.
분해된 테이블들은 반드시 **같은 Primary key**를 취해야 한다.

# Table Merge
두 개 혹은 그 이상의 테이블을 하나의 테이블로 병합하는 과정이다. ML 알고리즘은 **하나의 테이블만 입력**받기 때문에 이 과정이 반드시 필요하다. 또한 테이블을 병합할 때에는 하나의 **Primary key** 혹은 **Foreign key** 열을 공유하는 테이블 간 병합만 가능하다는 점을 주의해야 한다.

>(5) Reference

