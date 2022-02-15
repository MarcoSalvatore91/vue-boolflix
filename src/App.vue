<template>
  <div id="app">
    <Header @search="fetchMovie" />
    <Main :movies="movies" :series="series" :getProducts="getProducts" />
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
        getProducts: "",
      }
    },


  methods: {

    fetchMovie(element) {

      this.getProducts = element;

      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.api_key}&language=it-IT&query=${this.getProducts}`).then((res) => {
        this.movies = res.data.results;
      })

      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.api_key}&language=it-IT&query=${this.getProducts}`).then((res) => {
        this.series = res.data.results;
      })
    }

    },

    mounted() {
      this.fetchMovie();
    },
};
</script>

<style scoped lang="scss">
@import './assets/scss/style.scss';

#app {
  height: 100vh;
}
</style>
