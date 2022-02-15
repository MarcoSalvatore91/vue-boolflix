<template>
    <div>
        <input v-model="getProducts" type="text" placeholder="Cosa vuoi guardare?">
        <button @click="$emit('search', getProducts)">Cerca</button>
    </div>
</template>

<script>
export default {
    name: "Header",

    data() {
        return {
            getProducts: "",
        }
    },

    methods: {
        
    }
}
</script>

<style scoped lang="scss">

</style>