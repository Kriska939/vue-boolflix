<template>
  <div class="search-container">
    <div class="input-group">
      <div class="form-outline">
        <input
          type="text"
          id="form1"
          class="form-control"
          placeholder="Search.."
          v-model.trim="queryText"
        />
      </div>
      <button type="button" class="btn bg-red" @click="sendQuery">
        <i class="fas fa-search"></i>
      </button>
    </div>
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
.bg-red {
  background-color: #e50914;
}
</style>