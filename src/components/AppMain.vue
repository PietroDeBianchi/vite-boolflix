<template>
    <main>
        <section>
            <h3>Film</h3>
            <ul>
                <AppMovie v-for="(movie, index) in store.movies" :key="index" :movie="movie" />
            </ul>
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
main {
    height: 100vh;
    padding: 0 40px;
    background-color: #1B1B1B;
    padding-top: 120px; //100px = header heigth

    h3 {
        color: white;
        font-size: 2rem;
    }
}
</style>