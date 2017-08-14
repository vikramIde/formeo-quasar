<template>
    <div class="layout-view">
      <div class="logo-container non-selectable no-pointer-events">
        <div class="logo">
          <img src="~assets/quasar-logo.png">
          
        </div>
      </div>
    </div>
</template>

<script>
export default {
  mounted () {
    console.log('I am index.vue')
    console.log(this.$refs)
  },
  methods: {
    openLeftNav () {
      this.$emit('show_nav')
    }
  }
}
</script>

<style lang="stylus">
.logo-container
  width 192px
  height 268px
  perspective 800px
  position absolute
  top 50%
  left 50%
  transform translateX(-50%) translateY(-50%)
.logo
  position absolute
  transform-style preserve-3d
</style>
