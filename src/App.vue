<template>
  <b-container fluid>
    <div id="app">
      <b-row>
        <b-col>
          <Header />

          <product-component :products="products" />
          <h2>{{selectTurtle}}</h2>
          <checkbox-component :turtles="turtles" @selectedTurtle="selectTurtle = $event" />
          <h2>Emails</h2>
          <Email :emails="emails" />
          <user-component :users="users" />
          <h1>{{message}}</h1>
          <input-component :msg="message" @inputChangeValue="message = $event" />
          <QuizBox :currentQuestion="questions[index]" />
        </b-col>
      </b-row>
    </div>
  </b-container>
</template>

<script>
import Header from "./components/Header.vue";
import QuizBox from "./components/QuizBox";
import Email from './components/Email';
import User from './components/User';
import Input from './components/Input';
import Checkbox from './components/Checkbox';
import Guesser from './components/Guesser';
import Product from './components/Product';
import ProductVue from './components/Product.vue';

export default {
  name: "app",
  components: {
    Header,
    QuizBox,
    Email,
    'user-component': User,
    'input-component': Input,
    'checkbox-component': Checkbox,
    'guess-component': Guesser,
    'product-component': ProductVue
  },
  data() {
    return {
      selectTurtle: [],
      turtles: ['Donatello', 'Michenlangelo', 'Rafael'],
      questions: [],
      index: 0,
      message: 'Default Message',
      emails: [
        {
          id: 1,
          subject: 'Send Email 1',
          message: 'Lorem'

        },
        {
          id: 2,
          subject: 'Send Email 2',
          message: 'Lorem'

        },
        {
          id: 3,
          subject: 'Send Email 3',
          message: 'Lorem'

        }
      ],
      users: [
        {
          name: 'Samczar',
          rating: 4

        },
        {
          name: 'Danjiel',
          rating: 4
        },
        {
          name: 'Andras',
          rating: 3
        }],
      products: [{
        name: 'Apple Juice',
        yearOfProduction: '20/11/18',
        expireDate: '24/12/2019'
      },
      {
        name: 'Orange Juice',
        yearOfProduction: '19/07/2019',
        expireDate: '21/18/2020'
      },
      {
        name: 'Pineapple Juice',
        yearOfProduction: '11/06/2018',
        expireDate: '06/09/2019'
      }]
    }
  },
  mounted: function () {
    fetch(
      "https://opentdb.com/api.php?amount=10&category=27&difficulty=medium&type=multiple",
      {
        method: "get"
      }
    )
      .then(response => {
        return response.json();
      })
      .then(data => {
        this.questions = data.results;
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
