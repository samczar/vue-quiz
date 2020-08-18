<template>
  <div>
    <div v-for="(turtle, index) in turtles" :key="index">
      <label :for="turtle">{{turtle}}</label>
      <input
        type="checkbox"
        v-model="checkedTurtle"
        :value="turtle"
        :id="turtle"
        @change="handleSelectedTurtle"
      />
    </div>
    <br />
  </div>
</template>

<script>
export default {
  name: 'checkbox-model',
  props: ['turtles'],
  data() {
    return {
      checkedTurtle: [],
    }
  },
  methods: {
    async handleSelectedTurtle() {
      await this.$emit('selectedTurtle', this.checkedTurtle)
    }
  },

}
</script>

<style>
</style>