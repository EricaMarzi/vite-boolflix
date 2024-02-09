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
    <main class="p-5">
        <div class="container-fluid">
            <section>
                <h2>Film</h2>
                <div class="row row-cols-7">

                    <ProductionCard v-for="movie in store.movies" :key="movie.id" :production="movie" />

                </div>
            </section>


            <section class="pt-5">
                <h2>Serie TV</h2>
                <div class="row row-cols-7">

                    <ProductionCard v-for="serie in store.series" :key="serie.id" :production="serie" />

                </div>
            </section>
        </div>
    </main>
</template>

<style lang="scss" scoped>
.row {
    gap: 20px
}
</style>
