<template>
  <div>
    <Header />
    <h1>Hello {{ name }}, welcome on Home Page</h1>
    <table border="1">
      <tr>
        <td>Id</td>
        <td>Name</td>
        <td>Contact</td>
        <td>Adress</td>
        <td>Actions</td>
      </tr>
      <tr v-for="item in restaurant" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.contact }}</td>
        <td>{{ item.address }}</td>
        <td>
          <router-link :to="'/update/' + item.id">Update</router-link>
          <button @click="deleteRestaurant(item.id)">X</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import axios from "axios";

export default {
  name: "HomePage",
  components: {
    Header,
  },
  data() {
    return {
      name: null,
      restaurant: [],
    };
  },
  methods: {
    async deleteRestaurant(id) {
      const restaurant = await axios.delete(
        `http://localhost:3000/restaurant/${id}`
      );

      if (restaurant.status === 200) {
        this.loadData()
      }
    },
    async loadData() {
      const user = localStorage.getItem("user-info");
      this.name = JSON.parse(user).name;

      if (!user) {
        this.$router.push({ name: "SignUp" });
      }

      const restaurant = await axios.get("http://localhost:3000/restaurant");
      console.warn(restaurant);
      this.restaurant = restaurant.data;
    },
  },
  async mounted() {
    this.loadData();
  },
};
</script>

<style>
td {
  width: 160px;
  height: 40px;
}
</style>
