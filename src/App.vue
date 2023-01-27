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
    /*   fetchTopRated() {
        store.isLoading = true;
        let url = this.uriToprated;
        // if (this.term) url += `?eq[type1]=${this.term}`;
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
      }, */
    fetchMovies() {
      store.isLoading = true;
      let url = `${this.baseUri}/search/movie?api_key=${this.apiKey}&query=${this.term}`
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
    onSearchedMovie(selected) {
      this.term = selected;
      this.fetchMovies()
    }
  },
  /*  created() {
     this.fetchTopRated();
   } */
}
</script>

<template>
  <app-header @term-change="onSearchedMovie"></app-header>
  <app-main></app-main>
</template>


<style>

</style>