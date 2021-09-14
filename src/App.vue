<template>
  <div id="app">
    <header class="d-flex justify-content-between align-items-center bg-black">
      <h1 class="c-red ms-3">Boolflix</h1>
      <SearchBar @dataQuery="getDataQuery" class="me-3" />
    </header>
    <main class="bg-grey">
      <section class="container">
        <h2 class="c-red">Movies</h2>
        <div class="row d-flex">
          <div
            class="col col-lg-3 col-md-4 col-sm-6 mb-5 movieList"
            v-for="item in searchedMovies"
            :key="item.id"
          >
            <Card :item="item" />
          </div>
        </div>
      </section>
      <section class="container">
        <h2 class="c-red">Series</h2>
        <div class="row d-flex">
          <div
            class="col col col-lg-3 col-md-4 col-sm-6 mb-5 seriesList"
            v-for="item in searchedSeries"
            :key="item.id"
          >
            <Card :item="item" />
          </div>
        </div>
      </section>
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
    getDataQuery(query) {
      this.query = query;

      if (!query) this.searchedMovies = this.searchedSeries = [];

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

      axios.get("https://api.themoviedb.org/3/search/tv", params).then((r) => {
        this.searchedSeries = r.data.results;
      });
    },
  },
};
</script>

<style lang="scss">
.bg-black {
  background-color: black;
}

.bg-grey {
  background-color: #3c3c3c;
}

.c-red {
  color: #e50914;
}
h1 {
  margin: 0;
  line-height: 80px;
}

h2 {
  padding: 40px 0;
}
</style>
