<template>
  <div>
    <Header />
    <h1>Hello User, welcome on Add Restaurant Page</h1>
  </div>
</template>

<script>
import Header from "./Header.vue";

export default {
  name: "Add",
  components: {
    Header,
  },
  mounted() {
    const user = localStorage.getItem("user-info");

    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>

<style></style>
