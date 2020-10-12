<template src='./templates/App.html'></template>

<script>
import { GiphyFetch } from "@giphy/js-fetch-api";
import GifGrid from "./components/GifGrid.vue";
import Navbar from "./components/Navbar.vue";
import BannerCTA from "./components/BannerCTA.vue";
import Footer from "./components/Footer.vue";

const gf = new GiphyFetch(`${process.env.VUE_APP_GIPHY_API_KEY}`);

export default {
  name: "App",
  components: { GifGrid, Navbar, BannerCTA, Footer },

  data: function () {
    return {
      trendingGifs: [],
      searchedGifs: [],
      reactionsGifs: [],
      emojis: [],
      query: "",
    };
  },
  methods: {
    async fetchTrending() {
      try {
        const result = await gf.trending({ limit: 8 });
        this.trendingGifs = result.data;
      } catch (error) {
        console.error(`trending`, error);
      }
    },
    async fetchReactions() {
      try {
        const result = await gf.gifs("reactions");
        result.data.forEach((gif, index) => {
          if (index > 7) return;
          this.reactionsGifs.push(gif);
        });
      } catch (error) {
        console.error(`reactions`, error);
      }
    },
    async fetchEmojis() {
      try {
        const result = await gf.emoji({ limit: 8 });
        result.data.forEach((emoji, index) => {
          if (index > 7) return;
          this.emojis.push(emoji);
        });
      } catch (error) {
        console.error(`emojis`, error);
      }
    },
    async searchGifs() {
      this.searchedGifs = [];
      try {
        const result = await gf.search(`"${this.query}"`, {
          sort: "relevant",
          lang: "es",
          limit: 8,
          type: "stickers",
        });
        result.data.forEach((gif, index) => {
          if (index > 7) return;
          this.searchedGifs.push(gif);
        });
      } catch (error) {
        console.error(`search`, error);
      }
    },
  },

  created: function () {
    this.fetchTrending();
    this.fetchReactions();
    this.fetchEmojis();
  },
};
</script>

<style>
#app {
  background-color: whitesmoke;
}
.search {
  margin-bottom: 3em;
}
</style>
