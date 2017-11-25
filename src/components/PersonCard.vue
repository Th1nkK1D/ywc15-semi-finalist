<template>
  <v-card class="ma-1">
    <v-card-text>
      {{person}}
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'PersonCard',
  props: ['person'],
  data () {
    return {
      
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
