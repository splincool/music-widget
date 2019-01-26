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
          <SongsList :_songs="songs"/>
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
        'Я поднимаю за тебя бокал!'
      ]
    }
  },
  components: {
    SongsList
  }
}
</script>

<style>

</style>
