<template>
<div class="vc-page">
  <header-bar>
    <icon-button slot="left" @click="back()" icon="arrow_back"></icon-button>
    <span>Toast</span>
  </header-bar>
  <content>
    <button-area>
      <button fill raised color="red" text="显示 toast" @click="show('default')"></button>
      <button fill raised color="red" text="在中间的 toast" @click="show('center')"></button>
      <button fill raised color="red" text="带icon的 toast" @click="show('ok')"></button>
    </button-area>
  </content>
  <toast v-for="toast in toasts" :text="toast.text" :loading="toast.loading" :icon="toast.icon" :center="toast.center"></toast>
</div>
</template>

<script>
export default {
  data () {
    return {
      toasts: []
    }
  },
  methods: {
    back () {
      window.history.back()
    },
    show (type) {
      switch (type) {
        case 'center':
          this.toasts.push({
            text: '在中间',
            center: true
          })
          break
        case 'loading':
          this.toasts.push({
            text: '加载中...',
            loading: true
          })
          break
        case 'ok':
          this.toasts.push({
            text: '操作成功',
            icon: 'check',
            center: true
          })
          break
        default:
          this.toasts.push({
            text: '默认toast'
          })
          break
      }
      setTimeout(() => this.toasts.splice(0, 1), 2000)
    }
  }
}
</script>

<style lang="css">
</style>
