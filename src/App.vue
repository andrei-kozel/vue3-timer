<template>
  <div id="app" class="h-screen bg-green-200 flex flex-col justify-center items-center h-full">
    <Timer v-if="isTimerSet" :propState="state" @setStatus="setStatus" />
    <InputTimer v-else @setState="setState" />
  </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import Timer from "./components/Timer.vue";
import InputTimer from "./components/InputTimer";
import "./assets/styles/index.css";
import { reactive, ref } from "vue";

export default {
  name: "App",
  components: {
    Timer,
    InputTimer
  },
  setup() {
    const state = reactive({
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0
    });
    let isTimerSet = ref(false);

    const setState = data => {
      state.days = data.state.days;
      state.hours = data.state.hours;
      state.minutes = data.state.minutes;
      state.seconds = data.state.seconds;
      isTimerSet.value = data.setTimerToTrue;
    };

    const setStatus = status => {
      isTimerSet.value = status;
    };

    return { state, isTimerSet, setState, setStatus };
  }
};
/* eslint-enable no-unused-vars */
</script>

<style lang="scss"></style>
