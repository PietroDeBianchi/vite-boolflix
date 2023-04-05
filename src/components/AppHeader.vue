<template>
    <input type="text" @keyup.enter="$emit('doResearch')" v-model="store.search" placeholder=" Search Movies...">
    <button @click="$emit('doResearch')">Search</button>
</template>


<script>
import { store } from '../store.js'

export default {
    name: 'AppHeader',
    emits: ['doResearch'],
    data() {
        return {
            store
        }
    }
}
</script>


<style lang="scss" scoped></style>