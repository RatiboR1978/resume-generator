<template>
  <div class="form-control">
    <label for="type">Тип блока</label>
    <select
      id="type"
      @change="$emit('update:modelValue', $event.target.value)"
      :value="modelValue"
    >
      <option :value="item.value" v-for="(item, idx) in arrOptions" :key="idx">{{ item.text }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'AppSelect',
  props: {
    modelValue: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      arrOptions: [
        {
          value: 'app-title',
          text: 'Заголовок'
        },
        {
          value: 'app-sub-title',
          text: 'Подзаголовок'
        },
        {
          value: 'app-avatar',
          text: 'Аватар'
        },
        {
          value: 'app-text',
          text: 'Текст'
        }
      ]
    }
  }
}
</script>

<style scoped>

</style>
