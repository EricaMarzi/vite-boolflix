<script>
export default {
    name: 'SearchForm',
    data: () => ({
        searchText: ''
    }),
    emits: ['submit-search']
}
</script>

<template>
    <!--@submit.prevent-->
    <form @submit.prevent="$emit('submit-search', searchText)">
        <input type="text" placeholder="Cerca Film o Serie" v-model.trim="searchText">
        <button>Cerca</button>
    </form>
</template>

<style lang="scss"></style>
