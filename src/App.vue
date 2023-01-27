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
      term: '',
      uriToprated: 'https://api.themoviedb.org/3/movie/top_rated?api_key=e310165f0fd59ba5b0959d17155e6c84&',
      baseUri: 'https://api.themoviedb.org/3',
      apiKey: 'e310165f0fd59ba5b0959d17155e6c84',
    }
  },
  methods: {
    onSearchedMovie(selected) {
      this.term = selected;
      this.fetchApi('search/movie', 'movies'),
        this.fetchApi('search/tv', 'series')
    },
    searchProductions() {
      if (!this.term) {
        store.movies = [];
        store.series = [];
        return;
      }

      this.fetchApi('search/movie', 'movies');
    },
    // NUTRO API call endpoint and collection
    fetchApi(endpoint, collection) {
      store.isLoading = true;
      let url = `${this.baseUri}/${endpoint}?api_key=${this.apiKey}&query=${this.term}`
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

      store.isLoading = true;
      let url = this.uriToprated;
      axios.get(url)
        .then(res => {
          console.log(res);
          store.movies = res.data.results;
        }).catch(error => {
          console.error(error);
          store.movies = [];
        }).then(() => {
          store.isLoading = false;
        })

    },


  },

  // TODO C'e' qualcosa che non va quando term va a null
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