---
layout: post
title: "최상단으로 이동하는 Top버튼"
categories:
  - Markup
tags:
  - html
  - jsp
  - javascript
  - css
  - function
---

## 최상단으로 이동하는 Top버튼.

### Source

Step1. CSS
```css
<style type="text/css">

  a #MOVE_TOP_BTN {
      position: fixed;
      right: 2%;
      bottom: 50px;
      display: none;
      z-index: 999;
  }
</style>
```

<br>

Step2. Javascript
```html
<script type="text/javascript">

$(function() { 
  $(window).scroll(function() { 
    if ($(this).scrollTop() > 300) { 
      $('#MOVE_TOP_BTN').fadeIn(); 
    } else { } });

    $("#MOVE_TOP_BTN").click(function() {
        $('html, body').animate({
            scrollTop : 0
        }, 400);
        return false;
    });
});

</script>
```

<br>

Step3. 사용
```html
  <a id="MOVE_TOP_BTN" href="#">TOP</a>
```