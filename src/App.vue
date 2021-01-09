<template>
  <div class="section">
    <Search/>
    <div class="columns">
      <Movies v-model="movies" />
    </div>
    
  </div>
</template>

<script>
import Search from './components/Search'
import Movies from './components/Movies'

export default {
  name: 'App',
  components: {
    Search,
    Movies
  },
  data() {
    return {
      movies: []
    }
  }
}
</script>

<style>

</style>
