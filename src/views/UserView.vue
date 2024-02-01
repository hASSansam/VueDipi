<template>
  <v-card flat>
    <div class="table">
    <v-card-title class="d-flex align-center pe-2">
      <v-icon icon="mdi-video-input-component"></v-icon> &nbsp;
      Users

      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        prepend-inner-icon="mdi-magnify"
        density="compact"
        label="Search"
        single-line
        flat
        hide-details
        variant="solo-filled"
      ></v-text-field>
    </v-card-title>
    <v-divider></v-divider>
      <v-data-table v-model:search="search" :headers="headers" :items="items" return-object > 
      <template v-slot:[`item.image`]="{ item }">
        <router-link :to="{ name: 'search', params: { id: item.id } }">
        <v-card class="my-2" elevation="2" rounded>
          <v-avatar
            :image="item.image"
            size="64"
          ></v-avatar>
        </v-card>
      </router-link>
      </template>
    </v-data-table>
    </div>
  </v-card>
</template>

<style>
.table {
  width: 100%;
  margin: auto;
}
</style>

<script>
import utenti from "/dipi.js"
console.log(utenti)

  export default {
    data () {
      return {
        search: '',
        headers: [
          {key: "image", title:"Avatar"},
          {key: "firstName", title:"Nome"},
          {key: "lastName", title:"Cognome"},
          {key: "age", title:"Età"},
          {key: "gender", title:"Sesso"},
          {key: "email", title:"Email"},
          {key: "phone", title:"Cellulare"},
          {key: "username", title:"UserName"},
          {key: "password", title:"Password"},
          
      
      ],
        items: [],
        selected: []
      }
    },
  methods: 
    {
  },
  mounted() {
    this.items = utenti
  },
  reserve() {
    this.loading = true
    setTimeout(() => (this.loading = false), 2000)
  }
  }
</script>