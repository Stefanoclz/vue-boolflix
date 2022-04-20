<template>
  <header>
    <h2>BOOLFLIX</h2>
    <input type="text" v-model="searchText" />
  </header>
</template>

<script>
export default {
  name: "headerComponent",
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  background-color: black;
  display: flex;
  justify-content: space-between;
  padding: 30px;

  h2 {
    color: red;
  }
}
</style>