<template>
  <div>
    <h4>Titolo: {{ movie.title }}</h4>
    <h4>Titolo originale: {{ movie.original_title }}</h4>
    <p>
      Lingua:
      <span v-if="selectFlag(movie.original_language)">
        <img
          class="img-resize"
          :src="selectFlag(movie.original_language)"
          :alt="movie.original_language"
      /></span>
      <span v-else>
        {{ movie.original_language }}
      </span>
    </p>
    <p>Rating:{{ movie.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["movie"],

  methods: {
    selectFlag(lang) {
      if (lang === "en") {
        return require("../assets/images/en.png");
      } else if (lang === "it") {
        return require("../assets/images/it.png");
      } else {
        return;
      }
    },
  },
};
</script>

<style scoped lang="scss">
div {
  background-color: lightblue;
  margin: 0 20px;
}

.img-resize {
  max-width: 50px;
  max-height: 40px;
}
</style>