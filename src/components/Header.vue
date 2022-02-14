<template>
    <div>
        <input v-model="getMovie" type="text" placeholder="Cosa vuoi guardare?">
        <button @click="$emit('search', getMovie)">Cerca</button>
    </div>
</template>

<script>
export default {
    name: "Header",

    data() {
        return {
            getMovie: "",
        }
    },

    methods: {
        
    }
}
</script>

<style scoped lang="scss">

</style>