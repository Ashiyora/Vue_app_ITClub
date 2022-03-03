<template>
  <div style="margin-top: 5%;">
    <v-container>
      <center>
        <v-img src="images/CHTC.png" height="120" width="120" />
      </center>
    </v-container>
    <div class="text-center">
      <v-dialog
        v-model="dialog"
        width="500"
      >
        <v-card>
          <v-card-title class="text-h5 green darken-2">
            <p style="color:white;">
              Status Login
            </p>
          </v-card-title>

          <v-card-text>
            <v-container>
              <center>
                <v-img src="images/success.png" height="90" width="90" />
                <br>
                <p style="font-size: 20px; color:green;">
                  Login successful
                </p>
              </center>
            </v-container>
          </v-card-text>

          <v-divider />

          <!-- <v-card-actions>
            <v-spacer />
            <v-btn
              color="primary"
              text
              @click="dialog = false"
            >
              I accept
            </v-btn>
          </v-card-actions> -->
        </v-card>
      </v-dialog>
    </div>
    <div class="text-center">
      <v-dialog
        v-model="dialog_false"
        width="500"
      >
        <v-card>
          <v-card-title class="text-h5 red darken-2">
            <p style="color:white;">
              Status Login
            </p>
          </v-card-title>

          <v-card-text>
            <v-container>
              <center>
                <v-img src="images/fail.png" height="90" width="90" />
                <br>
                <p style="font-size: 20px; color:red;">
                  Login failed
                </p>
              </center>
            </v-container>
          </v-card-text>

          <v-divider />

          <!-- <v-card-actions>
            <v-spacer />
            <v-btn
              color="primary"
              text
              @click="dialog_false = false"
            >
              I accept
            </v-btn>
          </v-card-actions> -->
        </v-card>
      </v-dialog>
    </div>

    <v-card elevation="3" shaped light class="card1">
      <strong class="p">
        SIGN IN
      </strong>
      <v-form class="text-center drop">
        <v-text-field
          v-model="firstname"
          label="Username"
          outlined
        />
        <v-text-field
          v-model="user_type"
          label="Password"
          type="password"
          outlined
          class="btn2"
        />

        <v-btn rounded class="btn" color="#3D4E88" dark @click="Login">
          LOG IN
        </v-btn>
      </v-form>
      <br>
    </v-card>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data: () => ({
    firstname: '',
    user_type: '',
    dialog: false,
    dialog_false: false,
    user: ''
  }),
  methods: {
    async Login () {
      const std = {
        firstname: this.firstname,
        user_type: this.user_type
      }
      //  console.log('user:', std)
      const res = await axios.post('http://localhost:7001/Login', std)
      console.log('data=', res.data.datas.id)
      this.id = res.data.datas.id
      try {
        if (res.data.status > 0) {
          console.log('Login successful')
          this.dialog = true
          this.firstname = ''
          this.user_type = ''
          setInterval(() => {
            this.dialog = false
            this.$router.push('/home?id=' + this.id)
          }, 2000)
        } else {
          this.dialog_false = true
          setInterval(() => {
            this.dialog_false = false
            this.$router.push('/login')
          }, 3000)
        }
      } catch (error) {
        console.log('Error Login')
      }
    }
  }
}
</script>

<style>
.card1{
    padding: 40px;
    margin-top: 10px;
}
.p{
  color: #3D4E88;
  font-size: 28px;
}
.txt1{
    color: brown;
  }

.btn{
    width: 150px;
    margin-top: 10px;
  }
.btn2{
    margin-top: -10px;
  }
</style>
