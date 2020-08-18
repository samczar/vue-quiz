<template>
  <div>
    <input type="text" placeholder="Input Guess" v-model="model" />
    <button @click="submitGuess">Submit Guess</button>
  </div>
</template>

<script>
export default {
  name: 'Guesser',
  data() {
    return {
      guess: '10',
      model: ''
    }
  },
  methods: {
    submitGuess() {
      if (this.model === this.guess) {
        alert('Correct Guess')
      } else {
        alert('Try Again')
      }
    }
  }
}
</script>

<style>
</style>