<script>
import MoviesList from './MoviesList.vue';
export default {
    name: 'AppMain',
    components: {
        MoviesList
    },
}
</script>

<template>
    <main>
        <movies-list></movies-list>
    </main>
</template>

<style lang="scss" scoped>
main {
    height: 100vh;
    background-color: #555555;
}
</style>