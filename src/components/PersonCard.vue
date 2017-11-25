<template>
  <v-card class="ma-1">
    <v-card-text>
      <v-layout row>
        <v-flex xs3>
          <v-layout column>
            <v-flex>
              <strong>{{person.interviewRef}}</strong>
            </v-flex>
          </v-layout>
        </v-flex>
        <v-flex>
          <v-layout column>
            <v-flex><strong>{{person.firstName}} {{person.lastName}}</strong></v-flex>
            <v-flex>{{interviewSection}}</v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'PersonCard',
  props: ['person','interviewCutoff'],

  data() {
    return {

    }
  },

  computed: {
    interviewSection() {
      return parseInt(this.person.interviewRef.slice(2,4)) <= this.interviewCutoff ? 'เช้า 9:00' : 'บ่าย 13:00'
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
