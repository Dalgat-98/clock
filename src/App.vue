<template>
  <div class="container">
    <ClocksList />
    <!-- <Clock />
    <AddClock /> -->
  </div>
</template>

<script>
// import Clock from "./components/Clock.vue";
import ClocksList from "./components/ClocksList.vue";
// import AddClock from "./components/AddClock.vue";

export default {
  name: "App",
  components: {
    // Clock,
    ClocksList,
    // AddClock,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
.container {
  display: flex;
  margin: 0 auto;
  max-width: 1200px;
  background: #353638;
}

@media (max-width: 1200px) {
  .container {
    max-width: 768px;
  }
}
@media (max-width: 768px) {
  .container {
    max-width: 320px;
  }
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
