
<script>
import SearchBar from './SearchBar.vue';
export default {
    name: 'AppHeader',
    components: {
        SearchBar
    }
}
</script>

<template>
    <header>
        <search-bar></search-bar>
    </header>
</template>

<style lang="scss" scoped>
header {
    height: 200px;
    background-color: black;
}
</style>