<template>
  <div id="app">
    <span class="text">ABCDE</span>
    <router-view/>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
// 获取html根元素并设置fontsize属性
export default {
  computed: {
    // ...是ES6中的扩展运算符
    ...mapGetters(['test'])
  },
  mounted () {
    this.$store.dispatch('setTest', 1).then(() => {
      // console.log(this.$store.state.book.test)
      console.log(this.test)
    })
  }
}
document.addEventListener('DOMContentLoaded', () => {
  const html = document.querySelector('html')
  let fontSize = window.innerWidth / 10
  // 为fontSize设置最大值
  fontSize = fontSize > 50 ? 50 : fontSize
  html.style.fontSize = fontSize + 'px'
})
</script>

<style lang="scss" scoped>
@import "./assets/styles/global.scss";
.text{
  font-family:'Days One';
  font-size: px2rem(20);
  color:orange
}
</style>
