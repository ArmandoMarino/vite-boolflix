<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            term: ''
        }
    },
    props: {
        // movies: Array,
        placeholder: String
    },
    methods: {
        onTermChange(selected) {
            this.$emit('term-change', selected);
        }
    },
    emits: ['term-change', 'form-submit']
};

</script>

<template>
    <form @submit.prevent="$emit('form-submit')">
        <input type="text" v-model.trim="term" @keyup="$emit('term-change', term)"
            :placeholder="placeholder || 'Cerca...'">
        <button type="submit">{{ buttonLabel || 'Cerca' }}</button>
    </form>
</template>

<style>

</style>