<template>
   <button class="answers" :class="{'selected':selected}">
                <div id="" class="hover1" ></div>
                <span id="btntext"><slot></slot></span>
    </button> 
</template>
  
  <script>
  export default {
    name: 'answer',
    props: {
      iscorrect:Boolean,
      selected:Boolean,
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
.answers {
  overflow: hidden;
  display: flex;
  align-items: center;
  position: relative;
  background: #eda9a9;
  color: rgb(0, 0, 0);
  padding: 10px 40px;
  padding-left: 12px;
  border: none;
  width: 100%;
  margin-bottom: 10px;
  border-radius: 50rem;
  font-size: medium;
  font-weight: bold;
  cursor: pointer;
}

.answers:hover,.selected{
  transition: all 0.5s;
  color: aliceblue;
  background-color: #be3459;
}
  </style>
  