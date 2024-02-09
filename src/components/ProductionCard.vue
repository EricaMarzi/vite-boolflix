<script>
export default {
    name: 'ProcutionCard',
    props: {
        production: Object
    },
    computed: {
        title() {
            return this.production.title || this.production.name
        },
        originalTitle() {
            return this.production.original_title || this.production.original_name
        },
        lang() {
            return this.production.original_language
        },
        vote() {
            return this.production.vote_average
        },
        hasFlag() {
            const flags = ['en', 'it'];
            return flags.includes(this.lang)
        },
        flagUrl() {
            const url = new URL(`../assets/img/${this.lang}.png`, import.meta.url);
            return url.href;
        },
        posterUrl() {
            return `https://image.tmdb.org/t/p/w185${this.production.poster_path}`;

        },
        getVote() {
            let transformVote = Math.round((this.vote / 10) * 5)
            const fullStar = '<i class="fa-solid fa-star"></i>'
            const emptyStar = '<i class="fa-regular fa-star"></i>'
            return `Voto: ${fullStar.repeat(transformVote)}${emptyStar.repeat(5 - transformVote)}`

        }
    }
}
</script>
<template>
    <div class="poster-container">

        <img class="poster" :src="posterUrl" :alt="title" v-if="production.poster_path">
        <div class="no-img" v-else><i class="fa-solid fa-film fa-2xl"></i></div>


        <section class="product-info">
            <h5>{{ title }}</h5>
            <h6>{{ originalTitle }}</h6>
            <div>
                <span>Lingua: </span>
                <img class="lang" v-if="hasFlag" :src="flagUrl" :alt="lang">
                <span v-else>{{ lang }}</span>
            </div>
            <div v-html="getVote"></div>
        </section>

    </div>
</template>

<style lang="scss" scoped>
.poster-container {
    position: relative;
    width: 185px;
}

.no-img {
    height: 277px;
    width: 185px;
    background-color: gray;
    color: rgb(99, 99, 99);

    display: flex;
    justify-content: center;
    align-items: center;
}


.poster-container:hover .poster,
.poster-container:hover .no-img {
    opacity: 0.3;
}


img::before {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    background-color: rgba($color: #000000, $alpha: 0.5);
}

.product-info {
    color: white;

    display: none;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    flex-direction: column;


    width: 160px;
    padding-left: 5px;
}

.poster-container:hover .product-info {
    display: flex;
}



img.lang {
    height: 20px;
}
</style>