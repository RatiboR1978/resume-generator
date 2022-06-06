<template>
  <div class="form-control">
    <label for="value">Значение</label>
    <textarea
      id="value"
      rows="3"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    ></textarea>
  </div>
</template>

<script>
export default {
  name: 'AppTextArea',
  props: {
    modelValue: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped></style>
