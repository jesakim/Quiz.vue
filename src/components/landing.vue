<template>
    <h1 class="text">Welcome to AWS Cloud Practitioner<br> Knowledge Test</h1>
    <ul class="info_list">
        <li class="item"><h3 class="">You only have 30 sec to answer a question</h3></li>
        <li class="item"><h3 class="">Each question have only one correct answer</h3></li>
        <li class="item"><h3 class="">Pass the quiz and see how many questions you can answer correctly out of 10 !</h3></li>
    </ul>
        <!-- <div class="error" >Username should contain only letters and whitespaces ( 3 characters min )</div>
    <div class="form-outline">
        <input type="text" id="loginName" class="" placeholder=" "/>
        <label class="form-label" for="loginName" id="NameLabel">Your Name</label>
    </div> -->

    <button class="btn" @click='$emit("update:modelValue",$event.target.value=1)'>
        <div id="" class="hover1"></div>
        <span id="btntext" >Start Now</span>
    </button>
  </template>
  
  <script>
  export default {
    name: 'landing',
    props: {
        modelValue:Number,
    },
    methods:{
        next:function(){

           this.modelValue++;
        }
    },
    emits: ['update:modelValue'],
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
.text {
  color: #be3459;
  text-align: center;
  margin-top: 50px;
  cursor: default;
}
.text:hover {
  color: #eda9a9;
}

.btn {
  width: 100%;
  padding: 10px;
  margin-top: 20px;
  border-radius: 50rem;
  border: none;
  background-color: #eda9a9;
  font-size: larger;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  color: rgb(0, 0, 0);
  padding: 10px 40px;
  padding-left: 12px;
  border: none;
  border-radius: 50rem;
  cursor: pointer;
}
.btn #btntext {
  position: relative;
}
.btn:hover {
  transition: all 0.5s;
  color: aliceblue;
  background-color: #be3459;
}
  </style>
  