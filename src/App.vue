<template>
  <div class="container column">
    <app-form @add-block="addBlockData"></app-form>
    <app-component-container :blocks="this.blocks"></app-component-container>
  </div>
  <div class="container">
    <p>
      <app-button @click="donloadComents">Загрузить комментарии</app-button>
    </p>
    <app-comments :comments="this.comments"></app-comments>
    <app-loader v-if="loading"></app-loader>
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
      blocks: [],
      comments: [],
      loading: false
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
      this.createComponent()
    },
    async donloadComents () {
      try {
        this.loading = true
        const response = await fetch(
          'https://jsonplaceholder.typicode.com/comments?_limit=42'
        )
        const arrComments = await response.json()
        this.comments.push(...arrComments)
        this.loading = false
      } catch (error) {
        console.log(error)
        this.loading = false
      }
    },
    async createComponent () {
      try {
        this.loading = true
        const response = await fetch(
          'https://vue-resume-generator-2-default-rtdb.firebaseio.com/components.json',
          {
            method: 'PATCH',
            headers: {
              'Content-Type': 'application/json'
            },
            body: JSON.stringify({
              components: this.blocks
            })
          }
        )
        console.log(response)
        this.loading = false
      } catch (error) {
        console.log(error)
        this.loading = false
      }
    },
    async donloadComponent () {
      try {
        this.loading = true
        const response = await fetch(
          'https://vue-resume-generator-2-default-rtdb.firebaseio.com/components.json'
        )
        const arrComponents = await response.json()
        console.log(arrComponents)
        this.blocks.push(...arrComponents.components)
        this.loading = false
      } catch (error) {
        console.log(error)
        this.loading = false
      }
    }
  },
  mounted () {
    this.donloadComponent()
  }
}
</script>

<style scoped>

</style>
