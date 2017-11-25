<template>
  <div class="mainpage">
    <!-- <img src="../assets/logo.png" alt="">
    <v-text-field solo v-model="searchKeyword" label="Search" append-icon="keyboard_voice" prepend-icon="search"></v-text-field>
    {{searchKeyword}}
    <br>
    {{categorialList}} -->

    <v-layout column>
      <v-flex class="header">
        <img src="../assets/logo.png" alt="">

        <v-layout row>
          <v-flex></v-flex>
          <v-flex xs6>
            <v-text-field solo v-model="searchKeyword" label="Search" append-icon="keyboard_voice" prepend-icon="search"></v-text-field>
          </v-flex>
          <v-flex></v-flex>
        </v-layout>
        
      </v-flex>
      <v-flex class="content">
        
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
export default {
  name: 'MainPage',

  data() {
    return {
      response: [],
      searchKeyword: ''
    }
  },

  computed: {
    categorialList() {
      return {
        content: this.response.filter(item => item.major === 'content' && (item.firstName.indexOf(this.searchKeyword) >= 0 || item.lastName.indexOf(this.searchKeyword) >= 0)),
        marketing: this.response.filter(item => item.major === 'marketing' && (item.firstName.indexOf(this.searchKeyword) >= 0 || item.lastName.indexOf(this.searchKeyword) >= 0)),
        design: this.response.filter(item => item.major === 'design' && (item.firstName.indexOf(this.searchKeyword) >= 0 || item.lastName.indexOf(this.searchKeyword) >= 0)),
        programming: this.response.filter(item => item.major === 'programming' && (item.firstName.indexOf(this.searchKeyword) >= 0 || item.lastName.indexOf(this.searchKeyword) >= 0)),
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
  img {
    width: 100%;
    height: auto;
    max-width: 300px;
    margin: 10px;
  }
}
</style>