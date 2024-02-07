<script>
import SearchBar from './SearchBar.vue'
export default {
    name: 'AppHeader',
    components: { SearchBar }
}
</script>

<template>
    <header class="d-flex justify-content-between p-3">
        <div class="text-white">
            Logo
        </div>
        <div>
            <SearchBar />
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
    background-color: black;
}
</style>
