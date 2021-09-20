<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Home</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Post new bitt</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
          </ul>
          <form class="d-flex">
            <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success" type="submit">Search</button>
          </form>
        </div>
      </div>
    </nav>
    <h2>Bitts</h2>
    <button class="showBittsButton" @click="getAllBitts">Show All Bitts</button>
    <div class="addNewBitt">
      <input
        id="usernameInput"
        v-model="usernameInput"
        type="text"
        placeholder="Username"
      />
      <input
        id="textInput"
        v-model="textInput"
        class="input-text"
        type="text"
        placeholder="Enter your text here"
      />
      <button @click="newBitt" class="newBittButton">Submit new bit</button>
    </div>

    <div v-bind:key="bitt.id" v-for="bitt in bitts">
      <div class="card" style="width: 100%;" >
        <div class="card-body">
          <h5 class="card-title" >{{ bitt.username }}</h5>
          <h6 class="card-subtitle mb-2 text-muted">{{ bitt.created }}</h6>
          <p class="card-text">{{ bitt.text }}</p>
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
      usernameInput: "",
      textInput: "",
    };
  },
  methods: {
    async getAllBitts() {
      let response = await axios.get("http://localhost:5000/get-all-bitts");

      console.log(response.data);
      this.bitts = response.data;
    },
    async newBitt() {
      let res = await axios.post("http://localhost:5000/create-bitt", {
        text: this.textInput,
        username: this.usernameInput,
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