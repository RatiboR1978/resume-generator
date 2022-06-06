<template>
  <h2>{{this.value}}</h2>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  },
  name: 'AppSubTitle'
}
</script>

<style scoped>

</style>
