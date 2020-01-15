---
layout: post
title: "스크롤시 따라오는 Floating Banner"
categories:
  - Markup
tags:
  - html
  - jsp
  - javascript
  - function
---

## Javascript dispaly 속성을 이용한 접었다 펴는 버튼.

### Source

Step1. Javascript
```html
<script type="text/javascript">

  $(window).scroll(function(event){
    
    if(jQuery(window).scrollTop() > jQuery(".banner").offset().top) {
      jQuery("#chase").css("position", "fixed");
    } else if (jQuery(window).scrollTop() < jQuery(".banner").offset().top) {
      jQuery("#chase").css("position", "static");
    }

  });

</script>
```

<br>

Step2. body 구현
```html
<s_sidebar_element>
  <div class="banner">
    <div id="chase" style="top:0px;"> 내용 </div>
  </div>
</s_sidebar_element>
```


출처: https://wendys.tistory.com/98 [웬디의 기묘한 이야기]