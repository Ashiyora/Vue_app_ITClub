<template>
  <div class="drop">
    <v-card class="ma-2 card1" elevation="0">
      <h1>เช็คชื่อ</h1>
      <v-sheet id="scrolling-techniques-7" class="overflow-y-auto" max-height="350">
        <v-simple-table>
          <template #default>
            <thead>
              <tr>
                <th class="text-left">
                  เลขที่
                </th>
                <th class="text-left">
                  ชื่อ
                </th>
                <th class="text-left">
                  นามสกุล
                </th>
                <th class="text-left">
                  การเข้าร่วม
                </th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in users_student" :key="item.id">
                <td>{{ item.student_id }}</td>
                <td>{{ item.firstname }}</td>
                <td>{{ item.lastname }}</td>
                <td>
                  <v-radio-group
                    v-model="row[item.id]"
                    row
                  >
                    <v-radio
                      label="มา"
                      value="ma"
                    />
                    <v-radio
                      label="ลา"
                      value="la"
                    />
                    <v-radio
                      label="ขาด"
                      value="cad"
                    />
                  </v-radio-group>
                </td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </v-sheet>
      <br>
      <div class="text-center">
        <v-btn
          color="blue darken-3"
          rounded
          class="btn1"
          dark
          elevation="0"
          @click="onSave"
        >
          SAVE
        </v-btn>
      </div>
      <br>
    </v-card>
    <!-- <v-bottom-navigation
      v-model="value"
      background-color="indigo"
      absolute
    >
      <v-btn href="/home">
        <span style="color:white;">home</span>
        <v-icon style="color:white;">
          mdi-home
        </v-icon>
      </v-btn>
      <v-btn href="/profile">
        <span style="color:white;">profile</span>
        <v-icon style="color:white;">
          mdi-account
        </v-icon>
      </v-btn>
    </v-bottom-navigation> -->
    <h4>row: {{ row }}</h4>
  </div>
</template>

<script>
export default {
  layout: 'Theme1',
  data  () {
    return {
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4'
      ],
      users_student: [
        { id: 1, student_id: '001', firstname: 'นายปฎิnamมากร', lastname: 'เจนจิต', ma: false },
        { id: 2, student_id: '002', firstname: 'นายอภิรักษ์', lastname: 'กาเวสูง', ma: false },
        { id: 3, student_id: '003', firstname: 'นายธนโชติ', lastname: 'จ่าแก้ว', ma: false },
        { id: 4, student_id: '004', firstname: 'นายปิยศักดิ์', lastname: 'จันทร์ต้น', ma: false },
        { id: 5, student_id: '005', firstname: 'นายภูรินทร์', lastname: 'โม้อุ่น', ma: false },
        { id: 6, student_id: '006', firstname: 'นายณัฐดนัย', lastname: 'จันภักดี', ma: false },
        { id: 7, student_id: '007', firstname: 'นายภัทรพงษ์', lastname: 'อาจโยธี', ma: false },
        { id: 8, student_id: '008', firstname: 'นายกฤษฎา', lastname: 'มาตรโคกสูง', ma: false },
        { id: 9, student_id: '009', firstname: 'นายวันชัย', lastname: 'วัฒนะ', ma: false },
        { id: 10, student_id: '010', firstname: 'นายวีรภัทร', lastname: 'ฉัตรหลวง', ma: false }
      ],
      row: []
    }
  },
  created () {
    this.showData()
  },
  methods: {
    async showData () {
      console.log('Showdata')
      // http://localhost:7005/save?name=%27alonkorn%27&age=48
      const res = await fetch('http://localhost:7001/list_std')
      // const data = res.json()
      const data = await res.json()
      this.users_student = data.value
      console.log(this.users_student)
    },
    async onSave () {
      console.log('data=', this.row)
      const res = await fetch('http://localhost:7001/savecheck?data=' + this.row)
      const data = await res.json()
      this.users_student = data.value
      this.$router.push('/home')
    }
  }
}
</script>

<style>
.card1{
  padding: 14px;
}
.btn1{
  width: 140px;
}
.drop{
  margin-top: 30px;
}
</style>
