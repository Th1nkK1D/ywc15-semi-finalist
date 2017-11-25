<template>
  <v-card class="ma-1">
    <v-card-text>
      <v-layout row>
        <div :class="major.color+'--text'">
          <strong class="intref">
            {{person.interviewRef.slice(0,2)}}
            <br>
            {{person.interviewRef.slice(2,4)}}
          </strong>
        </div>
        <v-flex>
          <v-layout column>
            <v-flex><strong>{{person.firstName}} {{person.lastName}}</strong></v-flex>
            <v-flex><v-icon>access_time</v-icon> {{interviewSection}}</v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'PersonCard',
  props: ['person','major'],

  data() {
    return {

    }
  },

  computed: {
    interviewSection() {
      return parseInt(this.person.interviewRef.slice(2,4)) <= this.major.interviewCutoff ? '9:00' : '13:00'
    }
  }
}
</script>

<style lang="scss" scoped>
  .icon {
    font-size: 15px;
    line-height: 20px;
  }
  .intref {
    font-size: 22px;
    line-height: 0;
    opacity: 0.5;
  }
</style>
