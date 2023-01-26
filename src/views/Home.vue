<template>
  <div>
    <Header />
    <h1>Hello {{ name }}, welcome on Home Page</h1>
  </div>
</template>

<script>
import Header from "../components/Header.vue";

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
  mounted() {
    const user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;

    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>

<style></style>
