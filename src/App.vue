<template>
  <div id="app">
    <!-- <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/sign-up">SignUp</router-link>
    </nav> -->
    <router-view />
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.logo {
  width: 85px;
}

.register input, .add input {
  width: 300px;
  height: 30px;
  padding-left: 10px;
  display: flex;
  margin: 20px auto;
  border: 1px solid skyblue;
}

.register button, .add button {
  width: 315px;
  height: 35px;
  border: 1px solid skyblue;
  cursor: pointer;
  background: skyblue;
  color: #fff;
}

.register button:hover {
  opacity: 0.8;
}
</style>
