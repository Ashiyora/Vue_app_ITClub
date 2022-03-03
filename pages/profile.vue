<template>
  <div>
    <v-btn color="transparent" elevation="0" href="/home">
      <v-icon style="color:white">
        mdi-arrow-left
      </v-icon>
    </v-btn>
    <br><br>
    <v-card class="ma-2 card1 drop" elevation="3">
      <div class="text-center drop">
        <v-icon style="font-size: 120px;">
          mdi-account-circle
        </v-icon>
      </div>
      <br>
      <div class="p">
        <p><span>ชื่อ : {{ fname }}</span></p>
        <p><span>นามสกุล : {{ lname }}</span></p>
        <p><span>E-mail : {{ email }}</span></p>
      </div>

      <br><br><br>
      <div class="text-center">
        <v-btn
          color="blue darken-3"
          rounded
          class="btn1"
          dark
          elevation="0"
          href="/edit_profile"
        >
          <v-icon>mdi-pencil</v-icon> EDIT
        </v-btn>
        <br>
        <v-btn
          color="error"
          rounded
          class="btn1 drop2"
          dark
          elevation="0"
          href="/"
        >
          <v-icon>mdi-logout</v-icon> LOGOUT
        </v-btn>
      </div>
      <br>
    </v-card>
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
        { group_id: '005', fisrtname: 'Name5', lastname: 'phukongka5', email: 'Name1' }
      ],
      fname: '',
      lname: '',
      email: ''
    }
  },
  created () {
    this.showData()
  },
  methods: {
    async showData () {
      console.log('Showdata', this.$route.query.id)
      this.id = this.$route.query.id
      // http://localhost:7005/save?name=%27alonkorn%27&age=48
      const res = await fetch('http://localhost:7001/list1?id=' + this.id)
      // const data = res.json()
      const data = await res.json()
      this.users = data.value
      this.fname = data.value.firstname
      this.lname = data.value.lastname
      this.email = data.value.email
      console.log('user:', this.users)
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
.p{
  font-size: 35px;
  font-family: 'PSL Display';
}
</style>
