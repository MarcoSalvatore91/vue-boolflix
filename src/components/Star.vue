<template>
  <div>
    <div>
        <i v-for="number in 5" :key="number"
        class="fa-star"
        :class="number <= getStar ? 'fa-solid' : 'fa-regular'"></i>
    </div>
  </div>
</template>

<script>
export default {
    name: "Star",

    props: ["item"],

    computed: {
        getStar() {
           return  Math.ceil(this.item.vote_average / 2);
        },
    }
}
</script>

<style scoped lang="scss">
    i {
        color: white;
    }
</style>