<script>
export default {
    name: 'SearchForm',
    data: () => ({
        searchText: ''
    }),
    emits: ['submit-search', 'term-change']
}
</script>

<template>
    <!--@submit.prevent-->
    <form @submit.prevent="$emit('submit-search')">
        <input type="text" placeholder="Cerca Film o Serie" v-model.trim="searchText"
            @keyup="$emit('term-change', searchText)">
        <button>Cerca</button>
    </form>
</template>

<style lang="scss"></style>
