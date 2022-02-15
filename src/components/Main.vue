<template>
  <section>

    <div v-if="!getMovie">
      <p>Cerca un film o una serie TV</p>
    </div>

    <div v-else>

      <h1>Film</h1>
      <ul v-for="(movie, index) in movies" :key="index">
        <li>{{ movie.title }}</li>
        <li>{{ movie.original_title }}</li>
        <div>
          <li v-if="movie.original_language === 'en' || movie.original_language === 'it'">
            <img :src="require (`../assets/img/${movie.original_language}.png`)" :alt="`${movie.original_language}`">
          </li>
          <li v-else>{{ movie.original_language }}</li>
        </div>
        <li>{{ movie.vote_average }}</li>
        <li><img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt=""></li>
      </ul> 

      <h1>Serie</h1>
      <ul v-for="(serie, index) in series" :key="index">
        <li>{{ serie.name }}</li>
        <li>{{ serie.original_name }}</li>
        <div>
          <li v-if="serie.original_language === 'en' || serie.original_language === 'it'">
            <img :src="require (`../assets/img/${serie.original_language}.png`)" :alt="`${serie.original_language}`">
          </li> 
          <li v-else>{{ serie.original_language }}</li>
        </div>
        <li>{{ serie.vote_average }}</li>
        <li><img :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt=""></li>
      </ul>  
    </div>
  </section>
</template>

<script>
export default {
    name: "Main",

    props: ["movies", "series", "getMovie"],

    methods: {
      getElement() {}
    }
}
</script>

<style scoped lang="scss">

</style>