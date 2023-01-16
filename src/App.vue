<script >
import { store } from './store.js';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
  name: 'App',
  components: { AppHeader, AppMain },
  data() {
    return {
      store,
      apiKey: 'afbf158776bc993869bf790f7b9b71de',
      languageApi: 'it-IT',
      apiUrlFilm: 'https://api.themoviedb.org/3/search/movie?',
      apiUrlTv: 'https://api.themoviedb.org/3/search/tv?'
    }
  },

  methods: {
    //FILM ARRAY
    getFilmApi(userQuery) {
      // FILM
      axios.get(this.apiUrlFilm, {
        params: {
          api_key: this.apiKey,
          language: this.languageApi,
          query: userQuery
        }
      })
        .then(function (response) {
          console.log(response.data.results);
          store.filmList = response.data.results;
        })
        .catch(function (error) {
          console.log(error);
        })
      // TV SERIES
      axios.get(this.apiUrlTv, {
        params: {
          api_key: this.apiKey,
          language: this.languageApi,
          query: userQuery
        }
      })
        .then(function (response) {
          console.log(response.data.results);
          store.filmList.push(...response.data.results);
        })
        .catch(function (error) {
          console.log(error);
        })
    },
  },
}
</script>

<template>
  <!-- IMPORT HEADER -->
  <AppHeader @sendResearch="getFilmApi" />
  <!-- IMPORT MAIN -->
  <AppMain />

</template>

<style>
</style>