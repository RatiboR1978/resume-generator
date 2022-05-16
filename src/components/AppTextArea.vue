<template>
  <textarea id="value" rows="3" @input="addText"></textarea>
</template>

<script>
export default {
  emits: {
    'add-text' (str) {
      if (str) return true
      console.warn('No data')
      return false
    }
  },
  methods: {
    addText (event) {
      this.$emit('add-text', event.target.value)
    }
  }
}
</script>

<style></style>
