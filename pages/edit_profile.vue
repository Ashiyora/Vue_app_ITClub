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
      <div v-for="item in id" :key="item.name" class="card1">
        ชื่อ-สกุล : <v-text-field v-model="name" label="name" />
        แผนก : <v-text-field v-model="dep" label="dep" />
        อีเมล์ : <v-text-field v-model="email" label="email" />
      </div>
      <br><br>
      <div class="text-center">
        <v-btn
          color="blue darken-3"
          rounded
          class="btn1"
          dark
          elevation="0"
          href="/profile"
        >
          <v-icon>mdi-pencil</v-icon> SAVE
        </v-btn>
      </div>
      <br>
    </v-card>
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
</style>
