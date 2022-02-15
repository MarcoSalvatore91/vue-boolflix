<template>
  <div>
    <div>
        <i class="fa-solid fa-star" v-for="(star, index) in getStar()" :key="index"></i>
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
           return  Math.ceil(this.item.vote_average / 2)
        }
    },
}
</script>

<style scoped lang="scss">
    i {
        color: white;
    }
</style>