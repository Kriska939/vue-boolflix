<template>
  <div id="app">
    <header>
      <h1>Boolflix</h1>
      <SearchBar />
    </header>
    <main>
      <h2>Movies</h2>
      <div class="movieList">
        <Card />
      </div>
    </main>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import Card from "./components/Card.vue";
export default {
  name: "App",
  components: {
    SearchBar,
    Card,
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
