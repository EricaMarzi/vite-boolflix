<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './assets/data/store.js';
import { api } from './assets/data/index.js'
const movieEndpoint = 'https://api.themoviedb.org/3/search/movie?api_key=58af0113a84f8b3226f413927cf278f8&language=it-IT';
const tvEndpoint = 'https://api.themoviedb.org/3/search/tv?api_key=58af0113a84f8b3226f413927cf278f8&language=it-IT';
export default {
  name: 'Boolflix',
  data: () => ({
    store
  }),
  components: {
    AppHeader, AppMain
  },
  methods: {
    searchFilms(searchText) {
      if (!searchText) {
        store.movies = [];
        store.series = [];
        return;
      }

      const { baseUri, language, apiKey } = api;

      const apiConfig = {
        params: {
          query: searchText,
          api_key: apiKey,
          language
        }
      }

      axios.get(`${baseUri}/search/movie`, apiConfig).then((res) => {
        store.movies = res.data.results
        console.log(res.data.results)
      })
    }
  }
}
</script>

<template>
  <AppHeader @search-films="searchFilms" />
  <AppMain />
</template>

<style lang="scss">
@use './assets/scss/style.scss' as *;
</style>
