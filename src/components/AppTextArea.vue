<template>
  <div class="form-control">
    <label for="value">Значение</label>
    <textarea id="value" rows="3" v-model="textOptions" @input="inputTextarea($event)"></textarea>
  </div>
</template>

<script>
export default {
  name: 'AppTextArea',
  data () {
    return {
      textOptions: ''
    }
  },
  methods: {
    inputTextarea (event) {
      this.$emit('input-text', event.target.value)
    }
  }
}
</script>

<style scoped>

</style>
