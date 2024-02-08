<script>
import { store } from '../assets/data/store.js';
import ProductionCard from './ProductionCard.vue';
export default {
    name: 'AppMain',
    data: () => ({
        store
    }),
    components: {
        ProductionCard
    }
}
console.log({ store })
</script>

<template>
    <main>
        <h2>Film</h2>
        <ProductionCard v-for="movie in store.movies" :key="movie.id" :production="movie" />


        <h2>Serie TV</h2>
        <ProductionCard v-for="serie in store.series" :key="serie.id" :production="serie" />
    </main>
</template>

<style lang="scss">
ul {
    list-style-type: none;
}
</style>
