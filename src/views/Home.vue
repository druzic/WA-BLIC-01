<template>
  <v-container>
    <Kartica
      v-for="got in got"
      :key="got.isbn"
      :ime="got.name"
      :autor="got.authors[0]"
      :datum="got.released"
      :id="got.isbn"
  /></v-container>
</template>

<script>
// @ is an alias to /src
import Kartica from "@/components/Kartica.vue";
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      got: [],
    };
  },
  components: {
    Kartica,
  },
  async mounted() {
    const dohvati = await axios.get(
      "http://ntankovic.unipu.hr:8000/books.json"
    );
    this.got = dohvati.data;
    console.log(this.got);
  },
};
</script>
