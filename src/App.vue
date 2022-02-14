<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",

  data() {
    return {
      api_key: "0fe42dceece4f3ca88e1c2b3123892c7",
      query: "",
    }
  },

  components: {
    Header,
    Main,
  },

  methods: {
    fetchMovie() {

      const config = {
        params: {
          api_key: this.api_key,
          query: this.query,
          language: 'it-IT'
        }
      }

      axios.get("https://api.themoviedb.org/3/search/movies", config).then((res) => {
        this.movies = res.data.results;
      })
    }
  }
};
</script>

<style lang="scss">

</style>
