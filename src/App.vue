<template>
  <div id="app">
    <main>
      <AllBitts />
    </main>
  </div>
</template>

<script>
import AllBitts from "./components/AllBitts";

export default {
  name: "app",
  components: {
    AllBitts,
  },
};
</script>

<style>
* {
  background-color: rgb(233, 210, 210) ;
  
  margin: 0;
  padding: 0;

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50 ;
  margin-top: 60px;
}
</style>
