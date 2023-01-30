<script>
import axios from 'axios';
import { store } from './data/store';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store,
      baseUri: 'https://api.themoviedb.org/3',
      apiKey: 'e310165f0fd59ba5b0959d17155e6c84',
    }
  },
  methods: {
    onSearchedMovie(selected) {
      if (selected) {
        this.fetchApi('search/movie', 'movies', selected),
          this.fetchApi('search/tv', 'series', selected)

      } else {
        this.fetchTopRated();
      }
    },

    // NUTRO API call endpoint and collection
    fetchApi(endpoint, collection, query) {
      store.isLoading = true;
      let url = `${this.baseUri}/${endpoint}?api_key=${this.apiKey}`
      if (query) url += `&query=${query}`
      axios.get(url)
        .then(res => {
          console.log(res);
          store[collection] = res.data.results;
        }).catch(error => {
          console.error(error);
          store[collection] = [];
        }).then(() => {
          store.isLoading = false;
        })
    },
    fetchTopRated() {
      this.fetchApi('tv/top_rated', 'series');
      this.fetchApi('movie/top_rated', 'movies');
    }



  },

  // TODO C'e' qualcosa che non va quando term va a
  created() {
    this.fetchTopRated();
  }
}
</script>

<template>
  <app-header @term-change="onSearchedMovie"></app-header>
  <app-main></app-main>
</template>


<style>

</style>