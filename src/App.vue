<template>
  <div class="container column">
    <app-form @add-block="addBlockData"></app-form>
    <app-component-container :blocks="this.blocks"></app-component-container>
  </div>
  <div class="container">
    <p>
      <app-button>Загрузить комментарии</app-button>
    </p>
    <app-comments></app-comments>
    <app-loader></app-loader>
  </div>
</template>

<script>
import AppForm from '@/components/AppForm'
import AppButton from '@/components/AppButton'
import AppComments from '@/components/AppComments'
import AppLoader from '@/components/AppLoader'
import AppComponentContainer from '@/components/AppComponentContainer'

export default {
  data () {
    return {
      nameActiveBlock: '',
      dataActiveBlock: '',
      blocks: []
    }
  },
  components: {
    AppForm,
    AppButton,
    AppComments,
    AppLoader,
    AppComponentContainer
  },
  methods: {
    addBlockData (name, text) {
      this.nameActiveBlock = name
      this.dataActiveBlock = text
      this.blocks.push({
        type: this.nameActiveBlock,
        text: this.dataActiveBlock
      })
      console.log(this.blocks)
    }
  }
}
</script>

<style scoped>

</style>
