<template>
  <div>
    <form>
      <div>
        <span v-for="(rating,index) in ratings" :key="index">
          <input
            type="radio"
            :value="rating"
            v-model="userRating"
            class="rating"
            @change="selectUserRate"
          />
          <label class="form-check-label" :for="rating">{{rating}}</label>
        </span>
      </div>
      <button class="btn" @click.prevent="clear">Clear Rating</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'userRatings',

  props: ['selectedUserRating'],
  data() {
    return {
      ratings: [1, 2, 3, 4, 5],
      userRating: []
    }
  },
  mounted() {
    this.userRating = this.selectedUserRating
  },
  methods: {
    clear() {
      this.$emit('clearRate', this.userRating = null)
      return this.userRating = null
    },
    selectUserRate() {
      this.$emit('selectedRate', this.userRating)
    }

  },


}
</script>

<style scoped>
.rating {
  margin-left: 0.2em;
}
.btn {
  border-radius: 2px, 2px;
  border: 1px solid black;
  font-size: 0.5em;
  background-color: black;
  color: aliceblue;
  margin-bottom: 1.9em;
}
</style>