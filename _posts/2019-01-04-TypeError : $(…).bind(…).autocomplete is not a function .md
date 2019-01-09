---
layout: post
title: TypeError $(…).bind(…).autocomplete is not a function 
tags: [AngularJS, Jquery, javascript, library, jquery-ui, jquery-ui.min, autocomplete, TypeError, error]
---

TypeError : $(…).bind(…).autocomplete is not a function 

위의 에러가 발생한다면 jquery-ui의 script 선언이 min버전으로 되어있는지 확인해야한다.

만약 min.js 라면 <b>“jquery-ui.min.js” -> “jquery-ui.js”</b>  수정해줘야한다. 

---

라이브러리 사용시 xxxxx.min.js 일 경우 min은 minify의 약자로 공백과 줄바꿈을 제거하여 용량을 줄인 파일을 의미한다. 
min.js 파일을 사용하게 되면 시간과 네트워크 사용량을 줄일 수 있는 장점이 있다. 

하지만 minify하는 과정에서 내가 사용하는 기능이 지원을 안하게 되었는지 확인이 필요하다.

jquery-ui.js

  -jquery-ui.min.js
