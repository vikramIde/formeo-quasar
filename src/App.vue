<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
	
    <router-view ></router-view>
    <!-- <leftnav ref="leftNav"></leftnav> -->
  </div>
</template>

<script>
// import leftnav from './components/left_navigation'
export default {
  data () {
    return {
      search: ''
    }
  },
  components: {
    // leftnav
  },
  mounted () {
    console.log('I am App.vue')
    console.log(this.$parent.$refs)
  }
}
</script>
<style>
	
</style>
