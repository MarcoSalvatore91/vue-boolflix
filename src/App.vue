<template>
  <div id="app">
    <Header @search="fetchMovie" />
    <Main :movies="movies" :series="series" :getMovie="getMovie" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",

    components: {
      Header,
      Main,
    },

    data() {
      return {
        movies: [],
        series: [],
        api_key: "0fe42dceece4f3ca88e1c2b3123892c7",
        getMovie: "",
      }
    },


  methods: {

    fetchMovie(element) {

      this.getMovie = element;

      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.api_key}&language=it-IT&query=${this.getMovie}`).then((res) => {
        this.movies = res.data.results;
      })

      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.api_key}&language=it-IT&query=${this.getMovie}`).then((res) => {
        this.series = res.data.results;
      })
    }

    },

    mounted() {
      this.fetchMovie();
    },
};
</script>

<style lang="scss">

</style>
