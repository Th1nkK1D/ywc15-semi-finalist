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
            <v-flex>สัมภาษณ์รอบเช้า</v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
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
