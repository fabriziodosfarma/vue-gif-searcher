<template src='./templates/App.html'></template>

<script>
import GifGrid from './components/GifGrid.vue'
import Navbar from './components/Navbar.vue'
import BannerCTA from './components/BannerCTA.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {GifGrid,Navbar,BannerCTA,Footer},
  data: function() {
    return {
      trendingGifs: null,
      searchedGifs: null,
      baseURL: 'https://api.giphy.com/v1/gifs/',
      apiKey: 'zjabJCYz2uiqqJjvzeSLXSbg6E49Dr5u',
      query: ''
    }
  },
  methods: {
    fetchTrendingGifs: function() {
      const url = `${this.baseURL}trending?api_key=${this.apiKey}&limit=8`;
        fetch(url)
          .then(response => response.json())
          .then(data => this.trendingGifs = data.data)
    },
    searchGifs: function() {
      const url = `${this.baseURL}search?api_key=${this.apiKey}&q=${this.query}&limit=8`
      fetch(url)
        .then(response => response.json())
        .then(data => this.searchedGifs = data.data)
    }
  },
  created: function() {
    this.fetchTrendingGifs()
  }
} 
</script>

<style>
#app {
  background-color: whitesmoke;
}
.search {
  margin-bottom: 3em;
}
</style>
