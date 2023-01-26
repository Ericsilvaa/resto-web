<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/add">Add Restaurant</router-link>
    <router-link to="/update">Update Restaurant</router-link>
    <a @click.prevent="logout" href="#">Logout</a>
  </nav>
</template>

<script>
export default {
  name: "HeaderHome",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style>
nav {
  padding: 0;
  display: flex;
  background-color: #333;
  box-shadow: 0px 0px 4px #555;
}

nav a {
  color: #f2f2f2f2;
  padding: 14px 16px;
  text-align: center;
  font-size: 17px;
  text-decoration: none;
  margin-right: 5px;
}

nav a:hover {
  background: #ddd;
  color: #333;
}
</style>
