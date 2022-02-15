<template>
  <section>
    <ul>

      <div class="position-abs">
        <div class="info-card">
          <li><h2>{{ item.title || item.name }}</h2></li>
          <li><h5>({{ item.original_title || item.original_name }})</h5></li>
          <li v-if="item.original_language === 'en' || item.original_language === 'it'">
            <img :src="require (`../assets/img/${item.original_language}.png`)" :alt="`${item.original_language}`">
          </li>
          <li v-else>{{ item.original_language }}</li>
          <li>{{ item.vote_average / 2 }}</li>
          <Star :item="item"/>
        </div>
      </div>
      <div class="img-container my-4">
        <div v-if="!item.poster_path">
          <li class="img-null">IMMAGINE NON DISPONIBILE</li>
        </div>
        <div v-else>
          <li><img :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" :alt="item.poster_path"></li>
        </div>
      </div>

    </ul>

  </section>
</template>

<script>
import Star from "./Star.vue"

export default {
    name: "Card",

    components: {
      Star,
    },

    props: ["item"],

    data() {
      return {
        newVote: "",
      }
    },

    methods: {
      getVote() {
        this.newVote = this.item.vote_average / 2;
      }
    }

    
}
</script>

<style scoped lang="scss">
@import '../assets/scss/style.scss';

  ul {
    position: relative;
  }

  .position-abs {
    position: absolute;
    .info-card {
      width: 342px;
      height: 520px;
      background-color: black;
      img {
        width: 100px;
      }
      li {
        padding: 10px;
        text-align: center;
        font-weight: bold;
        color: white;
      }
    }
  }

  .img-container {
    height: 520px;
    width: 342px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    opacity: 1;
    transition: opacity 1s linear;
    img {
      height: 520px;
      width: 342px;
    }
  }

  .img-container:hover {
    transition: opacity 1s linear;
    opacity: 0;
  }

  .img-null {
    height: 520px;
    width: 342px;
    background-color: lightgray;
    line-height: 520px;
    text-align: center;
  }

  li {
    list-style-type: none;
  }
</style>