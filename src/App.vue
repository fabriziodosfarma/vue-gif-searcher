<template>
  <div class="app">
    <Navbar></Navbar>
    <section>
      <div class="hero-body">
        <div class="container">
          <h1 class="container__title-1">GIF Searcher</h1>
          <h2 class="container__subtitle">Find the best GIFs</h2>
        </div>
      </div>
    </section>
    <input type="text" class='search' name="query" placeholder="Search the best GIFs" v-model="query" @keyup="searchGifs">
    <GifGrid :gifs='searchedGifs'></GifGrid>
    <h2 class="title is-2">Trending</h2>
    <GifGrid :gifs='trendingGifs'></GifGrid>
  </div>
</template>

<script>
import GifGrid from './components/GifGrid.vue'
import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {GifGrid,Navbar},
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
    fechTrendingGifs: function() {
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
    this.fechTrendingGifs()
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
