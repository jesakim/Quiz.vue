<template>
    <div class="dropbtn `+iscorrect+`" onclick="showdropdown(this)">
            <i class="icon right fa-regular fa-circle-`+icon+`"></i>
            <p class="broptxt">{{ question }}</p>
            <i class="icon left fa-solid fa-chevron-down"></i>
        </div>
    <div class="dropdown">
                <span class="itemstxt" >Your answer</span>
                <div class="items yours">{{selectedAnswer}}</div>
                <span class="itemstxt" >Correct answer</span>
                <div class="items correct">{{ correctAnswer }}</div>
                <span class="itemstxt" >Explanation</span>
                <div class="items exp">{{explanation}}</div>
        </div>
 </template>
   
   <script>
   export default {
     name: 'result',
     props: {
        question:String,
        selectedAnswer:String,
        correctAnswer:String,
        explanation:String,
     }
   }
   </script>
   
   <!-- Add "scoped" attribute to limit CSS to this component only -->
   <style scoped>
   .dropdown {
  /* display: none; */
  /* width: 100%; */
  border-radius: 0px  0px 20px 20px;
  background-color: #eda9a9;
  position: relative;
  pointer-events: none;
  /* z-index: -1; */
  padding: 10px 50px 1px 50px;
}
.dropdown .items {
  background-color: #eb8383;
  color: rgb(255, 255, 255);
  padding: 10px 20px;
  border-radius: 10px;
  margin-top: 10px;
  margin-bottom: 30px;
}
.dropdown .itemstxt {
  font: 1rem sans-serif;
  font-size: large;
}
.dropbtn {
  position: relative;
  background: #be3459;
  color: aliceblue;
  padding: 10px 20px;
  border: none;
  border-radius: 20px 20px 0px 0px;
  /* width: 100%; */
  margin-top: 25px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  transition: all 1s;
}
   </style>
   