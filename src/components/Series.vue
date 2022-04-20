<template>
  <div class="card">
    <div><strong>Titolo: </strong>{{ item.name }}</div>
    <div><strong>Titolo originale: </strong>{{ item.original_name }}</div>
    <div><strong>Lingua: </strong>{{ item.original_language }}</div>
    <div><strong>Voto: </strong>{{ item.vote_average }}</div>
    <div><strong>Overview: </strong>{{ item.overview }}</div>
  </div>
</template>

<script>
export default {
  name: "seriesList",
  props: {
    item: Object,
  },
};
</script>

<style scoped lang="scss">
.card {
  width: calc(100% / 3) - 5%;
  max-height: 500px;
  background-color: black;
  color: white;
  margin: 30px 0px;
  padding: 40px 20px;
  text-align: left;
  border: 1px solid white;
}
</style>