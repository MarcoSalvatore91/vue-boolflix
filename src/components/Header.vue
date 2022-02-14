<template>
    <div>
        <input v-model="query" type="text" placeholder="Cosa vuoi guardare?">
        <button @click="$emit('search', query)">Cerca</button>
    </div>
</template>

<script>
export default {
    name: "Header",

    data() {
        return {
            query: "",
        }
    }
}
</script>

<style scoped lang="scss">

</style>