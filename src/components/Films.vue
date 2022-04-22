<template>
  <div class="card">
    <img class="poster" :src="link + item.poster_path" />
    <div class="text">
      <div><strong>Titolo: </strong>{{ item.title }}</div>
      <div><strong>Titolo originale: </strong>{{ item.original_title }}</div>
      <div>
        <strong>Lingua: </strong>{{ item.original_language }}
        <img
          v-if="this.presentsFlags.includes(item.original_language)"
          :src="require(`@/assets/data/${item.original_language}.png`)"
          :alt="item.original_language + 'flag'"
          class="flag"
        />
        <img
          v-if="!this.presentsFlags.includes(item.original_language)"
          src="@/assets/data/unknown.png"
          alt="flag not present"
          class="flag"
        />
      </div>
      <Star :singleVote="item.vote_average" />
      <div>
        <strong>Overview: </strong>{{ item.overview }}
        <h3 v-show="item.overview.length === 0">
          Riassunto trama non disponibile
        </h3>
      </div>
    </div>
  </div>
</template>

<script>
import Star from "@/components/Star.vue";

export default {
  name: "filmList",
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
      presentsFlags: [
        "it",
        "en",
        "de",
        "es",
        "fr",
        "ru",
        "ja",
        "ko",
        "nl",
        "pl",
      ],
    };
  },
};
</script>

<style scoped lang="scss">
.card {
  width: calc(100% / 3) - 10%;
  height: 500px;
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
  opacity: 0%;
  transition: opacity 0.2s ease-in;
}

.poster {
  width: 100%;
  height: 100%;
  z-index: 0;
  transition: opacity 0.2s ease-in;
}

.card:hover .poster {
  opacity: 20%;
}

.card:hover .text {
  opacity: 100%;
}

.flag {
  width: 25px;
}
</style>