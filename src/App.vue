<template>
  <div id="app">
    <Header @search="fetchMovie"/>
    <Main :movies="movies" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",

  data() {
    return {
      movies: [],
      api_key: "0fe42dceece4f3ca88e1c2b3123892c7",
      query: "",
    }
  },

  components: {
    Header,
    Main,
  },

  methods: {

    fetchMovie(element) {
      this.query = element;
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.api_key}&language=it-IT&query=${this.query}`).then((res) => {
        this.movies = res.data.results;
      })
    },
    },

    mounted() {
      this.fetchMovie();
    },
};
</script>

<style lang="scss">

</style>
