<template>
  <div class="mainpage">
    <!-- <img src="../assets/logo.png" alt="">
    <v-text-field solo v-model="searchKeyword" label="Search" append-icon="keyboard_voice" prepend-icon="search"></v-text-field>
    {{searchKeyword}}
    <br>
    {{categorialList}} -->

    <v-layout column>
      <!-- Header -->
      <v-flex class="header">
        <img src="../assets/logo.png" alt="">

        <v-layout row>
          <v-flex></v-flex>
          <v-flex xs6>
            <v-text-field solo v-model="searchKeyword" label="Search" append-icon="keyboard_voice" prepend-icon="search"></v-text-field>
          </v-flex>
          <v-flex></v-flex>
        </v-layout>
        
      </v-flex><!-- End of Header -->
      <!-- Content -->
      <v-layout row class="content">
        <v-flex></v-flex>
        <v-flex xs10>
          <v-card>
            <!-- Majors Tab -->
            <v-tabs>
              <!-- Tab bar -->
              <v-tabs-bar class="grey lighten-4" dark>
                <v-tabs-item v-for="major in majors" :key="major.name" :href="'#' + major.name" class="black--text" ripple>
                  {{ major.alias }}
                </v-tabs-item>
                <v-tabs-slider color="cyan"></v-tabs-slider>
              </v-tabs-bar><!-- End of Tab bar -->

              <v-tabs-items class="grey lighten-4" >
                <v-tabs-content v-for="major in majors" :key="major.name" :id="major.name">
                  <major-content :list="categorialList[major.name]" :major="major"></major-content>
                </v-tabs-content>
              </v-tabs-items>
            </v-tabs><!-- End of Majors Tab -->
          </v-card>
        </v-flex>
        <v-flex></v-flex>
      </v-layout><!-- End of Content -->
    </v-layout>
  </div>
</template>

<script>
import MajorContent from './MajorContent'

export default {
  name: 'MainPage',
  components: {
    MajorContent
  },

  data() {
    return {
      majors: [
        {name: 'content', alias: 'Content', interviewCutoff: 25},
        {name: 'marketing', alias: 'Marketing', interviewCutoff: 20},
        {name: 'design', alias: 'Design', interviewCutoff: 18},
        {name: 'programming', alias: 'Programming', interviewCutoff: 23},
        ],
      response: [],
      searchKeyword: ''
    }
  },

  computed: {
    categorialList() {
      return {
        content: this.response.filter(p => p.major === 'content' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
        marketing: this.response.filter(p => p.major === 'marketing' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
        design: this.response.filter(p => p.major === 'design' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
        programming: this.response.filter(p => p.major === 'programming' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
      }
    },
  },

  mounted() {
    this.axios.get('https://ywc15.ywc.in.th/api/interview')
    .then(response => {this.response = response.data})
  }
}
</script>

<style lang="scss">
.header {
  text-align: center;
  margin: 40px 0;


  img {
    width: 100%;
    height: auto;
    max-width: 300px;
    margin: 10px;
  }
}
</style>