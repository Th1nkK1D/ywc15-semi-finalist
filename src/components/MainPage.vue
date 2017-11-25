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
              <v-tabs-bar class="grey lighten-4">
                <v-tabs-item v-for="major in majors" :key="major.name" :href="'#' + major.name" ripple>
                  {{ major.alias }}
                </v-tabs-item>
                <v-tabs-slider color="blue-grey"></v-tabs-slider>
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
        {name: 'content', alias: 'Web Content', icon: 'content.png', color:'blue', interviewCutoff: 25, hw: 'ให้น้อง ๆ เลือกทำคอนเทนต์ใด คอนเทนต์หนึ่งจาก 2 หัวข้อด้านล่าง โดยต้องทำเป็นคอนเทนต์ออกมาจริงเท่านั้น ไม่จำกัดรูปแบบการนำเสนอหัวข้อที่ให้เลือก \n1. คอนเทนต์ที่ทำให้ผู้ใช้ Social เข้าใจ Cyberbullying และตระหนักถึงปัญหาที่เกิดขึ้นจาก Cyberbullying \n2. คอนเทนต์ที่ทำให้คนไทยเปลี่ยนพฤติกรรมเสพติดหน้าจอ เสพติด Social หันมาพูดคุยกัน เจอหน้ากันในชีวิตจริง ๆ มากกว่าที่เป็นอยู่'},
        {name: 'design', alias: 'Web Design', icon: 'design.png', color:'amber', interviewCutoff: 18, hw: 'ให้ทำแผนการตลาด (Marketing Plan) สำหรับเว็บไซต์หนึ่งเว็บไซต์ โดยเลือกเว็บไซต์ใด ๆ ก็ได้ ทั้งเว็บไซต์ของไทยและเว็บไซต์ของต่างประเทศ \nนำเสนอในรูปแบบพรีเซนเทชั่น ไม่เกิน 10 หน้า ภายในเวลา 5 นาที'},
        {name: 'marketing', alias: 'Web Marketing', icon: 'marketing.png', color:'red', interviewCutoff: 20, hw: 'ให้ผู้ผ่านเข้ารอบสัมภาษณ์ออกแบบเว็บไซต์ของ "คณะรักษาความสงบแห่งชาติ หรือ คสช." เพื่อเป็นสื่อกลางในการประชาสัมพันธ์นโยบายต่าง ๆ และเป็นสื่อกลางระหว่างประชาชนกับคณะรักษาความสงบแห่งชาติ โดยให้ออกแบบในลักษณะของ One Page Design Website \n** สำหรับผู้ผ่านเข้ารอบสัมภาษณ์คนใดทำ CSS มา คณะกรรมการจะพิจารณาเป็นพิเศษ'},
        {name: 'programming', alias: 'Web Programming', icon: 'programming.png', color:'teal', interviewCutoff: 23, hw: 'ให้เขียน เว็บไซต์ประกาศผลผู้ผ่านเข้ารอบสัมภาษณ์ของ YWC#15 โดยใช้ข้อมูลจาก API โดยมี Feature ดังนี้ \n• ดึงข้อมูลจาก API โดยตรง \n• ให้แสดงผลแยกแต่ละสาขา \n• มีระบบค้นหาชื่อผ่านกล่อง Search \n• ความสามารถหรือ Feature พิเศษอื่น ๆ ที่มีความแตกต่าง และแสดงความสามารถของน้องออกมาให้ได้มากที่สุด \nเมื่อทำเสร็จแล้วให้ Push Source Code ขึ้น GitHub ก่อนเวลาสัมภาษณ์'},
        ],
      response: [],
      searchKeyword: ''
    }
  },

  computed: {
    categorialList() {
      return {
        content: this.response.filter(p => p.major === 'content' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
        design: this.response.filter(p => p.major === 'design' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
        marketing: this.response.filter(p => p.major === 'marketing' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
        programming: this.response.filter(p => p.major === 'programming' && (p.firstName.indexOf(this.searchKeyword) >= 0 || p.lastName.indexOf(this.searchKeyword) >= 0)),
      }
    },
  },

  mounted() {
    this.axios.get('https://ywc15.ywc.in.th/api/interview')
    .then(response => this.response = response.data.sort((a,b) => a.interviewRef.slice(2,4) - b.interviewRef.slice(2,4)))
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