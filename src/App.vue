<template>
  <v-app>
    <v-content>
      <v-container fluid>
        <MainPage/>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import MainPage from './components/MainPage'

export default {
  name: 'app',
  components: {
    MainPage
  }
}
</script>

<style lang="scss">
body {
  // background-color: black;
  // color: white;
}
</style>
