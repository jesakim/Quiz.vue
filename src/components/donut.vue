<template>
    <div class="donut" :style="{'--percent':percent*10}">
        <p class="donuttxt">{{percent}}/10</p> 
        </div> 
 </template>
   
   <script>
   export default {
     name: 'donut',
     props: {
        percent:Number,
     }
   }
   </script>
   
   <!-- Add "scoped" attribute to limit CSS to this component only -->
   <style scoped>
.donut {
  height: 200px;
  width: 400px;
  overflow: hidden;
  margin-top: 50px !important;
  margin-bottom: 50px !important;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  --percent:0;
  margin: auto;
}
.donut::after {
  content: "";
  border: 50px solid;
  border-color: #e7e6e6 #e7e6e6 #be3459 #be3459;
  position: absolute;
  left: 0;
  top: 0;
  height: 400px;
  width: 400px;
  box-sizing: border-box;
  border-radius: 50%;
  transform: rotate(calc(1deg * (-45 + var(--percent) * 1.8)));
  -webkit-animation: fillanim 2s linear forwards;
          animation: fillanim 2s linear forwards;
}
.donut .donuttxt {
  color: #be3459;
  font-size: 5rem;
  position: absolute;
  bottom: 0;
  margin-bottom: 0;
}
@keyframes fillanim{
    0%{transform: rotate(-45deg);}
    50%{transform: rotate(135deg);}
}
   </style>
   