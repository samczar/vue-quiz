<template>
  <div>
    <div>
      <b-jumbotron>
        <template slot="lead">{{currentQuestion.question}}</template>

        <hr class="my-4">

        <p>List of answers</p>

        <b-button variant="primary" href="#">Submit</b-button>
        <b-button variant="success" href="#">Next...</b-button>
      </b-jumbotron>
    </div>
  </div>
</template>
<script>
export default {
  props: ["currentQuestion"]
};
</script>

