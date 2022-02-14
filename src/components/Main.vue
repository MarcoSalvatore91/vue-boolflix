<template>
  <section>
    <ul v-for="(movie, index) in movies" :key="index">
      <li>{{ movie.title }}</li>
      <li>{{ movie.original_title }}</li>
      <li>{{ movie.original_language }}</li>
      <li>{{ movie.vote_average }}</li>
    </ul>  
  </section>
</template>

<script>
export default {
    name: "Main",

    props: ["movies"],
}
</script>

<style scoped lang="scss">

</style>