<template>
  <div>
    <Header />
    <h1>Hello User, welcome on Update Restaurant Page</h1>
    <form action="" class="add">
      <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name">
      <input type="text" name="address" placeholder="Enter address" v-model="restaurant.address">
      <input type="text" name="contact" placeholder="Enter contact" v-model="restaurant.contact">
      <button type="button" @click="updateRestaurant">Update new Restaurant</button>
    </form>
  </div>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios"

export default {
  name: "UpdateRestaurant",
  components: {
    Header,
  },
  data() {
    return {
      restaurant: {
        name: '',
        address: '',
        contact: '',
      }
    }
  },
  methods: {
    async updateRestaurant() {
      const id = this.$route.params.id
      
      const update = await axios.put(`http://localhost:3000/restaurant/${id}`, {
        name: this.restaurant.name,
        address: this.restaurant.address,
        contact: this.restaurant.contact
      })
      if(update.status === 200) {
        this.$router.push({name: 'Home'})
      }

    }
  },
  async mounted() {
    const user = localStorage.getItem("user-info");

    if (!user) {
      this.$router.push({ name: "SignUp" });
    }

    const id = this.$route.params.id
    const params = await axios.get(`http://localhost:3000/restaurant/${id}`)
    console.warn(params)
    this.restaurant = params.data
  },
};
</script>

<style></style>
