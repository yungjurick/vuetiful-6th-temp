<template>
    <div class="bar-container">
        <router-link to="/about">ABOUT</router-link>
        <router-link to="/">ARCHIVE</router-link>
        <router-link class="border" to="#">REGISTER</router-link>
    </div>
</template>

<script lang="ts">
import { Vue } from 'vue-property-decorator';
export default class NavBar extends Vue {
}
</script>

<style lang="scss" scoped>
    .bar-container {
        position: absolute;
        width: 71.1vw;
        margin: 2.4vh auto 0 auto;
        top: 0;
        left: 0;
        right: 0;
        display: flex;
        justify-content: flex-end;
        a {
            text-decoration: none;
            color: white;
            padding: 1.4vh 1.6vw 1.6vh 1.6vw;
            letter-spacing: 1.5px;
            font-weight: bold;
            font-size: 13px;
            font-family: 'Montserrat', sans-serif;
            transition: 0.25s;
        }
        a + a {
            margin-left: 1vw;
        }
        .border {
            background: #41b883;
        }
    }
</style>

