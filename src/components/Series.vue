<template>
  <div class="card">
    <img :src="link + item.poster_path" />
    <div class="text">
      <div><strong>Titolo: </strong>{{ item.name }}</div>
      <div><strong>Titolo originale: </strong>{{ item.original_name }}</div>
      <div>
        <strong>Lingua: </strong>{{ item.original_language }}
        <img
          :src="flagLink + item.original_language + '.png'"
          :alt="item.original_language + 'flag'"
          class="flag"
        />
      </div>
      <Star :singleVote="item.vote_average" />
      <div><strong>Overview: </strong>{{ item.overview }}</div>
    </div>
  </div>
</template>

<script>
import Star from "@/components/Star.vue";

export default {
  name: "seriesList",
  props: {
    item: Object,
    link: String,
    voto: Number,
  },
  components: {
    Star,
  },
  data() {
    return {
      flagLink: "src/assets/data/",
    };
  },
};
</script>

<style scoped lang="scss">
.card {
  width: calc(100% / 3) - 10%;
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

.flag {
  width: 25px;
}
</style>