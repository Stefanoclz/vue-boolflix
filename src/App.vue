<template>
  <div id="app">
    <Header @insertedText="searchedText" />
    <Main :movies="movies" :series="series" :allCast="castMembers" />
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
      apiUrlCast: "https://api.themoviedb.org/3/movie/",
      movies: [],
      series: [],
      filmId: [],
      castMembers: [],
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
            this.searchMovieID();
            this.loadMovieCast();
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
    loadMovieCast() {
      this.loadCast("movie");
    },
    searchMovieID() {
      if (this.movies.length > 0) {
        for (let i = 0; i < this.movies.length; i++) {
          let id = this.movies[i].id;
          this.filmId.push(id);
        }
      }
      console.log("idList", this.filmId);
    },
    loadCast(kind) {
      const params = {
        api_key: this.apiKey,
        language: "it-IT",
      };
      for (let i = 0; i < this.filmId.length; i++) {
        axios
          .get(
            `https://api.themoviedb.org/3/${kind}/${this.filmId[i]}/credits`,
            {
              params,
            }
          )
          .then((response) => {
            //let test = response.data.cast;
            // console.log("TEST CAST", test);
            this.castMembers.push(response.data.cast);
          });
      }
      console.log("basta", this.castMembers);
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
