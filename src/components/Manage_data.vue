<template>
    <div class="layout-padding">
      <p class="caption">
        <span class="desktop-only">Your Layouts</span>
        <span class="mobile-only">Your Layouts</span>
      </p>

      <div class="card " v-for="card in cardList">
        <div class="card-title">
          {{card.layoutname}}
        </div>
         <div class="card-media">
          <button class="primary circular small" @click="openFormView(card.id)">
            <i>edit</i>
          </button>
        </div>
        <div class="card-content">
          <div class="item-content">
            <div class="item-label">
              <p class="item-title">{{card.entityname}}</p>
            </div>
          </div>
        </div>
        <div class="card-actions card-no-top-padding">
          <div class="text-grey">
            {{card.date}}
          </div>
          <div>
            ({{card.totlformsfilled}} filled)
          </div>
          <div class="auto"></div> 
          <button class="warning clear small" ><i class="on-left">eye</i>view</button>
        </div>        
      </div>
    </div>
</template>

<script>
import Router from 'router'

/* global appconfig ,axios */
class Card {
  constructor (layoutname, entityname, date, totlformsfilled, fillformurl) {
    this.layoutname = layoutname
    this.entityname = entityname
    this.date = date
    this.totlformsfilled = totlformsfilled
    this.fillformurl = fillformurl
    this.id = ''
  }
}

function mapCards (data) {
  var List = []
  data.forEach(el => {
    console.log(el)
    var glblcard = new Card()
    glblcard.layoutname = el.name
    glblcard.entityname = el.layout_entity.name
    glblcard.date = el.updated_at
    glblcard.totlformsfilled = el.filled_forms.length
    glblcard.fillformurl = ''
    glblcard.id = el.id
    List.push(glblcard)
  })

  return List
}

export default {
  mounted () {
    this.getLayouts()
  },
  data () {
    return {
      cardList: []
    }
  },
  methods: {
    getLayouts () {
      const url = appconfig.dev.BASE_URL + '/api/mobile/get_layouts?api_token=' + appconfig.dev.APP_TOKEN
      axios.get(url).then(response => {
        this.cardList = mapCards(response.data.data)
      })
    },

    openFormView (id) {
      Router.replace({ path: 'fillform/' + id })
    }
  }
}

</script>
