<template>
  <div>
    <ul>
      <li v-for="(email,index) in emails" :key="index" @click="detailMail = email">
        <span>{{email.subject}}</span>
      </li>
    </ul>
    <email-detail :emailDetail="detailMail"></email-detail>
  </div>
</template>

<script>

import EmailDetail from '../components/EmailDetail'
import { watch } from 'fs';

export default {
  name: 'email',
  components: { EmailDetail },
  props: ['emails'],
  data() {
    return {
      detailMail: this.emails[0]
    }
  },

}
</script>

<style>
</style>