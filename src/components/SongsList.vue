<template>
  <v-layout>
    <v-flex>
      <Song :_songs="_songs"/>
    </v-flex>
  </v-layout> 
</template>

<script>
import Song from './Song'
export default {
  name: 'songsList',
  props: {
    _songs: Array
  },
  components: {
    Song
  }
}
</script>

<style>

</style>
