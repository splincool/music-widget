<template>
  <v-layout>
    <v-flex>
      <v-toolbar
        color="blue"
        dark
        tabs
      >
        <v-toolbar-title>Популярные поздравления</v-toolbar-title>
        <v-tabs
          slot="extension"
          v-model="tab"
          color="blue"
          grow
          show-arrows
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>
          <v-tab
            v-for="item in categories"
            :key="item"
            @click="chooseNextTab"
          >
            {{ item }}
          </v-tab>
        </v-tabs>
      </v-toolbar>
      <v-tabs-items v-model="tab">
        <v-tab-item
          v-for="item in categories"
          :key="item"
        >
          <SongsList :_songs="computedSongs"/>
          <v-btn 
            :disabled="currPage === 1" 
            small 
            @click="prevPage"
          >
              Назад
          </v-btn>
          <v-btn
            :disabled="currPage === pageCount"
            small 
            @click="nextPage"
          >
            Далее
          </v-btn>
        </v-tab-item>
      </v-tabs-items>
    </v-flex>
  </v-layout> 
</template>

<script>
import SongsList from './SongsList'

export default {
  name: 'widgetHeader',
  data () {
    return {
      currPage: 1,
      songsPerPage: 8,
      windowWidth: 0,
      tab: null,
      categories: [
        'По именам', 
        'Популярные', 
        'Прикольные',
        'Мужчине',
        'Девушке',
        'О любви',
        'Разные'
      ],
      songs: [
        'Поздравляю с Днём Рождения (звонок из полиции)', 
        'С днем рожденья тебя, дорогая моя!', 
        'Сестрёнка, пусть сбываются все твои мечты!',
        'Пускай идут года - ты только молодей!',
        'От всей души тебя я поздравляю с Днём Рождения!',
        'Заводное поздравление для мужчины!',
        'Поздравление для головокружительной Женщины!',
        'Я поднимаю за тебя бокал!',
        'С Новым Годом!'
      ]
    }
  },
  mounted() {
    this.$nextTick(function() {
      window.addEventListener('resize', this.getWindowWidth);
      this.getWindowWidth()
    })

  },
  beforeDestroy() {
    window.removeEventListener('resize', this.getWindowWidth);
  },
  watch: {
    windowWidth () {
      if (this.windowWidth < 600) {
        this.songsPerPage = 4
      } else {
        this.songsPerPage = 8
      }
    }
  },
  computed: {
    pageCount () {
      var pageCount = Math.ceil(this.songs.length / this.songsPerPage)
      return pageCount
    },
    computedSongs () {
      var computedSongs = this.songs.filter((item, idx) => {
        return (idx >= (this.songsPerPage * this.currPage - this.songsPerPage)) && 
               (idx <= (this.songsPerPage * this.currPage - 1))
      })
      return computedSongs
    }
  },
  methods: {
    nextPage () {
      this.currPage += 1
    },
    prevPage () {
      if (this.currPage != 1) {
        this.currPage -= 1
      }
    },
    getWindowWidth() {
      this.windowWidth = document.documentElement.clientWidth;
    },
    chooseNextTab () {
      this.currPage = 1
    }
  },
  components: {
    SongsList
  }
}
</script>

<style>

</style>
