<template>
  <v-app>
    <v-content>
      <v-container fluid>
        <main-page/>
      </v-container>
    </v-content>
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

<style lang="scss">
#app {
  background-color: #2c3e50;
  color: white;
}
</style>
