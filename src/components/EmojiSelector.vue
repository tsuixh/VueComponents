<template>
  <div class="container">
    <el-popover
      placement="bottom"
      trigger="click"
      :width="width"
      >
      <div class="emoji-area">
        <div v-for="(url, code, index) of emojis" :key="index" class="single-emoji" @click="selected(code)">
          <img :src="url" :alt="code" class="single-emoji"/>
        </div>
      </div>
      <span class="emoji-btn" slot="reference"><img src="../assets/smile.png" alt="emoji" class="emoji-btn"/></span>
    </el-popover>
  </div>
</template>

<script>
import Emojis from 'qq-wechat-emotion-parser/src/emotions'
export default {
  name: 'EmojiSelector',
  props: {
    col: {
      type: Number,
      default: 15
    }
  },
  data () {
    return {
      emojis: {}
    }
  },
  methods: {
    selected (code) {
      console.log(code)
      this.$emit('selected', code)
    }
  },
  computed: {
    width () {
      return this.col * 24
    }
  },
  mounted () {
    this.emojis = Emojis
    console.log(this.emojis)
  }
}
</script>

<style scoped>
  .emoji-btn {
    width: 24px;
    height: 24px;
  }
  .single-emoji {
    width: 24px;
    height: 24px;
    display: inline-block;
  }
  .single-emoji:hover {
    cursor: pointer;
    transform: scale(1.2);
  }
</style>
