<script>
import { store } from '../data/store';
import MovieCard from './MovieCard.vue';
export default {
    name: 'MoviesList',
    components: {
        MovieCard
    },
    data() {
        return { store }
    }
};
</script>

<template>
    <section id="movies">
        <div v-if="store.isLoading" class="text-center">Loading...</div>
        <div v-else class="row m-3 row-cols-2 row-cols-lg-5 g-2 g-lg-3">
            <movie-card v-for="pokemon in store.movies" :key="pokemon.id" :number="pokemon.number" :name="pokemon.name"
                :image="pokemon.imageUrl" :type="pokemon.type1"></movie-card>
        </div>
    </section>


</template>

<style lang="scss" scoped>
#movies {
    border-radius: 20px;
}
</style>