<template v-if="this.answers">

  <ScoreBoard :winCount="this.winCount" :loseCount="this.loseCount"/>

  <h1 v-html="this.question"></h1>

  <template v-for="(answer, index) in answers" :key="index">
    
    <label>
      <input 
        :disabled="this.answerSubmitted"
        type="radio" 
        name="options" 
        :value="answer"
        v-model="this.chosenAnswer"
        >
        <span v-html="answer"></span>
    </label><br>
  </template>


  <button v-if="!this.answerSubmitted" @click="this.submitAnswer()" class="send" type="button">Send</button>

  <section class="result" v-if="this.answerSubmitted">
    <h4 v-if="this.chosenAnswer == this.correctAnswer" v-html="'&#9989;Congratulations. the answer ' + correctAnswer + ' is correct.'"></h4>
    <h4 v-else>&#10060; I'm sorry, you picked the wrong answer. The correct is {{ correctAnswer }}</h4>
    <button class="send" type="button" @click="getNewQuesion">Next question</button>
  </section>

</template>

<script>
import ScoreBoard from './components/ScoreBoard'
export default {

  name: 'App',
  components: {
    ScoreBoard
  },
  data(){
    return {
      chosenAnswer: undefined,
      question: undefined,
      incorrectAnswer: undefined,
      correctAnswer: undefined,
      answerSubmitted: false,
      winCount: 0,
      loseCount: 0
    }
  },
  computed: {
    answers() {
      var answers = this.incorrectAnswer ? JSON.parse(JSON.stringify(this.incorrectAnswer)) : [];
      answers.splice(Math.round(Math.random() * answers.length), 0, this.correctAnswer);
      return answers;
    }
  },
  methods: {
    submitAnswer() {
      if(!this.chosenAnswer){
        alert('Pick one of the options')
      } else {
        this.answerSubmitted = true;
        if(this.chosenAnswer == this.correctAnswer){
          this.winCount++;
        } else {
          this.loseCount++;
        }
      }
    },
    getNewQuesion(){
      this.answerSubmitted = false;
      this.chosenAnswer = undefined;
      this.answer = undefined;
      this.axios
      .get('https://opentdb.com/api.php?amount=1&category=18')
      .then((response) => {
        this.question = response.data.results[0].question
        this.incorrectAnswer = response.data.results[0].incorrect_answers
        this.correctAnswer = response.data.results[0].correct_answer;
      })
    }
  },
  created(){
    this.getNewQuesion();
  }
}

//https://opentdb.com/api.php?amount=1&category=18
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  max-width: 960px;
}

#app input[type=radio]{
  margin: 12px 4px;
}

#app button.send {
  margin-top: 12px;
  height: 40px;
  min-width: 120px;
  padding: 0 16px;
  color: #FFF;
  background-color: #1867c0;
  border: 1px solid #1867c0;
  cursor: pointer;
}

</style>
