<template>
  <div>
    <Header />
    <h1>Hello User, welcome on Add Restaurant Page</h1>
    <form action="" class="add">
      <input type="text" name="name" placeholder="Enter Name" v-model="Restaurant.name">
      <input type="text" name="address" placeholder="Enter address" v-model="Restaurant.address">
      <input type="text" name="contact" placeholder="Enter contact" v-model="Restaurant.contact">
      <button type="button" @click="addRestaurant">Add new Restaurant</button>
    </form>
  </div>
</template>

<script>
import Header from "./Header.vue";

export default {
  name: "AddRestaurant",
  components: {
    Header,
  },
  data() {
    return {
      Restaurant: {
        name: '',
        address: '',
        contact: '',
      }
    }
  },
  methods: {
    addRestaurant() {
      console.warn(this.Restaurant)
    }
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
