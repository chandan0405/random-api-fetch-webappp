<template>
  <div>
    <input
      type="text"
      v-model="searchQuery"
      placeholder="Search users by name"
      @input="onSearch"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
    };
  },
  methods: {
    onSearch() {
      this.$emit("search", this.searchQuery); // Emit search event to parent
    },
  },
};
</script>

<style scoped>
input {
  padding: 8px;
  margin-bottom: 20px;
  width: 100%;
}
@media (min-width: 1024px) {
  input{
    width:100%;
  }
}
@media (max-width: 312px) {
    input{
      width:160px;
    }
}

</style>
