<template>
  <v-layout column class="ma-1">
    <v-layout row>
      <v-flex xs3>icon</v-flex>
      <v-flex>description</v-flex>
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
      
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
