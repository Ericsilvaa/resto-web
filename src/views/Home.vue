<template>
  <div>
    <Header />
    <h1>Hello {{ name }}, welcome on Home Page</h1>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import axios from 'axios'

export default {
  name: "HomePage",
  components: {
    Header,
  },
  data() {
    return {
      name: null,

    };
  },
  async mounted() {
    const user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;

    if (!user) {
      this.$router.push({ name: "SignUp" });
    }

    const restaurant = await axios.get("http://localhost:3000/restaurant")
    console.warn(restaurant)
  },
};
</script>

<style></style>
