<template>
  <select id="type" @change="selected($event)" :value="activeOption">
    <option :value="item.value" v-for="(item, idx) in valueSelect" :key="idx">
      {{ item.text }}
    </option>
  </select>
</template>

<script>
export default {
  data () {
    return {
      props: {
        value: {
          type: String,
          required: true
        }
      },
      activeOption: this.value,
      valueSelect: [
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

<style></style>
