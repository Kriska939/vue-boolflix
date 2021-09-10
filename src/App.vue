<template>
  <div id="app">
    <header>
      <h1>Boolflix</h1>
      <SearchBar />
    </header>
    <main></main>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
export default {
  name: "App",
  components: {
    SearchBar,
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
