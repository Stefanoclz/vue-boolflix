<template>
  <div id="app">
    <Header @insertedText="searchedText" />
    <Main :movies="movies" :series="series" />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import axios from "axios";
import Main from "@/components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      searchText: "",
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "9e7093415d92ae4b00347920cb93d49c",
      movies: [],
      series: [],
    };
  },
  methods: {
    searchedText(searchText) {
      this.searchText = searchText;
      this.loadMovieApi();
      this.loadTvApi();
    },
    loadApi(kind) {
      const params = {
        api_key: this.apiKey,
        query: this.searchText,
        language: "it-IT",
      };
      if (this.searchText.length > 0) {
        axios.get(this.apiUrl + kind, { params }).then((response) => {
          if (kind === "movie") {
            this.movies = response.data.results;
            console.log("movie", this.movies);
          } else if (kind === "tv") {
            this.series = response.data.results;
            console.log("serie", this.series);
          }
        });
      }
    },
    loadMovieApi() {
      this.loadApi("movie");
    },
    loadTvApi() {
      this.loadApi("tv");
    },
  },
};
</script>
<style lang="scss">
@import "./assets/data/general";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
