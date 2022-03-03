<template>
  <div>
    <v-card class="ma-2 card1 drop" elevation="3">
      <v-sheet id="scrolling-techniques-7" class="overflow-y-auto" max-height="490">
        <div class="drop2">
          <h2>กิจกรรม</h2>
        </div>
        <div class="drop" align="right">
          <v-textarea
            outlined
            name="input-7-4"
            label="บันทึกกิจกรรม"
          />
          <v-btn
            href="/activity"
            color="blue darken-3"
            rounded
            class="btn1 drop3"
            dark
            elevation="0"
          >
            SAVE
          </v-btn>
        </div>
      </v-sheet>
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
  </div>
</template>

<script>
export default {
  layout: 'Theme1',
  data: () => ({
    id: [
      { name: 'name Surname', dep: 'Information Technology', email: 'a@gmail.com' }
    ]
  })
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
  margin-top: 20px;
}
.drop2{
  margin-top: 5px;
}
.drop3{
  margin-bottom: 80%;
}
</style>
