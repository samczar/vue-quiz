<template>
  <div>
    <h3>Users</h3>
    <ul v-for="(user, index) in users" :key="index">
      <li @click.prevent="selectedUser = user">
        {{user.name}}
        <span class="userRate">{{user.rating}}</span>
      </li>
      <rating-component
        v-if="selectedUser === user"
        :selected-user-rating="user.rating"
        @selectedRate="user.rating = $event"
        @clearRate="user.rating = $event"
      />
    </ul>
    <br />
  </div>
</template>
<script>

import Rating from './Rating';

export default {
  name: 'user',
  components: {
    'rating-component': Rating,
  },
  data() {
    return {
      userList: {},
      selectedUser: null,
      ratings: '',
      userRating: []
    }
  },
  props: ['users'],



}
</script>

<style scoped>
.userRate {
  border-radius: 2px, 2px;
  border: 1px solid black;
  font-size: 0.5em;
  background-color: black;
  color: aliceblue;
}
</style>>
</style>