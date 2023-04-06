<template>
    <li class="card-container" @click="flipCard">
        <div class="card front-card" :class="{ 'hidden': isFlipped }">
            <img v-if="item.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`">
            <img v-else src="https://cdn.onlinewebfonts.com/svg/img_89726.png" alt="sob" class="poster_none">
        </div>
        <div class="card back-card" :class="{ 'hidden': !isFlipped }">
            <div class="back-container">
                <h3>Title: {{ getTitle() }}</h3>
                <div>
                    Language:
                    <img :src="getImageUrl(`../assets/flags/${item.original_language}.png`)"
                        v-if="myFlags.includes(item.original_language)" class="flag-leng" />
                    <span v-else> {{ item.original_language }}</span>
                </div>
                <div>
                    Rating:
                    <i v-for="i in 5" class=" fa-star" :key="i" :class="(i <= getRating() ? 'fa-solid' : 'fa-regular')"></i>
                </div>
                <p>{{ item.overview }}</p>
            </div>
        </div>
        <div class="main-title">
            <h3>{{ getName() }}</h3>
        </div>
    </li>
</template>

<script>

export default {
    name: "AppMovie",
    props: {
        item: Object,
    },
    data() {
        return {
            myFlags: ['en', 'it'],
            isFlipped: false
        }
    },
    methods: {
        getImageUrl(path) {
            return new URL(path, import.meta.url).href
        },
        getTitle() {
            if (this.item.original_title) {
                return this.item.original_title;
            } else {
                return this.item.original_name;
            }
        },
        getName() {
            if (this.item.title) {
                return this.item.title;
            } else {
                return this.item.name;
            }
        },
        getRating() {
            return Math.ceil(this.item.vote_average / 2);
        },
        flipCard() {
            this.isFlipped = !this.isFlipped
        }

    }
}
</script>

<style lang="scss" scoped>
li {
    align-self: stretch;

    span {
        margin: 0 4px;
    }

    .main-title {
        margin-top: 6px;
        text-align: center;
    }

    .flag-leng {
        width: 20px;
    }

    .poster_none {
        width: 342px;
        height: 513px;
        background-color: white;
    }
}

.card-container {
    position: relative;
    width: 350px;
    height: 520px;

    .card {
        width: 342px;
        height: 520px;

    }

    .back-card {
        border: 1px solid white;
    }

    .hidden {
        display: none;
    }
}

.back-container {
    width: 90%;
    height: 100%;
    margin: auto;
    padding: 6px 0;
    display: flex;
    flex-direction: column;
    gap: 12px;

    p {
        font-size: 14px;
    }
}
</style>