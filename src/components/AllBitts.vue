<template>
  <div>
    <h2>Show all bitts</h2>
    <button @click="getAllBitts">Gett All Bitts</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AllBitts",
  methods: {
    async getAllBitts() {
      let response = await axios.get("http://localhost:5000/get-all-bitts");

      console.log(response.data);
    },
  },
};
</script>

<style scoped>
</style>