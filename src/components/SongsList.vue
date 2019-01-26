<template>
  <v-layout>
    <v-flex>
      <v-card flat>
        <v-card-text>
          <v-layout row wrap justify-space-between>
            <v-flex 
              v-for="(song, idx) in _songs" 
              :key="idx"
              xs12 sm6
              >
              <v-card
                class="ma-1">
                <v-layout align-center>
                  <v-flex xs3>
                    <v-btn fab dark medium depressed color="blue">
                      <v-icon large dark>play_arrow</v-icon>
                    </v-btn>
                  </v-flex>
                  <v-flex xs9>
                    <div class="text-xs-left d-flex blue--text font-weight-bold">{{ song }}</div>
                  </v-flex>
                </v-layout>
              </v-card>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
      <v-btn disabled small>Назад</v-btn>
      <v-btn small>Далее</v-btn>
    </v-flex>
  </v-layout>  
</template>

<script>
export default {
  name: 'songsList',
  props: {
    _songs: Array
  },
}
</script>

<style>

</style>
