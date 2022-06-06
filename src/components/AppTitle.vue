<template>
  <h1>{{this.value}}</h1>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  },
  name: 'AppTitle'
}
</script>

<style scoped>

</style>
