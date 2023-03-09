<template>
  <div class="stepper" >
        <div class="step" ><span  class="after" >Info</span></div>
        <div class="line" :class="{'passed': step>=1 }"></div>
        <div class="step" ><span  class="after" >Quiz</span></div>
        <div class="line" :class="{'passed': step>=2 }" ></div>
        <div class="step" ><span  class="after" >Result</span></div>
    </div>
</template>

<script>
export default {
  name: 'stepper',
  props: {
    step:Number,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.stepper {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-around;
  /* padding: 0 20px; */
  color: #be3459;
  /* margin-top: 10px; */
}
.stepper.none {
  display: none;
}
.stepper .step {
  font-size: larger;
  position: relative;
}
/* .stepper .step .after {
  position: absolute;
  top: 100%;
  left: -50%;
} */
.stepper .line {
  height: 5px;
  width: 40%;
  border: 1px solid #be3459;
  margin: 0;
  border-radius: 50rem;
}
.stepper .line.passed {
  background-color: #be3459;
}
</style>
