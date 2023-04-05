<script >
import { store } from './store.js';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue'

export default {
  data() {
    return {
      store
    }
  },
  components: {
    AppHeader,
    AppMain
  },
  created() {
    this.getMovies();
    this.getTvShows();
  },
  methods: {
    doResearch() {

      const paramsObj = {
        params: {
          api_key: this.store.apiKey,
          query: this.store.search,
          language: "it-IT"
        },
      };

      this.getMovies(paramsObj);
      this.getTvShows(paramsObj);
    },

    getMovies(paramsObj) {
      axios.get(`https://api.themoviedb.org/3/search/movie`, paramsObj)
        .then(response => {
          console.log(response)
          this.store.movies = response.data.results;
        });
    },

    getTvShows(paramsObj) {
      axios.get(`https://api.themoviedb.org/3/search/tv`, paramsObj)
        .then(response => {
          console.log(response)
          this.store.tvshows = response.data.results;
        });
    },
  }
}
</script>

<template>
  <AppHeader @doResearch="doResearch" />
  <AppMain />
</template>

<style lang="scss">
@use './styles/general.scss'
</style>
