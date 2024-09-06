---
layout: base
title: Student Home 
description: Home Page
hide: true
---




<button class="button1" onClick="funButton()" type="button">hi</button>
<button class="button2" onClick="computerButton()" type="button">my</button>
<button class="button3" onClick="helloButton()" type="button">name</button>
<button class="button4" onClick="skibidyButton()" type="button">is</button>
<button class="button5" onClick="toiletbutton()" type="button">johan</button>
<button class="button6" onClick="boring button()" type="button">Mascarenhas</button>


<script>
  function funButton() {
    alert("Hello!!")
  }
   function computerButton() {
    alert("Woahh")
  }
   function skibidyButton() {
    alert("!WOW!!")
  }
   function toiletButton() {
    alert("CRAZY!!!")
  }
   function boringButton() {
    alert("Hee Hee!!")
  }
</script>

<style>
   .button1{
   margin-top: 20px;
   background-color: orange !important;
   }
   .button2{
   margin-top: 20px;
   background-color: blue !important;
   }
   .button3{
   margin-top: 20px;
   background-color: red !important;
   }
   .button4{
   margin-top: 20px;
   background-color: violet !important;
   }
   .button5{
   margin-top: 20px;
   background-color: blue !important;
   }
   .button6{
   margin-top: 20px;
   background-color: purple !important;
   }
   </style>


   I am in AP CSP and i am interested in software designing and computers. I am excited to take this class. I hope to get a 5 on the AP exam!!!!

   <img id="mario" src="https://art.pixilart.com/faaa938738.gif" alt="Mario" style="width:130px; position:absolute; bottom:0; left:0;">

<script>
  function moveMario() {
    var mario = document.getElementById("mario");
    var position = 0;
    var interval = setInterval(function() {
      if (position >= window.innerWidth) {
        clearInterval(interval);
      } else {
        position++;
        mario.style.left = position + "px";
      }
    }, 9);
  }

  // Start moving Mario
  moveMario();
</script>