<template>
  <a :id="id" class="base-ancher"></a>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      default: undefined,
    },
  },
  mounted() {
    // DOM生成完了後に実行される
    this.$nextTick(() => {
      this.scrollTo()
    })
  },
  methods: {
    /**
     * 該当箇所へスクロールする処理
     * @returns { void } - idとhashが等しければ該当箇所へスクロールする
     */
    scrollTo() {
      const hash = this.$route.hash
      const hasnName = hash ? hash.slice(1) : undefined
      if (hash && this.id === hasnName) {
        this.$scrollTo(hash)
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.base-ancher {
  position: relative;
  top: -72px; // topでoffsetを調整
  height: 0;
  overflow: hidden;
}
</style>
