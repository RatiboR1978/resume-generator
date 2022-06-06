<template>
  <div class="card card-w70">
    <h3 v-if="this.blocks.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>
    <div v-for="(item, idx) in blocks" :key="idx">
      <component :is="item.type" :value="item.text"></component>
    </div>
  </div>
</template>

<script>
import AppAvatar from '@/components/AppAvatar'
import AppSubTitle from '@/components/AppSubTitle'
import AppText from '@/components/AppText'
import AppTitle from '@/components/AppTitle'
export default {
  name: 'AppComponentContainer',
  props: ['blocks'],
  data () {
    console.log(this.blocks)
    return {

    }
  },
  components: {
    AppSubTitle,
    AppText,
    AppAvatar,
    AppTitle
  },
  methods: {

  }
}
</script>

<style scoped>

</style>
