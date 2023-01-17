<script>
import { store } from '../store.js';
import axios from 'axios';
import SingleFilm from './SingleFilm.vue';
export default {
    name: 'PopularFilm',
    components: {
        SingleFilm
    },
    data() {
        return {
            store,
            apiPopularFilm: 'https://api.themoviedb.org/3/movie/popular',
            apiKey: 'afbf158776bc993869bf790f7b9b71de',
            languageApi: 'it-IT'
        }
    },
    methods: {
        //TO GENERATE POPULAR FILM
        getPopularFilm() {
            axios.get(this.apiPopularFilm, {
                params: {
                    api_key: this.apiKey,
                    language: this.languageApi,
                }
            })
                .then(function (response) {
                    console.log(response.data.results);
                    store.popularMovie = response.data.results;
                })
                .catch(function (error) {
                    console.log(error);
                })
        }
    },
    created() {
        this.getPopularFilm()
    },
}
</script>
<template>
    <section id="popular-film">
        <h2>Film Popolari</h2>
        <div class="container-fluid">
            <div class="row">
                <article class="col-3 d-flex justify-content-center my-5" v-for="singleMovie in store.popularMovie">
                    <SingleFilm :singleFilm="singleMovie" />
                </article>
            </div>
        </div>
    </section>
</template>
<style lang="scss">
section#popular-film {
    padding: 2rem;
    h2 {
        font-size: 3rem;
        color: white;
    }
}
</style>