<template>
  <div class="container">
    <EmojiSelector></EmojiSelector>
  </div>
</template>

<script>
import EmojiSelector from './EmojiSelector'
export default {
  name: 'HelloWorld',
  components: {EmojiSelector},
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style scoped>
</style>
