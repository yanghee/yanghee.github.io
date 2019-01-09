---
layout: post
title: Entity Matching 1
tags: [python, database, entity, entity matching, translate, study]
---

1편은 Entity Matching 란 무엇인지,에 대해 알아본다.



먼저 무엇인지 알기 전에 어떻게 사용할 수 있는지 확인하자.

## Entity Matching은 어디에 쓸 수 있을까?


세상에는 같은 의미지만 다른 형태의 데이터들이 많다.
예를 들면 KR과 KOREA는 형태는 다르지만 의미는 같다.


형태는 다르지만 의미가 같은 데이터는 사람이 확인했을 때는 매칭이 가능하지만 컴퓨터가 이를 알기는 쉽지 않다.

<style type="text/css"> 
span{
    font-weight:500;
}

.divid-table{
   
    width:47%!important;

}
.left{
     float:left;
}

</style>

<label class="left" style="width:50%;">Table A</label> 
<label class="left" style="width:50%;padding-left:3%;">Table B</label>

<table class="left divid-table">
<tbody>
<tr><th> </th><th>Name</th><th>City</th><th>State</th><th>Age</th></tr>
<tr><td class="tuple-label">a1</td><td>Dave Smith<br></td><td>Madison<br></td><td>WI</td><td>30</td></tr>
<tr><td class="tuple-label">a2</td><td>Joe Wilson<br></td><td>San Jose<br></td><td>CA</td><td>44</td></tr>
<tr><td class="tuple-label">a3</td><td>Dan Smith<br></td><td>Middleton<br></td><td>WI</td><td>53</td></tr>
</tbody>
</table>

<table class="left divid-table" style="margin-left:5%;"> <tbody>
<tr><th></th><th> Name </th><th> City </th><th> State </th><th> Sex</th></tr>
<tr><td class="tuple-label">b1</td><td> David D. Smith </td><td> Madison </td><td> WI </td><td>M</td></tr>
<tr><td class="tuple-label">b2</td><td> Daniel W. Smith </td><td> Middleton </td><td> WI </td><td>M</td></tr>
</tbody>
</table>

<div style="clear:both"></div>
<p>
</p>
<div>
<label class="left" style="">Table C</label>
<table class="" > <tbody>
<tr><td></td><th> Name </th><th> City </th><th> State </th><th> Sex</th><th> Age</th></tr>
<tr><td class="tuple-label">c1</td><td> David D. Smith </td><td> Madison </td><td> WI </td><td>M</td><td>30</td></tr>
<tr><td class="tuple-label">c2</td><td> Daniel W. Smith </td><td> Middleton </td><td> WI </td><td>M</td><td></td></tr>
<tr><td class="tuple-label">c3</td><td> Joe Wlison </td><td> San Jose </td><td> CA </td><td></td><td>44</td></tr>
</tbody>
</table>
</div>
<br>


Table A와 Table B를 통합하여 Table C를 만들어야 한다고 가정해보자.
그러기 위해서 (a1, b1)이 같은 사람임을 확인하는 작업이 먼저 필요하게 된다.
데이터가 적을 경우 사람이 직접하는 것이 가능하지만 데이터가 많아지게 되면 사람이 이를 하나씩 보면서 확인하는 것은 어렵다. 
이 때 Entity Matching 을 이용하면 쉽고, 편하게 데이터 통합이 가능하게 된다.


---


## Entity Matching : EM ??

### Entity 란 무엇일까 ?
Entity의 사전적 의미는 사람이 생각하는 개념 또는 정보의 세계에서는 의미있는 정보의 단위다. 
쉽게 말하면 Table A는 사람들의 정보를 담고 있는 테이블이다. 
이를 명칭할 때 물리적 구조를 의미하는 Table은 "A", 논리적 구조를 의미하는 Entity는 “사람”이다. 

### Entity Matching란?
사전적 의미는 동일한 Entity를 식별하는 것으로, 데이터 통합 및 데이터 정리를 위한 중요한 작업이다. 
데이터베이스나 탐색 엔진 저장과 같은 이질적인 데이터 집합에 저장된 데이터를 연결하거나 통합하기 위한 핵심적인 방법이다.
다른 이름으로는 복제 확인, 레코드 연결, 엔티티 해상도 또는 참조 조정 등으로 불린다.

<b>Table A와 Table B로 예를 들면, A테이블에 있는 사람들과 B테이블에 있는 사람들이 일치하는지 맞추는 것이다. </b>




2편에서는 실제 Entity Matching 수행 과정을 살펴본다.






