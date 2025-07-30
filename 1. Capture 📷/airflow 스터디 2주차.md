>(1) 날짜: 
>(2) 태그(주제/카테고리):

>(3) Link
- 
---

![[Pasted image 20250714200807.png]]
야후 finance 종목 중 마음에 드는 것 선정하면 관련된 최신 뉴스 가져와서 요약 및 감정분석해서 슬랙으로
-> 이 워크플로우를 airflow로 특정 순서에 따라 발생하는 작업의 흐름을 자동화

이전에 워크플로우를 관리했던 방법: cron 사용
그러나 문제가 있었다. airbnb에서 워크플로우를 만듦

어디서 많이 사용?
- ELT/ ETL
- 비즈니스 운영
- MLOps
- 인프라

장점
- pure python
- 동적으로 데이터 파이프라인을 조정가능
- 활성화 된 커뮤니티
- 확장성과 직관적인 UI (모니터링하기 좋음)

Airflow 코어 컴포넌트
- web server
- scheduler: 실행 시점 등을 담당
- database: 모든 워크플로우에 대한 메타데이터
- executer: 작업이 실행되는 위치와 방법을 정의
- worker
- trigger: 

DAG: Directed Acyclic Graph
- 순환하지 말아야한다.

Astronomer
- 관리형 airflow 클러스터 제공
- 사용자가 인프라를 관리하지 않고도 airflow 사용할 수 있도록 지원

airflow 실행하는 것은 어렵다.
이번 스터디에선 로컬에서 실행하지 않고 astro를 사용한다.

homebrew 컴퓨터 클럽: https://ko.wikipedia.org/wiki/%ED%99%88%EB%B8%8C%EB%A3%A8_%EC%BB%B4%ED%93%A8%ED%84%B0_%ED%81%B4%EB%9F%BD

가용한 공간 알아보는 방법
![[Pasted image 20250714203804.png]]

에어플로우 최소 메모리 4GB 정도?

Astro CLI
- 데이터 오케스트레이션을 위한 명령줄 인터페이스
	- 로컬 머신에서 airflow를 쉽게 실행할 수 있다.

DAG는 파이썬 코드로 작성하는데, 두 가지 방법이 있다.
1. 함수 정의
2. 데코레이터 사용

>(5) Reference

