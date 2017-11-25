<template>
  <v-layout column class="ma-1">
    <v-layout row>
      <v-flex xs3>
        <img :src="getImgUrl(major.icon)" alt="">
      </v-flex>
      <v-flex>
        
      </v-flex>
    </v-layout>

    <v-layout row wrap>
      <!-- Card flex -->
      <v-flex xs3 v-for="person in list" :key="person.interviewRef">
        <person-card :person="person" :interviewCutoff="major.interviewCutoff"></person-card>
      </v-flex><!-- End of Card flex -->
    </v-layout>
  </v-layout>
</template>

<script>
import PersonCard from './PersonCard'

export default {
  name: 'MajorContent',
  props: ['list','major'],
  components: {
    PersonCard
  },
  data () {
    return {
      url: 'content.png'
    }
  },
  methods: {
    getImgUrl(pet) {
      var images = require.context('../assets/', false, /\.png$/)
      return images('./' + pet)
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
