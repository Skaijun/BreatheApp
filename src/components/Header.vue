<template>
  <div>
    <div class="header__top">
      <h2 class="header__top-title">Breathe Application</h2>
    </div>
    <button class="header__btn animate__fadeIn" @click="switchState" v-if="!running">Start breathing</button>
    <button class="header__btn animate__heartBeat" @click="reload" v-else>I'm already relaxed..</button>
  </div>
</template>

<script>
export default {
  props: ["running"],
  methods: {
    switchState() {
      const breatheState = !this.running;
      this.$emit("stateChanged", breatheState);
    },
    reload() {
        document.location.reload(true);
    }
  }
};
</script>

<style scoped>
.header__top {
  opacity: 0.8;
}
.header__top-title {
  font-size: 28px;
  line-height: 32px;
  color: cornflowerblue;
  border-bottom: 2px double white;
  text-align: center;
  padding-bottom: 15px;
}
.header__btn {
  cursor: pointer;
  width: 150px;
  height: 75px;
  font-size: 16px;
  line-height: 20px;
  background-color: cornflowerblue;
  opacity: 0.8;
  color: white;
  outline: none;
  border-radius: 10px;
  border: none;
  padding: 10px 5px;
  margin-left: 25px;
}
.header__btn:hover {
  opacity: 1;
}
</style>