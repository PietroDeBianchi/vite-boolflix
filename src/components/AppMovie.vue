<template>
    <li>
        {{ movie.title }}
        {{ movie.original_title }}
        <img :src="getImageUrl(`../assets/flags/${movie.original_language}.png`)"
            v-if="myFlags.includes(movie.original_language)" class="flag-leng" />
        <span v-else> {{ movie.original_language }}</span>
        {{ movie.vote_average }}
    </li>
</template>

<script>
export default {
    name: "AppMovie",
    props: {
        movie: Object
    },
    data() {
        return {
            myFlags: ['en', 'it']
        }
    },
    methods: {
        getImageUrl(path) {
            return new URL(path, import.meta.url).href
        }
    }
}
</script>

<style lang="scss" scoped>
.flag-leng {
    width: 20px;
}
</style>