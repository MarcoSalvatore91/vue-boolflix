<template>
  <section>
    <ul>

      <div class="position-abs">
        <div class="info-card">
          <li><h2>{{ item.title || item.name }}</h2></li>
          <li><span>({{ item.original_title || item.original_name }})</span></li>
          <li v-if="item.original_language === 'en' || item.original_language === 'it'">
            <img :src="require (`../assets/img/${item.original_language}.png`)" :alt="`${item.original_language}`">
          </li>
          <li v-else>{{ item.original_language }}</li>
          <li><Star :item="item"/></li>
          <div v-for="(cast, index) in casts" :key="index">
            <li v-if="index < 5">{{ casts[index].name }}</li>
          </div>
        </div>
      </div>
      <div class="img-container my-4">
        <div v-if="!item.poster_path">
          <li class="img-null"><img src="../assets/img/poster-placeholder.png" alt="Img-Null"></li>
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
import axios from 'axios';

export default {
    name: "Card",

    components: {
      Star,
    },

    props: ["item"],

    data() {
      return {
        api_key: "0fe42dceece4f3ca88e1c2b3123892c7",
        id: [this.item.id],
        casts: [],
      }
    },

    methods: {

      fetchCast() {
        axios.get(`https://api.themoviedb.org/3/movie/${this.id}/credits?api_key=${this.api_key}&language=it-IT&`).then((res) => {
        this.casts = res.data.cast;
      })
      }
    },

      mounted() {
        this.fetchCast();
      },

}
</script>

<style scoped lang="scss">
@import '../assets/scss/style.scss';

  ul {
    position: relative;
  }

  .position-abs {
    position: absolute;
    z-index: 1;
    opacity: 0;
    transition: opacity 1s linear;
    overflow-y: scroll;
    max-height: 520px;
    width: 342px;
    .info-card {
      min-height: 520px;
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

  .position-abs:hover {
    transition: opacity 1s linear;
    opacity: 1;
  }

  .img-container {
    height: 520px;
    width: 342px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    img {
      height: 520px;
      width: 342px;
    }
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