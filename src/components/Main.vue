<template>
  <section>

    <div class="preview-search" v-if="!getProducts">
      <h1 class="text-center fw-bold">Cerca un film o una serie TV</h1>
    </div>

    <div v-else class="container-fluid">

      <h1 class="py-4 text-center">Film</h1>
      
      <div class="row">
        <Card class="col-4" v-for="(movie, index) in movies" :key="index" :item="movie" />
      </div>

      <h1 class="py-4 text-center">Serie</h1>

      <div class="row text-center">
        <Card class="col-4" v-for="(serie, index) in series" :key="index" :item="serie" />
      </div>
         
    </div>
  </section>
</template>

<script>
import Card from "./Card.vue"

export default {
    name: "Main",

    components: {
      Card,
    },

    props: ["movies", "series", "getProducts"],
    
}
</script>

<style scoped lang="scss">
@import '../assets/scss/style.scss';

section {
  background-color: rgb(83,93,102);
}

.preview-search {
  height: calc(100vh - 100px);
  background-color: grey;
}

h1 {
  color: white;
}

</style>