---
layout: post
title: "페이지 내에서 움직이는 플로팅 버튼"
categories:
  - Markup
tags:
  - html
  - javascript
  - css
  - function
  - button
---

## 페이지 내에서 움직이는 플로팅 버튼.

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

Step1. Javascript
```html

<script type='text/javascript'>

var img_L = 0;
var img_T = 0;
var targetObj;

var count=0;

function getLeft(o){
     return parseInt(o.style.left.replace('px', ''));
}
function getTop(o){
     return parseInt(o.style.top.replace('px', ''));
}

// 이미지 움직이기
function moveDrag(e){
     var e_obj = window.event? window.event : e;
     var dmvx = parseInt(e_obj.clientX + img_L);
     var dmvy = parseInt(e_obj.clientY + img_T);
     targetObj.style.left = dmvx +"px";
     targetObj.style.top = dmvy +"px";
     return false;
}

// 드래그 시작
function startDrag(e, obj){
     targetObj = obj;
     var e_obj = window.event? window.event : e;


     if(<%=left%>==null && count != 1)
     {
    	 img_L = (getLeft(obj) * window.innerWidth )/100 - e_obj.clientX;
         img_T = (getTop(obj)* window.innerHeight)/100 - e_obj.clientY;
         count = 1;
     }
     else
     {
         img_L = getLeft(obj) - e_obj.clientX;
         img_T = getTop(obj) - e_obj.clientY;
     }
    
     document.onmousemove = moveDrag;
     document.onmouseup = stopDrag;
     if(e_obj.preventDefault)e_obj.preventDefault();
}

// 드래그 멈추기
function stopDrag(){
     document.onmousemove = null;
     document.onmouseup = null;
}


function endDrag(e, obj){
    targetObj = obj;

	$.ajax({
		type: "POST",
		url: "chat_position",
		data: {chat_left:getLeft(obj), chat_top:getTop(obj)},
		success: function(data){
		}
	});
}

</script>

```

<br>

Step3. 사용
```html


```