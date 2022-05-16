<template>
  <h1>Резюме {{ value }}</h1>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  }
}
</script>

<style></style>
