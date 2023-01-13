<script >
import {store} from './store.js';
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
    getFilmApi(importUrl) {
      axios.get(importUrl, {
        params: {
          api_key: 'afbf158776bc993869bf790f7b9b71de',
          language: 'it-IT',
          query: 'a'
        }
      })
        .then(function (response) {
          console.log(response.data);
        })
        .catch(function (error) {
          console.log(error);
        })
    },
  },
  created() {
    this.getFilmApi(this.apiUrl)
  },
}
</script>