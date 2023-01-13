<script>
import { store } from '../store.js';
import SingleFilm from './SingleFilm.vue';
export default {
    name: 'FilmList',
    components: { SingleFilm },
    data() {
        return {
            store
        };
    },
}
</script>

<template>
    <ul>
        <li v-for="singleMovie in store.filmList">
            <!--SINGLE FILM-->
            <SingleFilm :singleFilm="singleMovie" />
        </li>
    </ul>
</template>

<style lang="scss" scoped>
</style>