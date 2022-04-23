<template>
  <div>
    <h4>Cast:</h4>
    <p v-for="(actor, index) in actor" :key="actor.id" v-show="index < 5">
      {{ actor.name }}
    </p>
  </div>
</template>

<script>
export default {
  name: "castItem",
  props: {
    actor: Array,
  },
};
</script>

<style scoped lang="scss">
</style>