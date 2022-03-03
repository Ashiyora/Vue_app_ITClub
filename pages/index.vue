<template>
  <div style="margin-top: 50%;">
    <v-container>
      <center>
        <v-img src="images/logo2.png" height="170" width="190" />
        <strong class="p">
          กิจกรรมชมรม<br>
          Chaiyaphum Technical College<br><br>
        </strong>
        <v-btn rounded class="btn" color="#3D4E88" dark href="/login">
          LOG IN
        </v-btn>
      </center>
    </v-container>
  </div>
</template>

<script>
export default {
  layout: 'Theme2'
  // created () {
  //   this.nextpage()
  // },
  // methods: {
  //   nextpage () {
  //     console.log('nextpage')
  //     setInterval(() => {
  //       this.$router.push('/login')
  //     }, 3000)
  //   }
  // }
}
</script>

<style>
.btn{
    width: 150px;
  }
</style>
