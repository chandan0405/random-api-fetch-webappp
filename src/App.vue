<template>
  <div id="app">
    <h1>Random User Search</h1>
    <button @click="fetchUsers()">Fetch Users</button>
    
    <!-- SearchBar Component -->
    <SearchBar @search="handleSearch" />

    <!-- UserList Component -->
    <UserList :users="filteredUsers" />
  </div>
</template>

<script>
import axios from "axios";
import UserList from "./components/UserList.vue";
import SearchBar from "./components/SearchBar.vue"; // Ensure correct path

export default {
  data() {
    return {
      users: [], // Full list of users fetched from API
      searchQuery: "", // Search query from SearchBar
    };
  },
  computed: {
    filteredUsers() {
      // Filter users based on the search query
      const filtered = this.users.filter((user) =>
        `${user.name.first} ${user.name.last}`
          .toLowerCase()
          .includes(this.searchQuery.toLowerCase())
      );
      return filtered;
    },
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await axios.get("https://randomuser.me/api/?results=20");
        this.users = response.data.results; // Set the fetched users to the `users` array
      } catch (error) {
        console.error("Failed to fetch users!", error);
      }
    },
    handleSearch(query) {
      this.searchQuery = query; // Update the search query when the SearchBar emits it
    },
  },
  mounted() {
    this.fetchUsers(); // Fetch users when the component is mounted
  },
  components: {
    UserList,
    SearchBar,
  },
};
</script>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
  margin-block: auto;
}
button{
      height: 2rem;
    width: 8rem;
    border-radius: 8px;
    margin-bottom: 10px;
    cursor:pointer;
}
h1 {
  font-size: 2.5em;
  margin-bottom: 20px;
}

@media (min-width: 1024px) {
    #app {
        display: block;
        margin-block-end: auto;
        margin-top: 20px;
    }
}

@media (max-width: 312px) {
    input{
      width:100px;
    }
}
</style>
