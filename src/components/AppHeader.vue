<script>
import SearchForm from './SearchForm.vue';
export default {
    name: 'AppHeader',
    emits: ['search-films', 'term-change'],
    components: { SearchForm },

}
</script>

<template>
    <header class="d-flex justify-content-between p-3">
        <div class="text-white">
            Logo
        </div>
        <div>
            <SearchForm @submit-search="$emit('search-films')" @term-change="$emit('term-change', $event)" />
        </div>

    </header>
</template>

<style lang="scss" scoped>
header {
    background-color: black;
}
</style>
