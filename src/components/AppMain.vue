<script>
import { store } from '../assets/data/store';
export default {
    name: 'AppMain',
    data: () => ({
        store
    })
}
</script>

<template>
    <main>
        <ul v-for="(movie, i) in store.movies" :key="movie.id">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>
    </main>
</template>

<style lang="scss"></style>
