<template>
  <div id="app">
    <header>
      <h1>Boolflix</h1>
      <SearchBar @dataQuery="getDataQuery" />
    </header>
    <main>
      <h2>Movies</h2>
      <div class="movieList" v-for="movie in searchedMovies" :key="movie.id">
        <Card :movie="searchedMovies" />
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
    };
  },
  methods: {
    getDataQuery(data) {
      this.query = data;
      this.getMovies();
    },

    getMovies() {
      axios.get(
        `https://api.themoviedb.org/3/search/movie?api_key=bd55e90766b8791db24043f70a9dd910&language=it_IT&query=${this.query}`.then(
          (r) => {
            this.searchedMovies = r.data.results;
          }
        )
      );
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
</style>
