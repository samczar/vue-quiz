<template>
  <div>
    <input :value="msg" @input="changedValue" type="text" />
    {{message}}
  </div>
</template>

<script>
export default {
  name: 'input-component',
  props: ['msg'],
  data() {
    return {
      message: ''
    }
  },
  methods: {
    changedValue(event) {
      this.message = event.target.value
      this.$emit('inputChangeValue', this.message)
    }
  }
}
</script>

<style>
</style>