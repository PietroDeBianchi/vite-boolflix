<template>
    <header>
        <div>
            <h1>BoolFlix</h1>
        </div>
        <div class="my-inputs">
            <input type="text" @keyup.enter="$emit('doResearch')" v-model="store.search" placeholder=" Search Movies...">
            <button @click="$emit('doResearch')">Search</button>
        </div>
    </header>
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


<style lang="scss" scoped>
@use "../styles/partials/mixins";

header {
    z-index: 999;
    position: fixed;
    width: 100%;
    height: 80px;
    padding: 0 40px;
    @include mixins.d-flex-between;
    background-color: black;

    h1 {
        color: red;
        font-size: 40px
    }

    .my-inputs {
        @include mixins.d-flex-between;
        gap: 12px;
    }

    input {
        width: 210px;
        height: 36px;
        padding: 0 16px;
        background: transparent;
        border-radius: 4px;
        border: 1px solid #fe4567;
        color: #f9f9f9;
    }

    button {
        padding: 8px 20px;
        border-radius: 10px;
        border: 0;
        background-color: rgb(255, 56, 86);
        letter-spacing: 1.5px;
        font-size: 15px;
        transition: all .3s ease;
        box-shadow: rgb(201, 46, 70) 0px 2px 0px 0px;
        color: hsl(0, 0%, 100%);

        &:active {
            background-color: rgb(255, 56, 86);
            box-shadow: rgb(201, 46, 70) 0px 0px 0px 0px;
            transform: translateY(2px);
            transition: 200ms;
        }
    }
}
</style>