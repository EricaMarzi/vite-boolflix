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
<!--185x260-->
<template>
    <div class="col">
        <figure>
            <img :src="posterUrl" :alt="title" v-if="production.poster_path">
            <div class="no-img" v-else><i class="fa-solid fa-film fa-2xl"></i></div>

            <ul class="text-white">
                <li>
                    <h6>{{ title }}</h6>
                </li>
                <li>{{ originalTitle }}</li>
                <li>
                    <img class="lang" v-if="hasFlag" :src="flagUrl" :alt="lang">
                    <span v-else>{{ lang }}</span>
                </li>
                <li v-html="getVote"></li>
            </ul>
        </figure>
    </div>
</template>

<style lang="scss" scoped>
.no-img {
    height: 277px;
    width: 185px;
    background-color: gray;
    color: rgb(99, 99, 99);

    display: flex;
    justify-content: center;
    align-items: center;
}

figure {
    position: relative;
    width: 185px;
}

figure:hover img,
figure:hover .no-img {
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

ul {
    display: none;
    position: absolute;
    top: 50%;
    left: 40%;
    transform: translate(-50%, -50%);

    flex-direction: column;
    justify-content: center;
    align-items: center;
}

figure:hover ul {
    display: flex;
}

li {
    width: 160px;
}

.lang {
    height: 20px;
}
</style>