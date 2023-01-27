<script>
export default {
    name: 'MovieCard',
    props: {
        id: Number,
        title: String,
        image: String,
        flagImage: String
    },
};
</script>

<template>
    <div class="col movie-card text-center">
        <div class=" interior-card p-3">
            <img class="img-fluid mb-3" :src="image" :alt="title">
            <!-- <p>#{{ number }}</p>
            <p><strong>{{ name }} </strong> </p>
            <p>{{ type }}</p> -->
        </div>

    </div>
</template>

<style lang="scss" scoped>
.movie-card {
    .interior-card {
        background-color: white;
        border-radius: 20px;

        p {
            font-style: italic;
        }

        img {
            width: 200px;
            height: 200px;
        }
    }
}
</style>