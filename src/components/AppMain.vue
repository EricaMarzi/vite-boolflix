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
        <div v-for="(movie, i) in store" :key="movie.id">{{ movie.title }}</div>
    </main>
</template>

<style lang="scss"></style>
