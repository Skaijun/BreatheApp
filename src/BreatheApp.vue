<template>
  <div id="app">
    <app-header @stateChanged="setUpApp($event)" :running="isStarted"></app-header>
    <app-breathe-circle :running="isStarted" :circleText="circleText"></app-breathe-circle>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import BreatheCircle from "./components/BreatheCircle.vue";
export default {
  name: "breathe-app",
  data() {
    return {
      isStarted: false,
      circleText: "",
      circleContainer: "",
      appInterval: "",
      totalBreatheTime: 7500
    };
  },
  methods: {
    setUpApp(isOn) {
      this.isStarted = isOn;
      this.circleContainer = document.querySelector(".container");
      this.circlePointer = document.querySelector(".pointer-container");
      this.breatheAnimation();

      if (this.isStarted) {
        this.appInterval = setInterval(
          this.breatheAnimation,
          this.totalBreatheTime
        );
      } else {
        console.log("STOOP!");
        clearInterval(this.appInterval);
        this.circleText = "";
        this.circleContainer.className = "container";
      }
    },
    breatheAnimation() {
      const timeBreatheIn = (this.totalBreatheTime / 5) * 2;
      const timeHold = this.totalBreatheTime / 5;

      this.circleText = "breatheIn";
      this.circleContainer.className = "container grow";
      this.circlePointer.className = "pointer-container animation-play";

      setTimeout(() => {
        this.circleText = "breatheHold";

        setTimeout(() => {
          this.circleText = "breatheOut";
          this.circleContainer.className = "container shrink";
        }, timeHold);
      }, timeBreatheIn);
    }
  },
  components: {
    appHeader: Header,
    appBreatheCircle: BreatheCircle
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  background-image: url("/images/background.jpeg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  height: 100vh;
  overflow: hidden;
  object-fit: cover;
}
</style>