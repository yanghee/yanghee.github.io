---
layout: post
title: Entity Matching 2
tags: [python, database, entity, entity matching, translate, study,py_entitymatching]
---


2편은 Entity Matching 수행 과정에 대해서 알아보려고 한다. <br>
<br>

## The Process of Performing Entity Matching

Entity Matching은 크게 총 3단계로 이루어져있다.

1. 요구사항 분석 단계 : 요청자와 논의하여 요구사항을 이해한다. 
2. 개발 단계  : 정확한 EM Workflow을 개발하기 위해 데이터 샘플을 실험하고, 요구사항 분석 단계에서의 요구 사항을 충족시킨다.
3. 제작 단계  : 개발 단계를 통해 EM Workflow이 개발되면 전체 데이터로 실행하여 제작에 투입한다. 이 단계에서는 확장성, 품질 모니터링, 충돌 복구 및 로깅이 중요하다.
<br>

### EM Workflow의 두가지 기본 단계 : Blocking and Matching

실질적인 Entity Matching에 대한 개발은 EM Workflow의 두 단계인 Blocking, Matching에 있다. 
 * Blocking 단계 :  확실하게 일치하지 않는 Tuple 쌍을 제거하는 단계이다. 테이블의 사이즈가 클 경우 시간과 비용이 많이 들기 때문에 Blocking 단계가 필요하다. 
 * Matching 단계 : Tuple 쌍만 생각하여 각각의 쌍에 대해 일치하는 Tuple인지 불일치하는지 예측하는 단계이다. 

 (Tuple : 테이블의 단일 행으로, 해당 관계에 대한 단일 레코드를 포함하는 것 ex)아래 테이블의 a1,a2,a3...)


![Example Blocking Matching]({{ site.baseurl }}/assets/img/example-blocking-matching.png)

위의 테이블 A와 B은 일치한다고 가정한다. 각 Tuple은 사람에 대한 정보이다. 


먼저 Blocking 단계를 수행한다. Blocking 단계에서 모든 Tuple 쌍들이 열거된다. 모든 Tuple 쌍은 (a1,b1),(a1,b2),(a2,b1),(a2,b2),(a3,b1),(a3,b2)이다. 두 Tuple의 State 속성 값이 일치 하지 않으면 동일한 사람이 아니라는 사람의 경험적 방법을 사용하여 정확히 일치 하지 않는 Tuple 쌍을 제거할 수 있다. 이 단계에서 (a2,b1),(a2,b2)는 제거된다. 


Matching 단계에서는 blocking단계를 통과한 Tuple 쌍들만을 고려하여 각각 쌍들에 대해 “일치+” 또는 “일치하지 않음-”을 예측하여 표시한다. 

<br>

### 개발 단계

사용자는 데이터 샘플을 사용하여 정확한 EM 워크플로우를 찾는 단계이다. 

각각 100만 개의 Tuple이 있는 두 개의 테이블 A,B를 매칭하려고 한다. 100만 개의 테이블은 크기가 크기 때문에 다운 샘플링을 통해 작은 버전의 테이블을 만든다. 그 결과 10만개 Tuple이 있는 A’와 B’ 테이블이 만들어진다. (다운 샘플링 : 크기가 큰 테이블 원래의 테이블을 참조하여 크기가 작은 버전의 테이블을 만든다.)<br>

 A’와 B’를 이용해 blocker X와 blocker Y를 실험하여 최상의 blocker를 찾는다. blocker X가 최상의 blocker라는 판단이 서면 후보 Tuple 쌍 세트인 C를 얻는다. <br>

C에서 샘플링을 하여 S를 얻는다. 사용자는 이 S에 “일치” 또는 “불일치”로 라벨링을 한다.  라벨링한 S를 G라고 한다. 이 G를 이용하여 교차 유효성 검사를 한다. 이 때 더 높은 정확도를 얻는 matcher V를 얻는다. 그 다음  matcher V를 이용하여 C의 Tuple 쌍 들의 “일치” 또는 “불일치”를 예측한다. <br>

마지막으로 사용자는 C의 “일치”또는 “불일치”를 예측한 데이터에 관해 품질 검사를 수행 한 다음 이전 단계를 적절히 수정하고 디버그하여 개발 단계를 수행한다. EM workflow 에 대해 만족하는 정확성이 나올때까지 반복한다.
<br>

![Example Dev Stage]({{ site.baseurl }}/assets/img/example-dev-stage.png)

<br>

### 제작 단계 
사용자가 전체 데이터에 개발단계에서 찾은 EM Workflow를 실행하는 단계이다.
개발 단계에서 사용자가 만족하는 정확성이 나오면 제작 단계가 된다. 제작 단계에서는 원본 테이블 A와 B을 이용하여 EM Workflow를 수행한다. 

---

<br><br>

지금까지 Entity Matching 수행 단계에 대해서 설명하였다. <br>
Blocking and Matching는 EM에서 중요한 단계로 Blocker, Matcher의 정확도에 따라 EM의 결과는 크게 좌우된다.
그래서 Blocker, Matcher의 성능을 높이기 위해 여러 개를 사용하기도 하고 알고리즘을 개발하여 다양한 방법으로 정확도를 높이고 있다. 
<br><br>

---

###참고한 자료 <br>
* py_entitymatching 0.3.0 documentation - http://anhaidgroup.github.io/py_entitymatching/v0.3.x/user_manual/overview.html <br>
* “엔티티 매칭을 위한 프레임워크의 비교” - 과학기술 정보연구원 전문연구위원 김홍기
<br>
