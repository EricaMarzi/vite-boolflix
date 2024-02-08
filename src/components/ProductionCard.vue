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
        hasFlag() {
            const flags = ['en', 'it'];
            return flags.includes(this.production.original_language)
        },
        flagUrl() {
            const url = new URL(`../assets/img/${this.production.original_language}.png`, import.meta.url);
            return url.href;
        }
    }
}
</script>

<template>
    <ul>
        <li>{{ title }}</li>
        <li>{{ originalTitle }}</li>
        <li>
            <img v-if="hasFlag" :src="flagUrl" alt="">
            <span v-else>{{ production.original_language }}</span>
        </li>
        <li>{{ production.vote_average }}</li>
    </ul>
</template>

<style lang="scss" scoped></style>