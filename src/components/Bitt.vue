<template>
  <div>
    <div class="card" style="width: 100%">
      <div class="card-body">
        <h5 class="card-title">{{ bitt.username }}</h5>
        <h6 class="card-subtitle mb-2 text-muted">
          {{ testnaFun }}
        </h6>
        <p class="card-text">{{ bitt.text }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Bitt",
  props: ["bitt", "test"],
  computed: {
    testnaFun() {
      let miliseconds = Date.parse(this.bitt.created);
      console.log(miliseconds);
      let date = new Date(miliseconds);
      console.log(date.getFullYear());
      let month = date.getMonth() + 1;

      return date.getDay() + " / " + month + " / " + date.getFullYear();
    },
  },
};
</script>

<style>
</style>