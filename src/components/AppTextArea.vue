<template>
  <div class="form-control">
    <label for="value">Значение</label>
    <textarea id="value" rows="3" @input="inputTextarea()" v-model="this.textOptions"></textarea>
  </div>
</template>

<script>
export default {
  name: 'AppTextArea',
  props: {
    value: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      textOptions: this.value
    }
  },
  methods: {
    inputTextarea () {
      this.$emit('input-text', this.textOptions)
    }
  }
}
</script>

<style scoped>

</style>
