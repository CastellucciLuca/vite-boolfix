<script>
import { store } from '../store.js';
import FilmList from './FilmList.vue';
import PopularFilm from './PopularFilm.vue';
export default {
    name: 'AppMain',
    components: {
        FilmList,
        PopularFilm
    },
    data() {
        return {
            store
        }
    },
}
</script>

<template>
    <main>
        <!-- FILM LIST -->
        <FilmList v-if="store.filmList.length > 0 && store.userSearch != ''" />
        <!-- POPULAR FILMS-->
        <PopularFilm v-else-if="store.filmList.length == 0 && store.userSearch == ''" />
        <!--IF FILM NOT FOUND-->
        <span v-else-if="store.filmList.length == 0 && store.userSearch != ''">Nessun Film trovato</span>
    </main>
</template>

<style lang="scss" scoped>
span {
    color: white;
}
</style>