<script>
export default {
    name: 'MovieCard',
    props: {
        id: Number,
        title: String,
        originalTitle: String,
        language: String,
        average_vote: Number,
        image: String,
        flagImage: String
    },
    computed: {
        hasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.language)
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.language}.png`, import.meta.url);
            return url.href;
        },
        vote() {
            return Math.ceil(this.average_vote / 2)
        }
    },
};
</script>

<template>
    <div class="col movie-card text-center bounce my-4">
        <div class=" interior-card">
            <img class="img-fluid img-production" :src="image" :alt="title">
            <!-- OVERLAY ON CARD -->
            <div class="card__overlay">
                <div class="overlay__text">
                    <h3>{{ title }}</h3>
                    <p class="p-2">{{ originalTitle }}</p>
                    <div class="wrapper-flag p-1">
                        <img class="img-fluid p-2" v-if="hasFlag" :src="flagSrc" :alt="originalTitle">
                        <p class="p-2" v-else>{{ language }}</p>
                    </div>
                    <!-- <p>{{ vote }}</p> -->

                    <i v-for="i in 5" :class="i <= vote ? 'fa-solid' : 'fa-regular'" class="fa-star"></i>

                </div>
            </div>
        </div>

    </div>
</template>

<style lang="scss" scoped>
// ANIMAZIONE BOUNCE
@keyframes bounce {
    0% {
        transform: translateY(-20px);
    }

    50% {
        transform: translateY(-20px);
    }

    100% {
        transform: translateY(-20px);
    }
}

// MOVIE CARD
.movie-card {
    cursor: pointer;
    animation-duration: 100s;
    height: 200px;


    .interior-card {
        background-color: white;
        position: relative;
        transition: all .5s ease-in;

        .img-production {
            width: 100%;
            height: 200px;
            object-fit: cover;
            object-position: top;
        }

        p {
            font-style: italic;
        }

        .card__overlay {
            position: absolute;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
            height: 200px;
            width: 100%;
            opacity: 0;
            transition: .5s ease;
            background-color: #393839;

            .overlay__text {
                color: white;
                font-size: 15px;
                position: absolute;
                top: 50%;
                left: 50%;
                -webkit-transform: translate(-50%, -50%);
                -ms-transform: translate(-50%, -50%);
                transform: translate(-50%, -50%);
                text-align: center;
                width: 100%;

                h3 {
                    font-size: 15px;
                    margin: 0;
                }

                p {
                    margin: 0;
                }

                .wrapper-flag {
                    img {
                        width: 50px;
                    }
                }

                ul {
                    list-style-type: none;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    margin: 0;
                    padding: 0;
                }
            }


        }

        .card__overlay:hover {
            opacity: 0.9;
        }
    }
}

.bounce:hover {
    animation-name: bounce;
    animation-timing-function: ease;
}
</style>