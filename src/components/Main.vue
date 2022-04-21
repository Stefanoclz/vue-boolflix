<template>
  <main>
    <h2 v-show="movies.length > 0">Films</h2>
    <div class="container">
      <Films
        v-for="movie in movies"
        :key="movie.id"
        :item="movie"
        :link="imageLink"
        :voto="voto"
        :star="star"
        :class="starCalculator(movie)"
      />
    </div>
    <h2 v-show="series.length > 0">Series</h2>
    <div class="container">
      <Series
        v-for="serie in series"
        :key="serie.id"
        :item="serie"
        :link="imageLink"
        :voto="voto"
        :star="star"
        :class="starCalculator(serie)"
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
      star: "",
    };
  },
  props: {
    movies: Array,
    series: Array,
  },
  methods: {
    starCalculator(object) {
      /* console.log(
        "voto",
        object.name,
        object.title,
        object.vote_average,
        "=>",
        Math.round(object.vote_average / 2)
      );*/
      this.voto = Math.round(object.vote_average / 2);
      if (this.voto === 1) {
        return (this.star = '<i class="fa-solid fa-star"></i>');
      } else if (this.voto === 2) {
        return (this.star = '<i class="fa-solid fa-star"></i>');
      } else if (this.voto === 3) {
        return (this.star = '<i class="fa-solid fa-star"></i>');
      } else if (this.voto === 4) {
        return (this.star = '<i class="fa-solid fa-star"></i>');
      } else if (this.voto === 5) {
        return (this.star = '<i class="fa-solid fa-star"></i>');
      } else {
        return "ND";
      }
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