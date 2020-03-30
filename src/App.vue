<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <QuestionList :questions="questions"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import QuestionList from './components/QuestionList';

export default {
  name: 'App',
  components: {
    HelloWorld,
    QuestionList
  },
  data: function() {
    return {
      questions: [
        {id: 1, title: 'Question 1', answers: ['Answer 1', 'Answer 2', 'Answer 3']},
        {id: 2, title: 'Question 2', answers: ['Answer 1', 'Answer 2', 'Answer 3']},
        {id: 3, title: 'Question 3', answers: ['Answer 1', 'Answer 2', 'Answer 3']}
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
