<template>
  <div id="app" class="h-screen">
    <InputTimer />
  </div>
</template>

<script>
// import Timer from "./components/Timer.vue";
import InputTimer from "./components/InputTimer";
import "./assets/styles/index.css";

export default {
  name: "App",
  components: {
    InputTimer
  }
};
</script>

<style lang="scss"></style>
