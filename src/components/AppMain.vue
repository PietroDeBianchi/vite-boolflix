<template>
    <main>
        <section v-if="store.movies.length > 0">
            <h3>Film</h3>
            <ul>
                <AppMovie v-for="movie in store.movies" :key="movie.id" :item="movie" />
            </ul>
        </section>
        <section v-if="store.tvshows.length > 0">
            <h3>Series</h3>
            <ul>
                <AppMovie v-for="show in store.tvshows" :key="show.id" :item="show" />
            </ul>
        </section>

        <section v-if="store.tvshows.length == 0 && store.movies.length == 0">
            <h3>No Results...</h3>
        </section>
    </main>
</template>

<script>
import { store } from '../store.js';
import AppMovie from './AppMovie.vue'

export default {
    name: "AppMain",
    data() {
        return {
            store
        }
    },
    components: {
        AppMovie
    }
}
</script>

<style lang="scss" scoped>
@use "../styles/partials/mixins";

main {
    min-height: 100vh;
    padding: 0 40px;
    background-color: #1B1B1B;
    padding-top: 100px; //80px = header heigth
    color: white;

    h3 {
        font-size: 2rem;
    }
}

section {
    min-height: 20vh;
    margin-top: 20px;
    padding-bottom: 20px;

    ul {
        @include mixins.d-flex-between;
        gap: 12px;
        overflow-x: scroll;
    }
}
</style>