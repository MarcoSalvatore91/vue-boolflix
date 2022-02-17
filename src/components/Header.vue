<template>
    <div id="head">
        <section class="d-flex justify-content-between">
            <div class="ms-2">
                <h3>BOOLFLIX</h3>
            </div>
            <div class="form-input me-2">
                <input v-model="getProducts" type="text" placeholder="Cosa vuoi guardare?">
                <button @click="$emit('search', getProducts)">Cerca</button>
            </div>
        </section>
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
}
</script>

<style scoped lang="scss">
@import '../assets/scss/style.scss';

#head {
    background-color: black;
    height: 100px;
}

h3 {
    color: red;
    line-height: 100px;
}

.form-input input, .form-input button {
    margin-top: 40px;
}
</style>