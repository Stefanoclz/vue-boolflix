<template>
  <div class="star">
    <h4><strong>Voto: </strong>{{ starCalculator }}</h4>
    <i
      v-for="index in starCalculator"
      :key="index"
      class="fa-solid fa-star"
    ></i>
  </div>
</template>

<script>
export default {
  name: "starItem",
  props: {
    singleVote: Number,
  },
  computed: {
    starCalculator() {
      const stars = Math.round(this.singleVote / 2);
      return stars;
    },
  },
};
</script>

<style scoped lang='scss'>
.star {
  display: flex;
  column-gap: 10px;

  i {
    color: yellow;
  }
}
</style>