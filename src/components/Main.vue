<template>
  <div class="card">
    <p>{{ item.title }}</p>
    <p>{{ item.original_title }}</p>
    <p>{{ item.vote_average }}</p>
    <p>{{ item.overview }}</p>
  </div>
</template>

<script>
export default {
  name: "mainComponent",
  props: {
    item: Object,
  },
};
</script>

<style scoped lang="scss">
.card {
  width: calc(100% / 3) - 5%;
  min-height: 200px;
  background-color: black;
  color: white;
  margin: 30px 0px;
  padding: 40px 20px;
  text-align: left;
  border: 1px solid white;
}
</style>