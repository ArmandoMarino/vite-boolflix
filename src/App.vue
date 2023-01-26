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
    }
  }
}
</script>

<template>
  <app-header></app-header>
  <app-main></app-main>
</template>


<style>

</style>