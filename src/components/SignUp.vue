<template>
  <div>
    <img class="logo" src="../assets/restaurant-logo.png" />
    <h1>Sign Up</h1>

    <form action="">
      <div class="register">
        <input type="text" placeholder="Enter name" v-model="name" />
        <input type="text" placeholder="Enter email" v-model="email" />
        <input
          type="password"
          placeholder="Enter password"
          v-model="password"
        />
        <button @click.prevent="singUp">Sign Up</button>

        <p>
          <router-link to="/login">Login</router-link>
        </p>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SignUp",
  data() {
    return {
      name: null,
      email: null,
      password: null,
    };
  },
  methods: {
    async singUp() {
      const baseUrl = "http://localhost:3000";

      const user = await axios.post(`${baseUrl}/users`, {
        email: this.email,
        password: this.password,
        name: this.name,
      });

      if (user.status === 201) {
        localStorage.setItem("user-info", JSON.stringify(user.data));
        this.$router.push({ name: "Home" });
      }
    },
  },
  mounted() {
    const user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style>

</style>
