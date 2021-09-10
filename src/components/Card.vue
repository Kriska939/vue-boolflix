<template>
  <div>
    <h4>{{ movie.title }}</h4>
    <h4>{{ movie.original_title }}</h4>
    <p>{{ movie.original_language }}</p>
    <p>{{ movie.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["movie"],
};
</script>

<style scoped lang="scss">
</style>