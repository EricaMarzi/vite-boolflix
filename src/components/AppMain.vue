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
        <!-- <ul v-for="movie in store.movies" :key="movie.id">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul> -->


        <h2>Serie TV</h2>
        <ProductionCard v-for="serie in store.series" :key="serie.id" :production="serie" />
        <!-- <ul v-for="serie in store.series" :key="serie.id">
            <li>{{ serie.name }}</li>
            <li>{{ serie.original_name }}</li>
            <li>{{ serie.original_language }}</li>
            <li>{{ serie.vote_average }}</li>
        </ul> -->
    </main>
</template>

<style lang="scss">
ul {
    list-style-type: none;
}
</style>
