<template>
  <v-container 
    class="widget-wrapper">
    <v-layout
      text-xs-center
      wrap
    >
      <v-flex xs12>
        <CategoryTabs/>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import CategoryTabs from './CategoryTabs'

export default {
  components: {
    CategoryTabs
  }
}
</script>

<style lang="stylus">
.widget-wrapper
  max-width: 720px
  max-height: 540px 
</style>

