<template>
  <div class="stopwatch">
    <div v-for="n of clocksList" v-bind:key="n" class="stopwatch__list">
      {{ n }}
      <Clock />
    </div>
    <AddClock v-on:addClockItem="addClockItem" />
  </div>
</template>

<script>
import Clock from ".//Clock.vue";
import AddClock from ".//AddClock.vue";
export default {
  name: "ClocksList",
  components: {
    Clock,
    AddClock,
  },

  data() {
    return {
      clocksList: [],
    };
  },

  methods: {
    addClockItem: function () {
      this.clocksList.push("");
      // this.clocksList.push(Clock);
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.stopwatch {
  display: flex;
  flex-wrap: wrap;
  margin: 72px 180px 35px;
}
.stopwatch__list {
  display: flex;
  justify-content: space-between;
}

@media (max-width: 1200px) {
  .stopwatch {
    margin: 72px 101px 27px;
  }
}
@media (max-width: 768px) {
  .stopwatch {
    margin: 72px 0 30px;
  }
  .stopwatch__list {
    margin: 0 auto;
  }
}
</style>
