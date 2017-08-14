<template>
    <div class="layout-view">
      <div class="layout-padding">
<!--         <p class="caption">
          <span class="desktop-only">Fill Form</span>
          <span class="mobile-only">Fill Form</span>
        </p> -->
        <div class="build-wrap-editlayout" style="display:none;"></div>
        <form name="data-storage" v-if="formNotFilled">
            <div class="render-form-editlayout"></div>
        </form>
        <div v-else>
          <h3>Thanks For filling the form </h3>
        </div>
        <button class="primary" @click="saveData()" >Save</button>
      </div>   
    </div>
</template>
<style type="text/css">
  h1{
      font-size: -webkit-xxx-large !important;
  }
</style>
<script>
/* global appconfig ,axios,Formeo */

function renderDataLayout (result) {
  var dataLayout = JSON.stringify(result.data)
  let renderContainer = document.querySelector('.render-form-editlayout')

  sessionStorage.removeItem('formData')
  sessionStorage.setItem('formData', dataLayout)

  let container = document.querySelector('.build-wrap-editlayout')

  var fbOptions = {
    container,
    allowEdit: true,
    controls: {
      groupOrder: [
        'common',
        'layout'
      ]
    },
    svgSprite: 'https://draggable.github.io/formeo/assets/img/formeo-sprite.svg',
    sessionStorage: true,
    editPanelOrder: ['attrs', 'options']
  }

  var formeo1 = new Formeo(fbOptions)

  setTimeout(function () {
    formeo1.render(renderContainer)
  }, 1000)
}

export default {
  mounted () {
    this.getLayouts()
  },
  data: function () {
    return {
      formNotFilled: true
    }
  },
  methods: {
    openLeftNav () {
      this.$emit('show_nav')
    },
    getLayouts () {
      const url = appconfig.dev.BASE_URL + '/api/mobile/get_data_layout?api_token=' + appconfig.dev.APP_TOKEN + '&dl_id=' + this.$route.params.id
      axios.get(url).then(response => {
        renderDataLayout(response.data)
        console.log(response)
      })
    },
    saveData () {
      const url = appconfig.dev.BASE_URL + '/api/mobile/save_data_storage?api_token=' + appconfig.dev.APP_TOKEN
      var form = document.querySelector('form')
      var dataToSend = JSON.stringify(new FormData(form))
      alert('Your data is being saved')
      axios.post(url, {data: dataToSend, dl_id: this.$route.params.id}).then(response => {
        // console(response.data)
        console.log(response)
        alert(response.data.data)
        this.formNotFilled = false
      })
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
