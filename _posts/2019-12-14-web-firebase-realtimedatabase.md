---
layout: post
title: "Web Firebase의 realtime database 읽어오기"
categories:
  - Markup
tags:
  - html
  - javascript
  - function
  - firebase
  - database
---

## Web에서 Firebase의 realtime database 읽어오기.

### Source

Step1. 선언
```html
<!-- Add Firebase products that you want to use -->
<script src="https://www.gstatic.com/firebasejs/7.5.2/firebase-auth.js"></script>
<script src="https://www.gstatic.com/firebasejs/7.5.2/firebase-firestore.js"></script>
<script src="https://www.gstatic.com/firebasejs/7.5.2/firebase-database.js"></script>
```

<br>

Step2. Javascript
```html
<script>

var firebaseConfig = {
  apiKey: "",
  authDomain: "",
  databaseURL: "",
  projectId: "",
  storageBucket: "",
  messagingSenderId: "",
  appId: "",
  measurementId: ""
};

// Initialize Firebase
firebase.initializeApp(firebaseConfig);
firebase.analytics();
var a = document.getElementById("result");
var database = firebase.database();
var messageRef = database.ref("1");

messageRef.on('child_added', function(snapshot) {
  var data = snapshot.val();
  var name = data.id;
  var message = data.text;
  var b = name + "  :  " + message +"\n";
    
    a.value += b;
    
    //출력
    document.getElementById("result").scrollTop = document.getElementById("result").scrollHeight;
});
</script>
```