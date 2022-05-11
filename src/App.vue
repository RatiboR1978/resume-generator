<template>
  <div class="container column">
    <form class="card card-w30">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <app-select @selected-block="selected"></app-select>
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
      <div v-for="component in blocks" :key="component">
        <component :is="component" :value="textComponent"></component>
      </div>
    </div>
  </div>
  <div class="container">
    <p>
      <app-button>Загрузить кооментарии</app-button>
    </p>
    <div class="card" v-if="coments.length > 0">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item">
          <div>
            <p><strong>test@microsoft.com</strong></p>
            <small
              >Lorem ipsum dolor sit amet, consectetur adipisicing elit.
              Eligendi, reiciendis.</small
            >
          </div>
        </li>
      </ul>
    </div>
    <div class="loader"></div>
  </div>
</template>

<script>
import AppSelect from './components/AppSelect.vue'
import AppTitle from './components/AppTitle.vue'
import AppAvatar from './components/AppAvatar.vue'
import AppSubTitle from './components/AppSubTitle.vue'
import AppText from './components/AppText.vue'
import AppButton from './components/AppButton.vue'
export default {
  data () {
    return {
      blocks: [],
      coments: [],
      textOptions: '',
      activeOption: 'app-title',
      textComponent: ''
    }
  },
  components: {
    AppSelect,
    AppTitle,
    AppAvatar,
    AppSubTitle,
    AppText,
    AppButton
  },
  methods: {
    selected (data) {
      this.activeOption = data
    },
    addBlock () {
      this.textComponent = this.textOptions
      this.blocks.push(this.activeOption)
    }
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
