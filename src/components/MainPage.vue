<template>
  <div class="mainpage">
    <!-- <img src="../assets/logo.png" alt=""> -->
    <v-text-field solo v-model="searchKeyword" label="Search" append-icon="keyboard_voice" prepend-icon="search"></v-text-field>
    {{searchKeyword}}
    <br>
    {{categorialList}}
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

<style lang="sass" scoped>

</style>
