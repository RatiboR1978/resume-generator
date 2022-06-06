<template>
  <div class="form-control">
    <label for="type">Тип блока</label>
    <select id="type" @change="selected($event)" :value="this.value">
      <option :value="item.value" v-for="(item, idx) in arrOptions" :key="idx">{{ item.text }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'AppSelect',
  props: {
    value: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      activeOption: this.value,
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
  },
  methods: {
    selected (event) {
      this.$emit('selected-block', event.target.value)
    }
  }
}
</script>

<style scoped>

</style>
