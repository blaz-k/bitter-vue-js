<template>
  <div>
    <h2>Bitts</h2>
    <button class="showBittsButton" @click="getAllBitts">Show All Bitts</button>
    <div class="addNewBitt">
      <input id="usernameInput" type="text" placeholder="Username" />
      <input
        id="textInput"
        class="input-text"
        type="text"
        placeholder="Enter your text here"
      />
      <button @click="newBitt" class="newBittButton">Submit new bit</button>
    </div>

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
    async newBitt() {
      let usernameInput = document.getElementById("usernameInput").value;
      let textInput = document.getElementById("textInput").value;
      console.log(textInput);
      console.log(usernameInput);
      let res = await axios.post("http://localhost:5000/create-bitt", {
        text: textInput,
        username: usernameInput,
      });
      let data = res.data;
      console.log(data);
    },
  },
};
</script>

<style scoped>
.addNewBitt {
  margin-top: 50px;
}
.information {
  text-align: left;
  margin-top: 40px;
}

.information .username {
  padding: 5px 1px;
  font-size: 22px;
  font-weight: 700;
  color: rgb(189, 8, 8);
  margin-left: 10px;
}

.text {
  display: inline-block;
  padding: 5px 15px;
  font-size: 18px;
  font-weight: 500;
  background-color: rgba(189, 165, 165, 0.733);
  border-radius: 13px;
  margin: 8px 0px;
  margin-left: 10px;
}
.showBittsButton {
  display: flex;
  margin: auto;
  margin-top: 20px;
  border-radius: 13px;
  padding: 5px 15px;
  text-shadow: 0px 1px;
  font-size: 15px;
}

h2 {
  font-size: 100px;
  font-weight: 900;
  text-align: center;
}

#usernameInput {
  padding: 10px;
  font-size: 20px;
  border-radius: 0px 10px 0px 10px;
  box-shadow: 0px 0px 26px;
  border-color: rgb(255, 0, 0);
  margin: 10px;
}
#textInput {
  padding: 10px;
  font-size: 20px;
  border-radius: 0px 10px 0px 10px;
  box-shadow: 0px 0px 26px;
  border-color: rgba(189, 165, 165, 0.733);
  margin: 10px;
}
.newBittButton {
  margin: 10px;
  border-radius: 10px;
  padding: 11px;
  text-shadow: 0px 1px;
  font-size: 20px;
  border-color: rgb(10, 10, 10);
}
.addNewBitt {
  margin: 10px;
  padding-top: 50px;
}
</style>