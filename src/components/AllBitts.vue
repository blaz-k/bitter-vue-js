<template>
  <div>
    <h2>Show all bitts</h2>
    <button @click="getAllBitts">Gett All Bitts</button>
    <div v-bind:key="bitt.id" v-for="bitt in bitts">
      <div class="all-bits">
        <div class="information">
          <div class="created">
            {{ bitts.username }}
          </div>
          <div class="username"></div>
        </div>
        <div class="bitt-text"></div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AllBitts",
  data() {
    return {
      bitts: [],
    };
  },
  methods: {
    async getAllBitts() {
      let response = await axios.get("http://localhost:5000/get-all-bitts");

      console.log(response.data);
      this.bitts = response.data;
    },
  },
};
</script>

<style scoped>
</style>