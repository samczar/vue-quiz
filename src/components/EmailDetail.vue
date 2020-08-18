<template>
  <div>
    Details:
    {{emailDetail.subject}}
    <br />
    {{emailDetail.message}}
  </div>
</template>

<script>
export default {
  name: 'email-detail',
  props: ['emailDetail']

}
</script>

<style>
</style>