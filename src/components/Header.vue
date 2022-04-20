<template>
  <header>
    <h2>BOOLFLIX</h2>
    <div>
      <input type="text" v-model="searchText" @keyup.enter="filterList" />
      <button @click="filterList">Cerca</button>
    </div>
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
  methods: {
    filterList() {
      this.$emit("insertedText", this.searchText);
    },
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