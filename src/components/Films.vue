<template>
  <div class="card">
    <img :src="link + item.poster_path" />
    <div class="text">
      <div><strong>Titolo: </strong>{{ item.title }}</div>
      <div><strong>Titolo originale: </strong>{{ item.original_title }}</div>
      <div><strong>Lingua: </strong>{{ item.original_language }}</div>
      <h4><strong>Voto: </strong>{{ voto }}</h4>
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
    voto: Number,
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
  position: relative;
}

.text {
  padding: 40px 20px;
  z-index: 1000;
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  overflow-y: auto;
}

img {
  width: 100%;
  height: 100%;
  z-index: 0;
}
</style>