<template>
  <div class="container column">
    <form class="card card-w30">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <app-select
          @selected-block="selected"
          :value="activeOption"
        ></app-select>
      </div>
      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="textOptions"></textarea>
      </div>
      <app-button :disabled="textOptions.length < 4" @click.prevent="addBlock"
        >Добавить</app-button
      >
    </form>

    <div class="card card-w70">
      <h3 v-if="blocks.length === 0">
        Добавьте первый блок, чтобы увидеть результат
      </h3>
      <div v-for="item in blocks" :key="item">
        <component :is="item.type" :value="item.text"></component>
      </div>
    </div>
  </div>
  <div class="container">
    <p>
      <app-button @click="donloadComents">Загрузить кооментарии</app-button>
    </p>
    <app-loader v-if="loading"></app-loader>
    <div class="card" v-if="coments.length > 0">
      <h2>Комментарии</h2>
      <app-coments :comments="coments"></app-coments>
    </div>
  </div>
</template>

<script>
import AppSelect from './components/AppSelect.vue'
import AppTitle from './components/AppTitle.vue'
import AppAvatar from './components/AppAvatar.vue'
import AppSubTitle from './components/AppSubTitle.vue'
import AppText from './components/AppText.vue'
import AppButton from './components/AppButton.vue'
import AppLoader from './components/AppLoader.vue'
import AppComents from './components/AppComents.vue'
export default {
  data () {
    return {
      blocks: [],
      coments: [],
      textOptions: '',
      activeOption: 'app-title',
      loading: false
    }
  },
  components: {
    AppSelect,
    AppTitle,
    AppAvatar,
    AppSubTitle,
    AppText,
    AppButton,
    AppLoader,
    AppComents
  },
  methods: {
    selected (data) {
      this.activeOption = data
    },
    addBlock () {
      this.blocks.push({
        type: this.activeOption,
        text: this.textOptions
      })
      this.textOptions = ''
      this.activeOption = 'app-title'
      this.createComponent()
    },
    async donloadComents () {
      try {
        this.loading = true
        const response = await fetch(
          'https://jsonplaceholder.typicode.com/comments?_limit=42'
        )
        const arrComments = await response.json()
        this.coments.push(...arrComments)
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
          'https://vue-with-http-25010-default-rtdb.asia-southeast1.firebasedatabase.app/components.json',
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
          'https://vue-with-http-25010-default-rtdb.asia-southeast1.firebasedatabase.app/components.json'
        )
        const arrComponents = await response.json()
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

<style>
.avatar {
  display: flex;
  justify-content: center;
}
.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
