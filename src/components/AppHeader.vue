<script>
import axios from 'axios';
import SearchForm from './SearchForm.vue';
const movieEndpoint = 'https://api.themoviedb.org/3/search/movie?api_key=58af0113a84f8b3226f413927cf278f8&language=it-IT';
import { store } from '../assets/data/store';
export default {
    name: 'AppHeader',
    components: { SearchForm },
    methods: {
        searchFilms(searchText) {
            console.log('cerca: ', searchText)
            const searchMovieEndpoint = `${movieEndpoint}&query=${searchText}`;
            console.log(searchMovieEndpoint)
            // axios.get(searchMovieEndpoint).then(res => {
            //     this.store = res.data.result
            // })
            // console.log(res.data.result)
        }
    }
}
</script>

<template>
    <header class="d-flex justify-content-between p-3">
        <div class="text-white">
            Logo
        </div>
        <div>
            <SearchForm @submit-search="searchFilms" />
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
    background-color: black;
}
</style>
