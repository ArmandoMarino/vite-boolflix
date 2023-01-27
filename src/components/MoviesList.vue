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
    <section id="productions">
        <div id="movies">
            <h1>Movies</h1>
            <div v-if="store.isLoading" class="text-center">Loading...</div>
            <div v-else class="row m-3 row-cols-2 row-cols-lg-5 g-2 g-lg-3">
                <movie-card v-for="movie in store.movies" :key="movie.id" :number="movie.number" :name="movie.name"
                    :image="`https://image.tmdb.org/t/p/original/${movie.poster_path}`"
                    :type="movie.type1"></movie-card>
            </div>
        </div>


        <div id="series">
            <h1>TV Series</h1>
            <div v-if="store.isLoading" class="text-center">Loading...</div>
            <div v-else class="row m-3 row-cols-2 row-cols-lg-5 g-2 g-lg-3">
                <movie-card v-for="serie in store.series" :key="serie.id" :number="serie.number" :name="serie.name"
                    :image="`https://image.tmdb.org/t/p/original/${serie.poster_path}`"></movie-card>
            </div>
        </div>

    </section>


</template>

<style lang="scss" scoped>
#productions {
    border-radius: 20px;
}
</style>