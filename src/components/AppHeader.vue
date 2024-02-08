<script>
import SearchForm from './SearchForm.vue';
export default {
    name: 'AppHeader',
    emits: ['search-films', 'term-change'],
    components: { SearchForm },

}
</script>

<template>
    <header class="d-flex justify-content-between align-items-center p-3">
        <a href="#">
            <img class="logo" src="../assets/img/netflix-logo.svg.png" alt="Netflix">
        </a>

        <div>
            <SearchForm @submit-search="$emit('search-films')" @term-change="$emit('term-change', $event)" />
        </div>

    </header>
</template>

<style lang="scss" scoped>
img.logo {
    height: 30px;
}
</style>
