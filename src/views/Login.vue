<template>
  <div>
    <h1>Login</h1>
    <div class="register">
      <input type="text" placeholder="Enter email" v-model="email" />
      <input type="password" placeholder="Enter password" v-model="password" />
      <button @click.prevent="login">Login</button>

      <p>
        <router-link to="/sign-up">Sign Up</router-link>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "LoginPage",
  data() {
    return {
      email: null,
      password: null,
    };
  },
  methods: {
    async login() {
      const baseUrl = "http://localhost:3000";

      const authLogin = await axios.get(
        `${baseUrl}/users?email=${this.email}&password=${this.password}`
      );

      if (authLogin.status === 200 && authLogin.data.length > 0) {
        localStorage.setItem("user-info", JSON.stringify(authLogin.data[0]));
        this.$router.push({ name: "Home" });
      }
    },
  },
};
</script>

<style></style>
