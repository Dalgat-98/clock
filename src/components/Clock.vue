<template>
  <div class="clock">
    <div class="clock__timer" :class="{ clock__timer_on: startStop }">
      <span class="clock__hours">{{ hours }}</span
      >:<span class="clock__min">{{ min }}</span
      >:<span class="sec">{{ sec }}</span>
    </div>
    <div class="clock__br" :class="{ clock__br_on: startStop }"></div>
    <div class="clock__control">
      <button
        v-on:click="clockStart"
        class="clock__start"
        :class="{ clock__start_on: startStop }"
      ></button>
      <button
        v-on:click="clockStop"
        class="clock__stop"
        :class="{ clock__stop_on: startStop }"
      ></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Clock",

  data() {
    return {
      t: 0,
      startStop: false,
      hours: "00",
      min: "00",
      sec: "00",
    };
  },

  methods: {
    tick: function () {
      this.sec++;
      if (this.sec <= 9) {
        this.sec = "0" + this.sec;
      }
      if (this.sec >= 60) {
        this.sec = "00";
        this.min++;
        if (this.min <= 9) {
          this.min = "0" + this.min;
        }
        if (this.min >= 60) {
          this.min = "00";
          this.hours++;
          if (this.hours <= 9) {
            this.hours = "0" + this.hours;
          }
        }
      }
    },

    clockStart: function () {
      if (!this.startStop) {
        this.t = setInterval(this.tick, 1000);
        this.startStop = true;
      } else {
        clearTimeout(this.t);
        this.startStop = false;
      }
    },

    clockStop: function () {
      clearTimeout(this.t);
      this.startStop = false;
      this.sec = "00";
      this.min = "00";
      this.hours = "00";
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.clock {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 0 25px 45px;
  width: 225px;
  height: 120px;
  background: #696969;
}
.clock__timer {
  margin: 22px auto 0;
  width: 95px;
  height: 18px;
  font-family: "Gotham Pro";
  font-style: normal;
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  text-align: center;
  color: #9e9e9e;
}
.clock__timer_on span {
  color: #ffffff;
}
.clock__br {
  width: 225px;
  height: 0px;
  border: 1px solid #9e9e9e;
}
.clock__br_on {
  border: 1px solid #ffffff;
}
.clock__control {
  display: flex;
  justify-content: space-around;
  margin: 0 67px 22px;
}
.clock__start {
  width: 17px;
  height: 20px;
  background: #696969;
  border: 10px solid transparent;
  border-left: 17px solid #9e9e9e;
  cursor: pointer;
}
.clock__start:hover {
  border: 10px solid transparent;
  border-left: 17px solid #ffffff;
}
.clock__start_on {
  border: 10px solid transparent;
  border-left: 17px solid #ffffff;
}
.clock__stop {
  width: 20px;
  height: 20px;
  background: #9e9e9e;
  border: none;
  cursor: pointer;
}
.clock__stop_on {
  background: #ffffff;
}
</style>
