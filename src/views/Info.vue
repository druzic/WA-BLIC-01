<template>
  <v-container
    ><v-card
      ><v-card-title> ISBN: {{ got.isbn }}</v-card-title>
      <v-card-subtitle v-for="author in got.authors" :key="author"
        >Autor: {{ author }}</v-card-subtitle
      >
      <v-card-subtitle>Broj stranica: {{ got.numberOfPages }}</v-card-subtitle>
      <v-card-subtitle>Izdavač: {{ got.mediaType }}</v-card-subtitle>
      <v-card-subtitle>Zemlja podrijetla: {{ got.country }}</v-card-subtitle>
      <v-btn @click="back()">go bak</v-btn>
    </v-card>
  </v-container>
</template>
<script>
import axios from "axios";
export default {
  name: "Info",
  data() {
    return {
      got: [],
      kod: this.$route.params.kod,
    };
  },

  async mounted() {
    console.log(this.kod);

    const dohvati = await axios.get(`${this.kod}`);
    this.got = dohvati.data;
    console.log(this.got);
  },
  methods: {
    back() {
      this.$router.push("/");
    },
  },
};
</script>
