<template>
  <v-layout column class="ma-1">
    <v-layout row wrap>
      <v-flex lg2 md3 sm4 xs12 class="text-xs-center">
        <img style="width:90%; height:auto;" :src="getImgUrl(major.icon)" alt="">
      </v-flex>
      <!-- Description -->
      <v-flex lg9 md8 sm7 xs12 class="description ma-2">
        <v-flex class="text-sm-left text-xs-center"><h1 :class="major.color+'--text'">{{major.alias}}</h1>  </v-flex>

        <v-expansion-panel class="elevation-0">
          <!-- HW panel -->
          <v-expansion-panel-content :value="true" class="grey lighten-4"> 
            <div slot="header"><h3><v-icon>inbox</v-icon> การบ้าน</h3></div>
            <v-card>
              <v-card-text class="grey lighten-3">
                <p class="hw">{{major.hw}}</p>
              </v-card-text>
            </v-card>
          </v-expansion-panel-content><!-- End of HW panel -->
          <!-- Interview Panel-->
          <v-expansion-panel-content class="grey lighten-4">
            <div slot="header"><h3><v-icon>mic</v-icon> รายละเอียดการสัมภาษณ์</h3></div>
            <v-card>
              <v-card-text class="grey lighten-3">
                <p>
                  การสัมภาษณ์จะจัดขึ้นในวันที่ 26 พฤศจิกายน 2560 ณ อาคาร ซี.พี.ทาวเวอร์ 1 (สีลม) 
                  ซึ่งจะแบ่งออกเป็น 2 รอบ คือ รอบช่วงเช้าตั้งแต่เวลา 9.00 น. ถึง 12.00 น. และ รอบช่วงบ่ายตั้งแต่เวลา 13.00 น. ถึง 18.00 น.
                </p>

                <p>
                  <strong>สิ่งที่ต้องเตรียมมาในวันสัมภาษณ์</strong>
                  <ol class="ml-4">
                    <li>บัตรประชาชนสำหรับการแลกบัตรเข้าอาคาร ซี.พี.ทาวเวอร์ 1 (สีลม) และ บัตรนักศึกษาสำหรับการลงทะเบียนสัมภาษณ์ กรุณาแต่งกายด้วยชุดนักศึกษา</li>
                    <li>การบ้านและสิ่งที่กรรมการสาขากำหนดไว้ กรุณาอ่านรายละเอียดการบ้านและสิ่งที่กรรมการให้เตรียมมาให้ครบถ้วน หากสาขาใดต้องใช้โน้ตบุ๊ค ควรชาร์ตแบตเตอรี่และเตรียมอินเทอร์เน็ตส่วนตัวมาให้พร้อม เนื่องจากสถานที่ไม่มีบริการอินเทอร์เน็ตให้ใช้</li>
                    <li>Portfolio สามารถนำมาประกอบการสัมภาษณ์ได้ สำหรับน้อง ๆ สาขาดีไซน์จะต้องนำ Portfolio มาด้วยทุกคน</li>
                  </ol>
                </p>

                <p>
                  <strong>การเดินทางมาสัมภาษณ์</strong>
                  <ol class="ml-4">
                    <li>ด้วยรถไฟฟ้า BTS สามารถลงสถานีศาลาแดง ณ ทางออกที่ 2</li>
                    <li>ด้วยรถไฟฟ้า MRT สามารถลงสถานีสีลม ณ ทางออกที่ 2 โดยเดินเรียบทางเท้าไปตามถนนสีลม</li>
                    <li>ด้วยรถประจำทาง สามารถขึ้นใช้บริการสาย 15, 77, 155, 504, 177, 76</li>
                  </ol>
                </p>

                <p>               
                  <strong>สอบถามเพิ่มเติมติดต่อ:</strong> พี่เบ๊บ: 064-174-7080, พี่ฟง: 092-458-7067, พี่เบนซ์: 085-666-7571
                </p> 

                <p><strong>หมายเหตุ:</strong>  สำหรับน้อง ๆ ที่ไม่สะดวกเดินทางมาสัมภาษณ์ที่อาคาร CP Tower สีลม ให้ Inbox มาทางเพจเฟสบุ๊ค <a href="https://www.facebook.com/ywcth">Young Webmaster Camp</a> ภายในวันที่ 20 พฤศจิกายน 2560</p>
              </v-card-text>
            </v-card>
          </v-expansion-panel-content>
        </v-expansion-panel><!-- End of Interview Panel-->
      </v-flex><!-- End of Description -->
    </v-layout>

    <!-- Name sort toggle -->
    <v-flex class="ml-2 name-sort">
      <v-switch label="Sort by Name" v-model="nameSort" hide-details></v-switch>
    </v-flex><!-- End of Name sort toggle -->

    <v-layout row wrap>
      <!-- Card flex -->
      <v-flex lg3 md4 sm6 xs12 v-for="person in sortedList" :key="person.interviewRef">
        <person-card :person="person" :major="major"></person-card>
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

  data() {
    return {
      nameSort: false
    }
  },
  
  methods: {
    getImgUrl(pet) {
      var images = require.context('../assets/', false, /\.png$/)
      return images('./' + pet)
    }
  },

  computed: {
    sortedList() {
      return this.nameSort ? this.list.sort((a,b) => a.firstName.localeCompare(b.firstName)) : this.list.sort((a,b) => a.interviewRef.slice(2,4) - b.interviewRef.slice(2,4))
    }
  }
}
</script>

<style lang="scss" scoped>
.description {
  .hw {
    margin-left: 10px;
    white-space: pre-wrap; 
    word-wrap: break-word;
    font-family: inherit;
  }

}
</style>
