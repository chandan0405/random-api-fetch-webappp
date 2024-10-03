<template>
  <div>
    <div v-if="users.length === 0">No users to display</div>
    <ul v-else>
      <UserItem v-for="user in users" :key="user.login.uuid" :user="user" />
    </ul>
  </div>
</template>

<script>
import UserItem from "./UserItem.vue";

export default {
  components: {
    UserItem,
  },
  props: {
    users: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
ul {
  display:flex;
  flex-wrap:wrap;
  gap:20px;
  list-style-type: none;
  padding: 0;
}

li {
  padding: 10px;
  border: 1px solid #ccc;
  margin-bottom: 10px;
}
</style>
