<template>
  <div>
    <div class="poster">
      <img :src="getPoster(item.poster_path)" alt="Poster" />
    </div>
    <div class="content">
      <h4>Titolo: {{ item.title || item.name }}</h4>
      <h4>Titolo originale: {{ item.original_title || item.original_name }}</h4>
      <p>
        Lingua:
        <span v-if="selectFlag(item.original_language)">
          <img
            class="img-resize"
            :src="selectFlag(item.original_language)"
            :alt="item.original_language"
        /></span>
        <span v-else>
          {{ item.original_language }}
        </span>
      </p>
      <p>Rating:{{ item.vote_average }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["item"],

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

    getPoster(address) {
      if (address) {
        return `https://image.tmdb.org/t/p/w342${address}`;
      } else {
        return `https://www.altavod.com/assets/images/poster-placeholder.png`;
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