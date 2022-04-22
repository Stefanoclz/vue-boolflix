<template>
  <main>
    <h2 v-show="movies.length > 0">Films</h2>
    <div class="container">
      <Films
        v-for="movie in movies"
        :key="movie.id"
        :item="movie"
        :link="imageLink"
      />
    </div>
    <h2 v-show="series.length > 0">Series</h2>
    <div class="container">
      <Series
        v-for="serie in series"
        :key="serie.id"
        :item="serie"
        :link="imageLink"
      />
    </div>
  </main>
</template>

<script>
import Films from "@/components/Films.vue";
import Series from "@/components/Series.vue";

export default {
  name: "mainComponent",
  components: {
    Films,
    Series,
  },
  data() {
    return {
      imageLink: "https://image.tmdb.org/t/p/w342/",
      voto: "",
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "9e7093415d92ae4b00347920cb93d49c",
      filmId: [],
    };
  },
  props: {
    movies: Array,
    series: Array,
  },
  methods: {
    searchID() {
      if (this.movie.length > 0) {
        for (let i = 0; i < this.movies.length; i++) {
          let id = this.movies[i].id;
          this.filmId = id;
        }
      }
      console.log(this.filmId);
    },
  },
};
</script>

<style scoped lang="scss">
.container {
  display: flex;
  flex-wrap: wrap;
  column-gap: 5%;
  width: 85%;
  margin: 0px auto;
  justify-content: center;
}

h2 {
  color: white;
  margin: 20px 0px;
}
</style>