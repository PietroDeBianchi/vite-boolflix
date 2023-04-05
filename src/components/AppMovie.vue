<template>
    <li>
        {{ movie.title }}
        {{ movie.original_title }}
        {{ movie.original_language }}
        {{ movie.vote_average }}
    </li>
</template>

<script>
export default {
    name: "AppMovie",
    props: {
        movie: Object
    }
}
</script>

<style lang="scss" scoped></style>