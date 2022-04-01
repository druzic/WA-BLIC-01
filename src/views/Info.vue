<template>
  <v-container v-if="got"
    ><v-card
      ><v-card-title> ISBN: {{ got.isbn }}</v-card-title>
      <v-card-subtitle>Autor: {{ got.authors }}</v-card-subtitle>
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
  data() {
    return {
      got: [],
      kod: this.$route.params.kod,
    };
  },

  async mounted() {
    const dohvati = await axios.get(
      "http://ntankovic.unipu.hr:8000/books.json/${this.kod}"
    );
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
