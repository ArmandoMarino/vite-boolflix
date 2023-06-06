
<script>
import SearchBar from './SearchBar.vue';
export default {
    name: 'AppHeader',
    components: {
        SearchBar
    },
    methods: {
        onTermChange(term) {
            this.$emit('term-change', term);
        }
    },
    emits: ['term-change', 'form-submit']

}
</script>

<template>
    <header>
        <h1><a style="text-decoration: none; color: red;" href="">BOOLFLIX</a></h1>
        <search-bar @term-change="onTermChange"></search-bar>
    </header>
</template>

<style lang="scss" scoped>
header {
    padding: 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 150px;
    background-color: black;

    h1 {
        color: red;
        font-size: 60px;
        font-family: 'Bebas Neue', cursive;
    }
}
</style>