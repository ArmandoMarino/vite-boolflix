
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
    emits: ['term-change']

}
</script>

<template>
    <header>
        <h1>BOOLFLIX</h1>
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