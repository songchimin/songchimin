---
layout: post
title: "Javascript dispaly 속성을 이용한 접었다 펴는 버튼"
categories:
  - Markup
tags:
  - html
  - jsp
  - css
  - javascript
---

## Javascript dispaly 속성을 이용한 접었다 펴는 버튼.

### Source

Step1. Style
```css
<style>
  .menu a{cursor:pointer;}
  .menu .hide{display:none;}
</style>
```

<br>

Step2. Javascript
```html
<script type="text/javascript">

$(document).ready(function(){
    // menu 클래스 바로 하위에 있는 a 태그를 클릭했을때
    $(".menu>button").click(function(){
    	var submenu = $(this).next("ul");
            // submenu 가 화면상에 보일때는 위로 보드랍게 접고 아니면 아래로 보드랍게 펼치기
            if( submenu.is(":visible") ){
                submenu.slideUp();
                $("#tab").text("▼");
            }else{
                submenu.slideDown();
                $("#tab").text("▲");
            }
        });
    });
</script>
```

<br>

Step3. body 구현
```html
<li class="menu" style="list-style: none; align-content: center;">
  <button class="btn btn-outline-primary" type="button" onclick="" style="margin-bottom: 15px;" id="tab">▼</button>
  
	<ul class="hide" style="list-style: none; text-align: left; padding:0; margin: 0;">
		<li>
			숨겨진 부분
		</li>
	</ul>
</li>

```
