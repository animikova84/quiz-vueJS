<template>
  <div id="app">
    <app-header></app-header>
    <main>
      <app-navigation @navigate="navigateHandler($event)"
                      :selectedNavigation="selectedNavIndex"
                      :nav-items="games.quizes">
      </app-navigation>
<!--      <app-home :questions="questions"></app-home>-->
<!--      <app-login></app-login>-->
<!--      <app-register></app-register>-->
      <app-create-quiz :quizes="games.quizes" :questions="questions" @create="createHandler($event)"></app-create-quiz>
    </main>
    <app-footer></app-footer>
<!--    <question-list :questions="questions" />-->

  </div>
</template>

<script>
  import games from './games.json';

 // import AppHome from './components/Home';
  //import AppLogin from './components/Login';
//   import AppRegister from './components/Register';
  import AppHeader from './components/core/Header';
  import AppFooter from './components/core/Footer';
  import AppNavigation from './components/core/Navigation';
  import AppCreateQuiz from './components/CreateQuiz';
  //import QuestionList from './components/QuestionList';

export default {
  name: 'App',
  components: {
   // AppHome,
   // AppLogin,
  //  AppRegister,
    AppCreateQuiz,
    AppHeader,
    AppFooter,
    AppNavigation
    // QuestionList
  },
  data: function() {
    return {
      games,
      selectedNavIndex: 0
    }
  },
  methods: {
    navigateHandler(ind) {
      this.selectedNavIndex = ind;
    },
    createHandler({ questionId, question: name, content}) {
      const selectedQuiz = this.games.quizes.find(t => t.id === questionId );
      selectedQuiz.questions = selectedQuiz.questions.concat({ name, content });
    }
  },
  computed: {
    questions() {
      return this.games.quizes[this.selectedNavIndex].questions;
    }
  }
}
</script>

<style>
  @import url("https://fonts.googleapis.com/css?family=Lato&display=swap");
  body {
    font-family: "Lato", sans-serif;
  }

  #app {
    font-family: 'Lato', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  /** ************************************** **/

  main div.navigation {
    background: #b771b0;
    font-size: 20px;
    text-align: left;
    display: flex;
  }

  main div.navigation ul {
    display: inline-block;
    text-align: left;
  }

  main div.navigation ul:nth-child(1) {
    width: 75%;
  }

  main div.navigation ul:nth-child(2) {
    width: 20%;
    text-align: right;
  }

  main div.navigation li {
    list-style: none;
    display: inline-block;
    margin-right: 3%;
  }

  main div.navigation ul:nth-child(2) li {
    width: 100%;
  }

  main div.navigation li a {
    padding: 1%;
    color: white;
    text-decoration: none;
    font-weight: bold;
  }

  main div.navigation li a:hover {
    text-decoration: underline;
  }

  main div.navigation li a.active {
    text-decoration: underline;
    border-bottom: 1px solid red;
  }

  main div.main-content {
    display: flex;
  }

  main div.main-content .content-navigation {
    width: 20%;
    border-right: 3px solid whitesmoke;
    border-left: 3px solid whitesmoke;
  }

  main div.main-content .subject-info {
    padding: 1%;
  }

  main div.main-content .subject-info p {
    font-size: 18px;
  }

  main .main-content .content-navigation ul {
    margin: 0;
    padding: 0;
  }

  main div.main-content .content-navigation ul li {
    list-style-type: none;
    padding: 10%;
    font-size: 23px;
    cursor: pointer;
    text-align: left;
  }

  main div.main-content .content-navigation ul li:hover {
    background: whitesmoke;
  }

  main div.main-content .content-navigation ul li:active,
  main div.main-content .content-navigation ul li.active{
    border-right: 5px solid #b771b0;
  }

  main div.main-content .content-navigation ul li a {
    color: black;
    text-decoration: none;
  }

  main .content-info {
    width: 80%;
    padding: 1%;
    font-size: 18px;
    display: block;
  }

  main .content-info .user-form input {
    padding: 1%;
    width: 25%;
    border: none;
    border-bottom: 1px solid black;
    font-size: 16px;
    font-family: inherit;
  }

  main .content-info .user-form input:focus {
    background: rgb(255, 248, 198);
  }

  main .content-info .user-form .form-group {
    margin-bottom: 1%;
  }

  main .content-info .user-form .form-group img {
    vertical-align: bottom;
  }

  main .content-info .user-form button {
    padding: 1%;
    background: #b771b0;
    color: white;
    border: none;
    width: 10%;
    font-size: 16px;
    cursor: pointer;
  }

  main .content-info .user-links a {
    color: black;
    text-decoration: none;
    font-weight: normal;
    margin: 2%;
  }

  main .content-info .user-links a:hover {
    color: #b771b0;
    text-decoration: underline;
  }

  main .content-info .user-links .active-route {
    color: #b771b0;
    text-decoration: underline;
  }

  /** ************************************** **/

  .btn {
    padding: 1%;
    background: #b771b0;
    color: white;
    width: 10%;
    font-size: 16px;
    cursor: pointer;
    border: 1px solid white;
    display: block;
    margin: 0 auto;
    margin-top: 1%;
    margin-bottom: 1%;
  }

  .btn:hover {
    color: #b771b0;
    background: white;
    border: 1px solid #b771b0;
    text-decoration: underline;
  }

  div.form-group {
    margin-top: 1%;
    margin-bottom: 1%;
  }

  div.form-group input, option, select {
    padding: 1%;
    width: 25%;
    border: none;
    border-bottom: 1px solid black;
    font-size: 16px;
    font-family: inherit;
    text-align: center;
    text-align-last: center;
  }

  select {
    -webkit-appearance: none;
    -moz-appearance: none;
    text-indent: 1px;
    text-overflow: '';
  }

  .content-preview {
    text-align: left;
    word-wrap: break-word;
    display: block;
    width: 100%;
  }
</style>
