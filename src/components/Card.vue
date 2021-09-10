<template>
  <div>
    <h4>Titolo: {{ movie.title }}</h4>
    <h4>Titolo originale: {{ movie.original_title }}</h4>
    <p>Lingua:{{ movie.original_language }}</p>
    <p>Rating:{{ movie.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["movie"],
};
</script>

<style scoped lang="scss">
div {
  background-color: lightblue;
  margin: 0 20px;
}
</style>