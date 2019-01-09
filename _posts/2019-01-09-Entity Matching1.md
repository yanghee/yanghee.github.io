---
layout: post
title: Entity Matching 1
tags: [python, database, entity, entity matching, translate, study]
---

1편은 Entity Matching 란 무엇인지에 대해 알아보려고 한다.



먼저 무엇인지 알기 전에 왜 필요한지 확인하자.

## Entity Matching은 왜 필요할까?


세상에는 같은 의미지만 다른 형태의 데이터들이 많다.
예를 들면 KR과 KOREA는 형태는 다르지만 의미는 같다.<br>

이렇게 <b>서로 의미가 같지만 형태가 다른 데이터는 사람이 확인했을 때는 매칭이 가능하지만 <u>컴퓨터로 매칭하기는 어렵다.</b>


<style type="text/css"> 
span{
    font-weight:500;
}

.divid-table{
   
    width:47%!important;

}
.tuple-label{
width:10%;
}
.left{
     float:left;
}

</style>

<label class="left" style="width:50%;"><b>Table A</b></label> 
<label class="left" style="width:50%;padding-left:3%;"><b>Table B</b></label>

<table class="left divid-table">
<tbody>
<tr><th> </th><th>Name</th><th>City</th><th>State</th><th>Age</th></tr>
<tr><td class="tuple-label">a1</td><td>Dave Smith<br></td><td>Madison<br></td><td>WI</td><td>30</td></tr>
<tr><td class="tuple-label">a2</td><td>Joe Wilson<br></td><td>San Jose<br></td><td>CA</td><td>44</td></tr
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
<table class=""  > <tbody>
<tr><td></td><th> Name </th><th> City </th><th> State </th><th> Sex</th><th> Age</th></tr>
<tr><td class="tuple-label">c1</td><td> David D. Smith </td><td> Madison </td><td> WI </td><td>M</td><td>30</td></tr>
<tr><td class="tuple-label">c2</td><td> Daniel W. Smith </td><td> Middleton </td><td> WI </td><td>M</td><td></td></tr>
<tr><td class="tuple-label">c3</td><td> Joe Wlison </td><td> San Jose </td><td> CA </td><td></td><td>44</td></tr>
</tbody>
</table>
</div>
<br>

위에 서로 다르게 입력된 Table A와 Table B가 있다. <br> 
Table A와 Table B를 통합하여 Table C를 만들어야 한다고 가정해보자. 


그러기 위해서 두 테이블 안의 사람 데이터들이 서로 같은 사람임을 확인하는 작업이 필요하다. 
비교가 가능한 칼럼은 두 테이블에 동일하게 존재하는 Name, City, State 이다. 이 세 개의 칼럼 데이터를 간단히 분석해보면 Name은 의미는 같지만 형식이 다른 데이터이고, State와 City는 형식과 의미가 같은 데이터라는 것을 알 수 있다. 
 

형식과 의미가 같은 State와 City 데이터는 쉽게 비교가 가능하지만 이 두 칼럼의 데이터가 일치하다고 같은 사람이라고 판단하기는 어렵다. 
그렇기 때문에 의미는 같지만 형식이 다른 Name 데이터를 비교해야한다.


<b>
Name의 데이터를 사람이 비교해보면 David D. Smith와 Dave Smith는 다르게 쓰여있지만 같은 사람임을 알 수 있다. 하지만 컴퓨터가 비교했을 때 David D. Smith와 Dave Smith는 다른 사람으로 판단한다.
</b>


다른 형식, 같은 의미 데이터의 매칭은 데이터가 적을 경우 사람이 직접하는 것이 가능하다. 
하지만 데이터가 양이 많을 경우 사람이 데이터 매칭 여부를 확인하기 힘들고, 많은 "시간"과 "노력"이 필요하게 된다.


위와 같은 상황에서 이용할 수 있는 방법이 바로 <b>"Entity Matching"</b> 이다.  <br>
Entity Matching을 이용하면 다른 형식, 같은 의미 데이터의 매칭이 쉽고, 편하게되어 손쉬운 데이터 통합이 가능하게 된다.

<br>
---
<br>
<br>

그럼 왜 필요한지 알았으니 Entity Matching 이 무엇인지 알아보자.

## Entity Matching : EM ??

### Entity 란 무엇일까 ?
Entity의 사전적 의미는 사람이 생각하는 개념 또는 정보의 세계에서는 의미있는 정보의 단위다. <br>
쉽게 말하면 Table A는 사람들의 정보를 담고 있는 테이블이다. 
이를 명칭할 때 물리적 구조를 의미하는 Table은 "A", 논리적 구조를 의미하는 Entity는 “사람”이다. 

### Entity Matching란?
동일한 Entity를 식별하는 것으로, 데이터 통합 및 데이터 정리를 위한 중요한 작업이다. 
데이터베이스나 탐색 엔진 저장과 같은 이질적인 데이터 집합에 저장된 데이터를 연결하거나 통합하기 위한 핵심적인 방법이다.
다른 이름으로는 복제 확인, 레코드 연결, 엔티티 해상도 또는 참조 조정 등으로 불린다. <br>
<b>Table A와 Table B로 예를 들면, A테이블에 있는 사람들과 B테이블에 있는 사람들이 일치하는지 맞추는 것이다. </b>
<br>
<br>
<br>
<br>
<br>




2편에서는 실제 Entity Matching 수행 과정을 살펴본다.
<br>
<br>







