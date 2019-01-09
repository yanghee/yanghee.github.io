---
layout: post
title: $watch에 array를 넣을 수 있을까?
tags: [AngularJS, web, javascript, $watch]
---


Angular JS 에는 $watch라는 기능이 있다. 

공식 페이지에 나온 사용하는 틀은 아래와 같다. 
{% highlight js %}
$watch(watchExpression, listener, [objectEquality]);
{% endhighlight %}

$watch의 기능은 watchExpression의 변경이 있을 때 마다 등록된 listener 가 callback을 한다. 
JS는 비동기로 순서없이 프로그램이 진행되기 떄문에 $watch와 같은 기능은 매우 유용하게 쓰인다.

---

사실 이 글은 $watch에 대한 기능 소개가 목적은 아니다. 
 
$watch를 사용하던 중 array가 변하는 것도 알 수 있다는 사실에 감탄하여 쓰게 되었다.(사실 별 게 없다.)  

<span class="codebox">
{% highlight js %}
$scope.data1=[];
$scope.data2=[]; 

$scope.$watch('[data1,data2]',function(newValue,oldValue){     
   console.log('changed',newValue); 
})
{% endhighlight %}
</span>

이런 식으로 watchExpression 자리에 직접 배열을 인자 값을 넣어줄 수 있다!!
angular를 계속 써왔지만 이렇게 써본 것은 처음이다.



물론 객체도 가능하다.
<span class="codebox">
{% highlight js %}
$scope.info = {   
 name: 'name',    
 phone: 'phone'     
}

$scope.$watch('info', function(newValue, oldValue){     
   console.log('changed',newVal); 
}, true);
{% endhighlight %}
</span>
