<template>
  <main>
    <h2 v-show="movies.length > 0">Films</h2>
    <div class="container">
      <Films v-for="movie in movies" :key="movie.id" :item="movie" />
    </div>
    <h2 v-show="series.length > 0">Series</h2>
    <div class="container">
      <Series v-for="serie in series" :key="serie.id" :item="serie" />
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
  props: {
    movies: Array,
    series: Array,
  },
};
</script>

<style scoped lang="scss">
.container {
  display: flex;
  flex-wrap: wrap;
  column-gap: 5%;
  width: 80%;
  margin: 0px auto;
}

h2 {
  color: white;
  margin: 20px 0px;
}
</style>