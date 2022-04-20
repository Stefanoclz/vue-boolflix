<template>
  <div id="app">
    <Header @insertedText="searchedText" />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
  },
  data() {
    return {
      searchText: "",
      apiUrl: "https://api.themoviedb.org/3/search/",
      movies: [],
    };
  },
  mounted() {
    this.loadApi();
  },
  methods: {
    searchedText(searchText) {
      this.searchText = searchText;
      console.log(this.searchText);
    },
    loadApi() {
      const params = {
        api_key: "9e7093415d92ae4b00347920cb93d49c",
        query: this.searchText,
        language: "it-IT",
      };
      if (this.searchText.length > 0) {
        axios
          .get(this.apiUrl + "movie", { params })
          .then((response) => {
            console.log(response.data);
          })
          .catch((error) => {
            console.log(error);
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
</style>
