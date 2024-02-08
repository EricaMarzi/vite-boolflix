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
    store,
    title: ''
  }),
  components: {
    AppHeader, AppMain
  },
  methods: {
    filterTitle(term) {
      store.filter = term

      console.log(term)

    },
    searchEntertainment() {
      if (!store.filter) {
        store.movies = [];
        store.series = [];
        return;
      }

      this.fetchApi('search/movie', 'movies');
      this.fetchApi('search/tv', 'series');

    },

    fetchApi(endpoint, collection) {
      const { baseUri, language, apiKey } = api;

      const apiConfig = {
        params: {
          query: store.filter,
          api_key: apiKey,
          language
        }
      }

      axios.get(`${baseUri}/${endpoint}`, apiConfig).then((res) => {
        store[collection] = res.data.results
      })
    },

  }
}
</script>

<template>
  <AppHeader @search-films="searchEntertainment" @term-change="filterTitle" />
  <AppMain />
</template>

<style lang="scss">
@use './assets/scss/style.scss' as *;
</style>
