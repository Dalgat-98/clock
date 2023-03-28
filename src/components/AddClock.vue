<template>
  <button v-on:click="addClock" class="clock-add">
    <span>+</span>
  </button>
</template>

<script>
export default {
  name: "AddClock",

  data() {
    return {};
  },
  methods: {
    addClock: function () {
      this.$emit("addClockItem");
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.clock-add {
  margin: 0 25px 45px;
  width: 225px;
  height: 120px;
  background: #696969;
  border: none;
  cursor: pointer;
}
.clock-add span {
  font-size: 42px;
  color: #9e9e9e;
}
.clock-add:hover span {
  color: #ffffff;
}
</style>
