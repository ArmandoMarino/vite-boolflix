
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
        <search-bar @term-change="onTermChange"></search-bar>
    </header>
</template>

<style lang="scss" scoped>
header {
    height: 200px;
    background-color: black;
}
</style>