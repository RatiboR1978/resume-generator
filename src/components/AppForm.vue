<template>
  <form class="card card-w30">
    <app-select @selected-block="selected" :value="activeOption"></app-select>
    <app-text-area @input-text="inputTextAria"></app-text-area>
    <app-button :disabled="textAria.length < 4"  @click.prevent="addBlock">Добавить</app-button>
  </form>
</template>

<script>
import AppSelect from '@/components/AppSelect'
import AppButton from '@/components/AppButton'
import AppTextArea from '@/components/AppTextArea'

export default {
  name: 'AppForm',
  data () {
    return {
      activeOption: 'app-title',
      textAria: ''
    }
  },
  components: {
    AppSelect,
    AppButton,
    AppTextArea
  },
  methods: {
    selected (data) {
      this.activeOption = data
    },
    inputTextAria (data) {
      this.textAria = data
    },
    addBlock () {
      this.$emit('add-block', this.activeOption, this.textAria)
    }
  }
}
</script>

<style scoped>

</style>
