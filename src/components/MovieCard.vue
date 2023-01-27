<script>
export default {
    name: 'MovieCard',
    props: {
        id: Number,
        title: String,
        originalTitle: String,
        language: String,
        vote: String,
        image: String,
        flagImage: String
    },
};
</script>

<template>
    <div class="col movie-card text-center">
        <div class=" interior-card">
            <img class="img-fluid" :src="image" :alt="title">
            <!-- OVERLAY ON CARD -->
            <div class="card__overlay">
                <div class="overlay__text">
                    <h3>{{ title }}</h3>
                    <p>{{ originalTitle }}</p>
                    <p>{{ language }}</p>
                    <p>{{ vote }}</p>
                </div>
            </div>
        </div>

    </div>
</template>

<style lang="scss" scoped>
.movie-card {
    .interior-card {
        background-color: white;
        border-radius: 20px;
        position: relative;
        transition: all .5s ease-in;


        p {
            font-style: italic;
        }

        .card__overlay {
            position: absolute;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
            height: 100%;
            width: 100%;
            opacity: 0;
            transition: .5s ease;
            background-color: #393839;

            .overlay__text {
                color: white;
                font-size: 20px;
                position: absolute;
                top: 50%;
                left: 50%;
                -webkit-transform: translate(-50%, -50%);
                -ms-transform: translate(-50%, -50%);
                transform: translate(-50%, -50%);
                text-align: center;
            }


        }

        .card__overlay:hover {
            opacity: 0.9;
        }
    }




}
</style>