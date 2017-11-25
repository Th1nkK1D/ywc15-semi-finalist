<template>
  <v-layout column class="ma-1">
    <v-layout row>
      <v-flex xs3>icon</v-flex>
      <v-flex>description</v-flex>
    </v-layout>

    <v-layout row wrap>
      <!-- Card flex -->
      <v-flex xs3 v-for="item in list" :key="item.interviewRef">
        <v-card class="ma-1">
          <v-card-text>
            {{item}}
          </v-card-text>
        </v-card>
      </v-flex><!-- End of Card flex -->
    </v-layout>
  </v-layout>
</template>

<script>
export default {
  name: 'MajorContent',
  props: ['list'],
  data () {
    return {
      
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
