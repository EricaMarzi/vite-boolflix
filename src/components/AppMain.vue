<script>
import { store } from '../assets/data/store.js';
export default {
    name: 'AppMain',
    data: () => ({
        store
    })
}
console.log({ store })
</script>

<template>
    <main>
        <ul v-for="movie in store.movies" :key="movie.id">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>
    </main>
</template>

<style lang="scss">
ul {
    list-style-type: none;
}
</style>
