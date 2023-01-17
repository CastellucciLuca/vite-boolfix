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
    <div class="container-fluid">
        <div class="row">
            <article class="col-3 d-flex justify-content-center my-5" v-for="singleMovie in store.filmList">
                <SingleFilm :singleFilm="singleMovie" />
            </article>
        </div>
    </div>
</template>
<style lang="scss" scoped>
</style>