<template>
  <section>
    <ul v-for="(movie, index) in movies" :key="index">
      <li>{{ movie.title }}</li>
      <li>{{ movie.original_title }}</li>
      <div>
        <li v-if="movie.original_language === 'en'">
          <img src="../assets/img/en.png" alt="England Flag">
        </li>
        <li v-else-if="movie.original_language === 'it'">
          <img src="../assets/img/it.png" alt="Italian Flag">
        </li> 
        <li v-else>{{ movie.original_language  }}</li>
      </div>
      <li>{{ movie.vote_average }}</li>
    </ul>  
  </section>
</template>

<script>
export default {
    name: "Main",

    props: ["movies"],

    methods: {
      
    }
}
</script>

<style scoped lang="scss">

</style>