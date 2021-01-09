<template>
    <div class="field" id="search">
        <label class="label">Buscar título de filmes:</label>
        <div class="control">
            <input class="input" v-model="text" v-on:keyup.enter="search" type="text" required autofocus>
            <input class="button is-primary m-2" type="submit" v-on:click="search" value="Buscar">
        </div>
        
        <div class="p-2 m-2" v-if="error != null">
            <div class="notification is-danger">
                <button class="delete" v-on:click="hideAlert"></button>
                    Filme não encontrado!
                </div>
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
            show: false,
            error: null
        }
    },
    components: {
        Movies
    },
    methods: {
        search: function () {
            axios.get(`${baseApiUrl}${ApiKey}&s=${this.text}`).then(res => {
                
                if(res.data.Response == 'False') {
                    this.error = res.data.Error
                    this.text = ''
                    this.movies = []
                } else {
                    this.movies = res.data.Search
                    this.error = null
                    this.show = true
                    this.text = ''
                }
                
            })
        },
        hideAlert: function () {
            this.error = null
        }
    }
}
</script>
<style scoped>

</style>