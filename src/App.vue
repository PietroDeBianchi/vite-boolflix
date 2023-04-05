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
  methods: {
    getMovies() {
      axios.get(`https://api.themoviedb.org/3/search/movie`,
        {
          params: {
            api_key: this.store.apiKey,
            query: this.store.search,
            language: "it-IT"
          }
        }
      )
        .then(response => {
          console.log(response)
          this.store.movies = response.data.results;
        });
    }
  }
}
</script>

<template>
  <AppHeader @doResearch="getMovies" />
  <AppMain />
</template>

<style lang="scss">
@use './styles/general.scss'
</style>
