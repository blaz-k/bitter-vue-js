<template>
  <div>
    <h2>Bitts forum</h2>
    <button @click="getAllBitts">Show All Bitts</button>
    <div v-bind:key="bitt.id" v-for="bitt in bitts">
      <div class="all-bits">
        <div class="information">
          <!--
          <div class="created">
            {{ bitt.created}}
          </div>-->
          <div class="username">
            {{ bitt.username }}
          </div>
        </div>
        <div class="text">
          {{ bitt.text }}
        </div>
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
.information {
  text-align: left;
  margin-top: 40px;
}

.information .username {
  padding: 5px 1px;
  font-size: 22px;
  font-weight: 700;
  color: rgb(189, 8, 8);
}

.text {
  display: inline-block;
  padding: 5px 15px;
  font-size: 18px;
  font-weight: 500;
  background-color: rgba(189, 165, 165, 0.733);
  border-radius: 13px;
  margin: 8px 0px;
}
button {
  display: flex;
  margin: auto;
  margin-top: 50px;
  border-radius: 13px;
  padding: 5px 15px;
  text-shadow: 0px 1px;
  font-size: 15px;
}

h2 {
  font-size: 40px;
  height: 20px;
  text-align: center;
}
</style>