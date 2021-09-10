<template>
  <div class="search-container">
    <input
      type="text"
      placeholder="Search.."
      name="search"
      v-model.trim="queryText"
    />
    <button @click="sendQuery">Search</button>
  </div>
</template>

<script>
export default {
  name: "searchBar",
  data() {
    return {
      queryText: "",
    };
  },
  methods: {
    sendQuery() {
      this.$emit("dataQuery", this.queryText);
    },
  },
};
</script>

<style scoped lang="scss">
.search-container {
  line-height: 80px;
  margin-left: 10px;
}
</style>