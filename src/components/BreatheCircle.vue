<template>
  <div class="out">
    <div class="container">
      <div class="circle-gradient"></div>
      <div class="circle-solid"></div>
      <p v-if="circleText == 'breatheIn'" class="circle-text" key="in">Breathe in!</p>
      <p v-else-if="circleText == 'breatheHold'" class="circle-text" key="hold">Hold!</p>
      <p v-else-if="circleText == 'breatheOut'" class="circle-text" key="out">Breathe out!</p>
      <p v-else class="circle-text" key="source">^_^</p>
      <div class="pointer-container">
        <div class="pointer"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["running", "circleText"],
  data() {
    return {};
  },
  methods: {}
};
</script>

<style scoped>
.out {
  min-height: 100vh;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #fff;
  overflow: hidden;
}
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 300px;
  width: 300px;
  margin: auto;
  position: relative;
  transform: scale(1);
}
.container.grow {
  animation: grow 3s linear forwards;
}
.container.shrink {
  animation: shrink 3s linear forwards;
}
.circle-gradient {
  width: 320px;
  height: 320px;
  background: conic-gradient(
    #f35454 0%,
    #fd0101 20%,
    #910202 40%,
    rgb(255, 255, 255) 40%,
    rgb(53, 252, 235) 60%,
    #020d3f 60%,
    #061f8f 80%,
    #1612f7 100%
  );
  position: absolute;
  border-radius: 50%;
  z-index: -2;
}
.circle-solid {
  width: 100%;
  height: 100%;
  background-color: rgb(2, 3, 82);
  border-radius: 50%;
  z-index: -1;
  position: absolute;
  top: 0;
  left: 0;
}
.circle-text {
  font-size: 32px;
  line-height: 36px;
  font-weight: 400;
}
.pointer-container {
  position: absolute;
  top: -40px;
  left: 140px;
  width: 20px;
  height: 190px;
  /* animation: rotate 7.5s linear forwards infinite; */
  transform-origin: bottom center;
}
.pointer-container.animation-play {
  animation: rotate 7.5s linear forwards infinite;
}

.pointer {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #fff;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
@keyframes grow {
  from {
    transform: scale(1);
  }
  to {
    transform: scale(1.2);
  }
}
@keyframes shrink {
  from {
    transform: scale(1.2);
  }
  to {
    transform: scale(1);
  }
}
</style>