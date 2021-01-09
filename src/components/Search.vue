<template>
    <div class="field" id="search">
        <label class="label">Buscar título de filmes:</label>
        <div class="control">
            <input class="input" v-model="text" v-on:keyup.enter="search" type="text" required autofocus>
            <input class="button is-primary" type="submit" v-on:click="search" value="Buscar">
        </div>
        
        <Movies :movies="movies" :show="show"/>
        
    </div>
</template>
<script>

import axios from 'axios'
import {baseApiUrl, ApiKey} from '@/global'
import Movies from './Movies'

export default {
    name: 'Search',
    data: function () {
        return {
            text: '',
            movies: [],
            show: false
        }
    },
    components: {
        Movies
    },
    methods: {
        search: function () {
            axios.get(`${baseApiUrl}${ApiKey}&s=${this.text}`).then(res => {
                this.movies = res.data.Search
                this.show = true
                this.text = ''
            })
        }
    }
}
</script>
<style scoped>

</style>