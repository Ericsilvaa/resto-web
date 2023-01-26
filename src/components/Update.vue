<template>
  <div>
    <Header />
    <h1>Hello User, welcome on Update Restaurant Page</h1>
  </div>
</template>

<script>
import Header from "./Header.vue";

export default {
  name: "Update",
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
