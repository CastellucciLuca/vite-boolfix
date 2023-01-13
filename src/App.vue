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
      apiUrl: 'https://api.themoviedb.org/3/search/movie?'
    }
  },
  methods: {
    getFilmApi(userQuery) {
      axios.get(this.apiUrl, {
        params: {
          api_key: 'afbf158776bc993869bf790f7b9b71de',
          language: 'it-IT',
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
    },
  },
  created() {
    // this.getFilmApi(this.apiUrl)
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