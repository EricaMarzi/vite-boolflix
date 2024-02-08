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
            return `https://image.tmdb.org/t/p/w342${this.production.poster_path}`;

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
    <ul>
        <li>{{ title }}</li>
        <li>{{ originalTitle }}</li>
        <li>
            <img v-if="hasFlag" :src="flagUrl" :alt="lang">
            <span v-else>{{ lang }}</span>
        </li>
        <li v-html="getVote"></li>
        <li>
            <img :src="posterUrl" alt="">
        </li>
    </ul>
</template>

<style lang="scss" scoped></style>