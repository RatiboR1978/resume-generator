<template>
  <p>{{this.value}}</p>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  },
  name: 'AppText'
}
</script>

<style scoped>

</style>
