<template>
  <div class="card">
    <img :src="link + item.poster_path" />
    <div class="text">
      <div><strong>Titolo: </strong>{{ item.title }}</div>
      <div><strong>Titolo originale: </strong>{{ item.original_title }}</div>
      <div><strong>Lingua: </strong>{{ item.original_language }}</div>
      <div><strong>Voto: </strong>{{ item.vote_average }}</div>
      <div><strong>Overview: </strong>{{ item.overview }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "filmList",
  props: {
    item: Object,
    link: String,
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
  text-align: left;
  border: 1px solid white;
}

.text {
  padding: 40px 20px;
}

img {
  width: 100%;
  height: 100%;
}
</style>