<template>
  <v-app class="blue-grey darken-3 white--text">
    <v-content>
      <v-container fluid>
        <main-page/>
      </v-container>
    </v-content>
    <v-footer class="pa-3 blue-grey darken-3">
      <v-flex class="text-xs-center">
        © Th1nk.K1D 2017 - <a class="white--text" href="https://github.com/Th1nkK1D/ywc15-semi-finalist">Github Repository</a>
      </v-flex>
    </v-footer>
  </v-app>
</template>

<script>
import MainPage from './components/MainPage'

export default {
  name: 'app',
  components: {
    MainPage,
  }
}
</script>

<style lang="scss" scoped>

</style>
