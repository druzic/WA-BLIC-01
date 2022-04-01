<template>
  <v-container>
    <v-card>
      <v-card-title>Naziv knjige: {{ ime }} </v-card-title>
      <v-card-subtitle> Autor: {{ autor }}</v-card-subtitle
      ><v-card-subtitle> Datum izdavanja: {{ datum }}</v-card-subtitle></v-card
    >
    <v-card-actions
      ><router-link :to="{ name: 'Info', params: { kod: id } }"
        ><v-btn style="color: purple">more info</v-btn></router-link
      ></v-card-actions
    >
  </v-container>
</template>

<script>
export default {
  name: "Kartica",
  props: {
    id: String,
    ime: String,
    datum: String,
    autor: String,
  },
};
</script>
