<template>
  <section>
    <ul>

        <li>{{ item.title || item.name }}</li>
        <li>{{ item.original_title || item.original_name }}</li>
        <div>
            <li v-if="item.original_language === 'en' || item.original_language === 'it'">
            <img :src="require (`../assets/img/${item.original_language}.png`)" :alt="`${item.original_language}`">
            </li>
            <li v-else>{{ item.original_language }}</li>
        </div>
        <li>{{ item.vote_average }}</li>
        <li><img :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" :alt="item.poster_path"></li>

    </ul>

  </section>
</template>

<script>
export default {
    name: "Card",

    props: ["item"],
}
</script>

<style scoped lang="scss">

</style>