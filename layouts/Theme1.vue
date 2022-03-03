<template>
  <v-app>
    <div class="bg1">
      <span class="white--text">
        <v-container>
          <Nuxt />
        </v-container>
      </span>
    </div>
    <v-bottom-navigation
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
    </v-bottom-navigation>
  </v-app>
</template>

<script>
export default {
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
      user: ''
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
      this.users = data.value.firstname
      this.fname = data.value.firstname
      console.log('user:', this.users)
    },
    profile () {
      this.$router.push('/profile?id=' + this.id)
    }
  }
}

</script>

<style>
.bg1{
  background: url('../assets/images/bg2.png');
  background-size: cover;
  background-attachment: fixed;
  height: 100%;
}
.drop{
  margin-top: 30px;
}
.drop2{
  margin-top: 5px;
}
.drop3{
  margin-top: 140px;
}
</style>
