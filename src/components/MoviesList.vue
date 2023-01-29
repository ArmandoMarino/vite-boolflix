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
    },
    methods: {
        voteTrasform() {
            let star = store[movie.vote_average]
            console.log(star)
            return
        }
    }
};
</script>

<template>
    <section id="productions">
        <div id="movies">
            <h1>Movies</h1>
            <div v-if="store.isLoading" class="text-center">Loading...</div>
            <div v-else class="row m-3 row-cols-2 row-cols-lg-5 g-2 g-lg-3">
                <movie-card v-for="movie in store.movies" :key="movie.id" :id="movie.id" :title="movie.title"
                    :originalTitle="movie.original_title"
                    :image="`https://image.tmdb.org/t/p/original/${movie.poster_path}`"
                    :language="movie.original_language" :vote="Math.floor(movie.vote_average)">
                </movie-card>
            </div>
        </div>


        <div id="series">
            <h1>TV Series</h1>
            <div v-if="store.isLoading" class="text-center">Loading...</div>
            <div v-else class="row m-3 row-cols-2 row-cols-lg-5 g-2 g-lg-3">
                <movie-card v-for="serie in store.series" :key="serie.id" :id="serie.id" :title="serie.name"
                    :image="`https://image.tmdb.org/t/p/original/${serie.poster_path}`"></movie-card>
            </div>
        </div>

    </section>


</template>

<style lang="scss" scoped>
#productions {
    border-radius: 20px;

    h1 {
        font-family: 'Bebas Neue', cursive;
        letter-spacing: 2px;
        margin-left: 1.5rem;
        margin-top: 1.5rem;
        color: white;
    }
}
</style>