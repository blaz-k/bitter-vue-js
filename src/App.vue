<template>
  <div id="app">
    <main>
      <AllBitts />
      
    </main>
  </div>
</template>

<script>
/*
import axios from "axios";*/
import AllBitts from "./components/AllBitts";

export default {
  name: "app",
  components: {
    AllBitts,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
