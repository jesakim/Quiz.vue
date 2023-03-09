<template>
  <stepper :step="step"></stepper>
  <div class="container">
    <!-- {{ qanda }} -->
    <landing v-if="step==0" v-model="step" ></landing>
    <div v-if="step==1">
    <h1 class="qst" >{{currentQuestion.question}}</h1>
    <answer :selected="isselected1" @click="select(1,currentQuestion.options[0].content)">{{currentQuestion.options[0].content}}</answer>
    <answer :selected="isselected2" @click="select(2,currentQuestion.options[1].content)">{{currentQuestion.options[1].content}}</answer>
    <answer :selected="isselected3" @click="select(3,currentQuestion.options[2].content)">{{currentQuestion.options[2].content}}</answer>
    <answer :selected="isselected4" @click="select(4,currentQuestion.options[3].content)">{{currentQuestion.options[3].content}}</answer>
    <div class="twobtn">
        <button class="nextbtn nohover">
            {{questionsIndex+1}}/10
        </button>
        <button class="nextbtn" @click="next" :disabled="answerContent=='no answer selected'">
            Submit
        </button>
    </div>
  </div>
  <div v-if="step==2">

    <donut :percent="result"></donut>
    <result v-for="(question, index) in qanda"
    :question="question.question"
    :selectedAnswer="selectedAnswers[index]"
    :correctAnswer="question.options[question.answers.correct-1].content"
    :explanation="question.answers.comment"
    ></result> 
  </div>
  </div>
</template>

<script>
import stepper from './components/stepper.vue'
import landing from './components/landing.vue'
import answer from './components/answer.vue'
import donut from './components/donut.vue'
import result from './components/result.vue'

export default {
  name: 'App',
  components: {
    stepper,
    landing,
    answer,
    donut,
    result
  },
  data:function(){
    return{
      step:0,
      isselected1:false,
      isselected2:false,
      isselected3:false,
      isselected4:false,
      currentQuestion:{},
      qanda:[],
      questionsIndex:0,
      answerContent:'no answer selected',
      selectedAnswers:[],
      result:0
    }
  },
  methods:{
    select:function(n,answerContent){
      this.isselected1=false;
      this.isselected2=false;
      this.isselected3=false;
      this.isselected4=false;
      if(n==1){
      this.isselected1=true;
      }else if(n==2){
      this.isselected2=true;
      }else if(n==3){
      this.isselected3=true;
      }else if(n==4){
      this.isselected4=true;
      }
      this.answerContent = answerContent
    },
    next:function(){
      this.selectedAnswers.push(this.answerContent);
      // console.log(this.selectedAnswers);
      if(this.currentQuestion.options[this.currentQuestion.answers.correct-1].content==this.answerContent){
        this.result++
      };
      console.log(this.result);
      if(this.questionsIndex < 9){
      this.questionsIndex ++;
      this.currentQuestion = this.qanda[this.questionsIndex];
      this.isselected1=false;
      this.isselected2=false;
      this.isselected3=false;
      this.isselected4=false;
      this.answerContent='no answer selected';
    }else{
      this.step=2
    }
  }
  },
  async mounted() {
    let result = await fetch('http://localhost:3001/questions')
    let data = await result.json()
    this.qanda = data.sort(function () {
      return Math.random() - 0.5;
    });
    this.currentQuestion = this.qanda[this.questionsIndex];

    }
}
</script>

<style>
.container{
  width: 100%;
  max-width: 700px;
  margin: auto;
}
.qst {
  text-align: center;
  color: #be3459;
  margin-bottom: 15px;
}
.twobtn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nextbtn {
  padding: 10px 40px;
  border-radius: 50rem;
  border: none;
  background-color: #be3459;
  color: aliceblue;
  font-size: larger;
  cursor: pointer;
  transition: color 1s, background-color 1s;
  white-space: nowrap;
}
.nextbtn.nohover {
  pointer-events: none;
}
.nextbtn:not(:disabled):hover{
  background-color: #eda9a9;
  color: black;
}
.nextbtn:disabled{
  cursor: not-allowed;
}

</style>
