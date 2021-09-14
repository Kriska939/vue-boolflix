<template>
  <div class="mb-3" id="card">
    <img
      :src="getPoster(item.poster_path)"
      alt="Poster"
      class="img-fluid poster"
    />
    <div id="content" class="text-center pt-5">
      <p class="mb-0">Titolo:</p>
      <h5 class="d-inline">{{ item.title || item.name }}</h5>
      <p class="mb-0">Titolo Originale:</p>
      <h5 class="d-inline">{{ item.original_title || item.original_name }}</h5>
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
      <p class="mb-0">Rating: {{ rating + "/5" }}</p>
      <span>
        <i
          v-for="n in 5"
          :key="n"
          :class="n <= rating ? 'fas' : 'far'"
          class="fa-star"
        ></i>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["item"],

  computed: {
    rating() {
      return Math.ceil(this.item.vote_average / 2);
    },
  },

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
.img-resize {
  width: 45px;
  height: 25px;
}

#card {
  height: 350px;
  padding-bottom: 30px;
}

#card .poster {
  height: 350px;
}

#content {
  visibility: hidden;
  height: 0;
}

#card:hover {
  #content {
    visibility: visible;
    height: 100%;
    color: white;
  }

  .poster {
    display: none;
  }
}
</style>