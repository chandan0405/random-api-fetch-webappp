<template>
  <li>
    <div>
      <img :src="user.picture.thumbnail" alt="User picture" />
      <p>{{ user.name.first }} {{ user.name.last }}</p>
      <p>Email: {{ user.email }}</p>
      <p>Location: {{ user.location.city }}, {{ user.location.country }}</p>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  flex-wrap:wrap;
  align-items: center;
}

img {
  border-radius: 50%;
  margin-right: 10px;
}
</style>
