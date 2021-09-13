<template>
  <div id="app">
    <header>
      <h1>Boolflix</h1>
      <SearchBar @dataQuery="getDataQuery" />
    </header>
    <main>
      <h2>Movies</h2>
      <div class="flex-container">
        <div class="movieList" v-for="item in searchedMovies" :key="item.id">
          <Card :item="item" />
        </div>
      </div>
      <h2>Series</h2>
      <div class="flex-container">
        <div class="seriesList" v-for="item in searchedSeries" :key="item.id">
          <Card :item="item" />
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import Card from "./components/Card.vue";
export default {
  name: "App",
  components: {
    SearchBar,
    Card,
  },
  data() {
    return {
      query: "",
      searchedMovies: [],
      searchedSeries: [],
    };
  },
  methods: {
    getDataQuery(data) {
      this.query = data;

      if (!this.query) this.searchedMovies = this.searchedSeries = [];

      this.getResults();
    },

    getResults() {
      const params = {
        params: {
          language: "it_IT",
          api_key: "bd55e90766b8791db24043f70a9dd910",
          query: this.query,
        },
      };
      axios
        .get("https://api.themoviedb.org/3/search/movie", params)
        .then((r) => {
          this.searchedMovies = r.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
header {
  display: flex;
  height: 80px;
}

h1 {
  margin: 0;
  line-height: 80px;
}

.flex-container {
  display: flex;
  flex-wrap: wrap;
}
</style>
