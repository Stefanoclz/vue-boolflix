<template>
  <div id="app">
    <Header @insertedText="searchedText" />
    <div class="container">
      <Main v-for="movie in movies" :key="movie.id" :item="movie" />
    </div>
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
    };
  },
  methods: {
    searchedText(searchText) {
      this.searchText = searchText;
      console.log(this.searchText);
      this.loadApi();
    },
    loadApi() {
      const params = {
        api_key: this.apiKey,
        query: this.searchText,
        language: "it-IT",
      };
      if (this.searchText.length > 0) {
        axios.get(this.apiUrl + "movie", { params }).then((response) => {
          this.movies = response.data.results;
          console.log(this.movies);
        });
      }
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

.container {
  display: flex;
  flex-wrap: wrap;
  column-gap: 5%;
  width: 80%;
  margin: 0px auto;
}
</style>
