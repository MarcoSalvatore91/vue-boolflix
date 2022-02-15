<template>
  <div>
    <div>
        <i class="fa-solid fa-star" v-for="(star, index) in getStar()" :key="index"></i>
        <i class="fa-regular fa-star" v-for="allStar in allGetStar()" :key="allStar"></i>
    </div>
  </div>
</template>

<script>
export default {
    name: "Star",

    props: ["item"],

    data() {
        return {
        }
    },

    methods: {
        getStar() {
           return  Math.ceil(this.item.vote_average / 2);
        },
        allGetStar() {
            return 5 - this.getStar();
        },
    },
}
</script>

<style scoped lang="scss">
    i {
        color: white;
    }
</style>