<template>
  <div id="app">
    <Header msg="Welcome to TV-maze" @searchTvShows="searchTvShows($event)"></Header>
    <Cards :tvShows="TvShows"></Cards>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Cards from './components/Cards.vue'

export default {
  name: 'app',
  components: {
    Header,
    Cards
  },
    data() {
        return {
            search: "",
            TvShows: []
        }
    },
    methods: {
        searchTvShows: function(search){
            fetch(`http://api.tvmaze.com/search/shows?q=:${search}`)
            .then(response => response.json())
            .then(response => {
                this.TvShows = []
                this.TvShows.push(...response)
                this.search = search
                console.log(this.TvShows, search, this.search)
            })
        }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
