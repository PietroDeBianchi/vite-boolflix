<template>
    <li>
        <h3>{{ getName() }}</h3>
        <h4>{{ getTitle() }}</h4>
        <img :src="getImageUrl(`../assets/flags/${item.original_language}.png`)"
            v-if="myFlags.includes(item.original_language)" class="flag-leng" />
        <span v-else> {{ item.original_language }}</span>
        <span>{{ item.vote_average }}</span>
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
            myFlags: ['en', 'it']
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
        }

    }
}
</script>

<style lang="scss" scoped>
.flag-leng {
    width: 20px;
}
</style>