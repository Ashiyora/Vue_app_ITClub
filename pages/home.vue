<template>
  <div style="margin-top: 8%;">
    <v-container>
      <v-icon style="font-size: 110px;">
        mdi-account-circle
      </v-icon>
      <strong class="text1">{{ fname }} {{ lname }}</strong>
    </v-container>

    <v-row class="drop3 text-center">
      <v-col>
        <v-btn
          href="/check"
          class="mx-2"
          fab
          dark
          x-large
          color="#8B9DB9"
          style="font-size: 40px; color: #000;"
        >
          <v-icon dark>
            mdi-text-box-outline
          </v-icon>
        </v-btn>
        <p class="text2">
          เช็คชื่อ
        </p>
      </v-col>

      <v-col style="margin-bottom: 20%;">
        <v-btn
          href="/activity"
          class="mx-2"
          fab
          dark
          x-large
          color="#8B9DB9"
          style="font-size: 40px; color: #000;"
        >
          <v-icon dark>
            mdi-calendar-text
          </v-icon>
        </v-btn>
        <p class="text2">
          กิจกรรม
        </p>
      </v-col>
    </v-row>
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
      <v-btn @click="profile">
        <span style="color:white;">profile</span>
        <v-icon style="color:white;">
          mdi-account
        </v-icon>
      </v-btn>
    </v-bottom-navigation> -->
  </div>
</template>

<script>
export default {
  layout: 'Theme1',
  data () {
    return {
      dialog: false,
      dialogDelete: false,
      users: [
        { group_id: '001', fisrtname: 'Name1', lastname: 'phukongka1', email: 'Name1' },
        { group_id: '002', fisrtname: 'Name2', lastname: 'phukongka2', email: 'Name1' },
        { group_id: '003', fisrtname: 'Name3', lastname: 'phukongka3', email: 'Name1' },
        { group_id: '003', fisrtname: 'Name4', lastname: 'phukongka4', email: 'Name1' },
        { group_id: '005', fisrtname: 'Name5', lastname: 'phukongka5', email: 'Name1' }
      ],
      id: '',
      fname: '',
      lname: '',
      user: ''
    }
  },
  created () {
    this.showData()
  },
  methods: {
    async showData () {
      // console.log('Showdata', this.$route.query.id)
      this.id = this.$route.query.id
      // http://localhost:7005/save?name=%27alonkorn%27&age=48
      const res = await fetch('http://localhost:7001/list1?id=' + this.id)
      // const data = res.json()
      const data = await res.json()
      this.users = data.value.firstname
      this.fname = data.value.firstname
      this.lname = data.value.lastname
      // console.log('user:', this.users)
    }
    // profile () {
    //   this.$router.push('/profile?id=' + this.id)
    // }
  }
}

</script>

<style>
.text1{
  font-size: 40px;
  font-family: 'PSL Display';
}
.text2{
  margin-top: 10px;
  color:#18275B;
  font-size: 30px;
  font-family: 'PSL Display';
}
</style>
